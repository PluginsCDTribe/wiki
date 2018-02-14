## 原理
单元测试用于测试一个单元：一个特定的类、方法被测试，来保证其中的逻辑合乎我们的预期。相反，集成测试保证两个以上的部件交互正常。

单元测试不需要保证运行的顺序 - 既不是一个类中的方法的顺序、也不是测试类中的顺序。单元测试不应该依赖于先前的测试建立。这是因为测试全部通过但运行时出错经常就是这个原因。

不必多说，在 test/ 文件夹下的任何东西不应该在外部使用。测试是分离的一部分，构建软件时不应该有任何测试的资源被包含。

## 技术

我们使用 JUnit, Hamcrest 和 Mockito 来进行单元测试。**JUnit** 是用于测试框架运行的基础；**Hamcrest** 提供了有力的匹配器来测试测试结果；**Mockito** 让我们可以模拟一个类，比如使用相同的类接口但是提供了特殊的功能来模拟某个特殊的情况。这让单元测试变得更方便：我们只想测试某一个部分，剩下的就模拟（mock）。

## 惯例

测试某个特定类的类应该使用对应类的名称，然后追加「Test」，比如测试 `Player` 类，创建一个 `PlayerTest` 的测试类。测试类的 JavaDoc 不是必需的，因为它们（应该）不言而喻。开始测试的方法应该使用 `should` 加上期望的动作，比如 `shouldKickPlayer()` 是期望的最终结果。

就算我们没有使用由行为驱动的开发方式，这些测试的经典类型仍然适用。每个测试分为三个部分，分别称为 `given`, `when` 和 `then`:

- `given` 实例化并定义类中的必要的值和对象来运行测试（比如产生测试需要的条件）。
- `when` 是测试的命令。经常每个测试类一行。
- `then` 检验测试的结果。

以下的实例形象的展示了这是如何工作的。

## 静态的注入和方法

Mockito 不能模拟所有的类和方法 - 类和方法不能是 `final` 的，方法也不能是 `static` 的。

静态的方法适用于轻量的工具类（没有状态，没有重量级操作如执行I/O）以及 logger。

## 示例

注意以下的测试仅仅为模拟的，不对应任何 AuthMe 中的类。给出以下方法：
```java
public static boolean isLoggedIn(CommandSender sender) {
  if (sender == null || !(sender instanceof Player)) {
    return false;
  }
  return Status.LOGGED_IN.equals(((Player) sender).getStatus());
}
```
你可能想要测试这个方法在 sender 不是 `Player` 类的实例时返回 `false` ，比如这个实例为 `Console` 。
```java
@Test
public void shouldReturnFalseForNonPlayerSender() {
  // given
  CommandSender sender = Mockito.mock(Console.class);

  // when
  boolean result = Verifier.isLoggedIn(sender);

  // then
  assertThat(result, equalTo(false));
}
```

现在我们想要测试玩家登录时是否会返回正确的 `Status` 。这个示例展示了 Mockito 的力量：我们不需要实例化一个实际的玩家，尤其还是这样做时我们可能会遇到返回我们想要的 Status 的问题（比如没有提供 setter）。

```java
@Test
public void shouldReturnTrueForLoggedInPlayer() {
  // given
  Player player = Mockito.mock(Player.class);
  given(player.getStatus()).willReturn(Status.LOGGED_IN);

  // when
  boolean result = Verifier.isLoggedIn(sender);

  // then
  assertThat(result, equalTo(true));
}
```
