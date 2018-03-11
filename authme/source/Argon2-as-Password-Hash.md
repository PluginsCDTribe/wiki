## 在linux操作系统基础上编译和安装 argon2 

```bash
git clone https://www.github.com/P-H-C/phc-winner-argon2.git argon2-src;
cd argon2-src && sudo make && sudo make install;
```

### 分发版本

如果您使用下面列出的发行版之一，则可以使用软件管理器来安装该库。你不需要自行下载和编译它。

#### ArchLinux

`$ pacman -S argon2`

#### Debian based (Debian, Ubuntu, ...)

`$ apt install libargon2-0-dev`

#### NixOs

`$ nix-env -iA nixos.libargon2`

#### OpenSUSE## 

`$ zypper install argon2-devel`

## 在Windows上编译和安装 argon2 库: 

**按理来讲 : 安装 [MINGW for Windows](https://sourceforge.net/projects/mingw/files/Installer/) 以及 [Git Bash for Windows](https://git-for-windows.github.io/), 以 _管理员身份_ 打开 git bash 并执行以下操作:**

```
git clone https://www.github.com/P-H-C/phc-winner-argon2.git argon2-src ;
cd argon2-src && make && make install;
```

我们写的是 按理来讲 ，因为 Makefile 与 MINGW 有关，所以我们不能正确的测试编译

## 修改你的 authme config.yml: 
```yaml
    security:
        passwordHash: 'ARGON2'
```