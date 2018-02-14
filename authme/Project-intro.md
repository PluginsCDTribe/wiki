### Issues
- The issue tracker is used for managing bugs but also new features
- Split issues if one becomes too complex
  * One "work item" per issue guarantees a better overview
  * If something is partially done in a milestone, open a follow-up issue so we can keep the milestone on the issue to reflect the truth
- After implementation the issue is not closed but it is labeled as **please verify**, giving the reporter/someone else the chance to test

### Technical layout
- Three important groups of classes are: [listeners](https://github.com/AuthMe/AuthMeReloaded/tree/master/src/main/java/fr/xephi/authme/listener), [ExecutableCommand](https://github.com/AuthMe/AuthMeReloaded/blob/master/src/main/java/fr/xephi/authme/command/ExecutableCommand.java) and [services](https://github.com/AuthMe/AuthMeReloaded/tree/master/src/main/java/fr/xephi/authme/service)
   * State is kept in services (not in commands or listener)
   * Commands / listeners are the entry point for actions to be performed -> they typically forward work to the services after some input checks
   * Arguments passed to ExecutableCommand always have the correct count! See [Command Handling](Command-Handling)
- [BukkitService](https://github.com/AuthMe/AuthMeReloaded/blob/master/src/main/java/fr/xephi/authme/service/BukkitService.java) wraps calls to the Bukkit API so we can easily update / swap calls or implement different behavior centrally
- We use [dependency injection](Dependency-Injection)
   * Injector acts a "singleton manager" and is responsible for setting members with the `@Inject` annotation

### Project setup
- See [Development Setup](Development-Setup). In particular, note:
   * Enable Maven `skipLongHashTests` profile locally
   * You can enable Checkstyle checks in IntelliJ to be in sync with [Code Climate](https://codeclimate.com/github/AuthMe/AuthMeReloaded/issues)
   * How to have a runnable MC server with your local code

### Settings
- We use [ConfigMe](https://github.com/AuthMe/ConfigMe).
   * Each property from config.yml lives in the code as a `Property`. See [fr.xephi.authme.settings.properties](https://github.com/AuthMe/AuthMeReloaded/tree/master/src/main/java/fr/xephi/authme/settings/properties)
   * A property's value can _never_ be null
   * Migration of settings with [SettingsMigrationService](https://github.com/AuthMe/AuthMeReloaded/blob/master/src/main/java/fr/xephi/authme/settings/SettingsMigrationService.java)
   * Adding new settings is handled by ConfigMe - no migration necessarily

### Unit tests
- New features / bug fixes should be accompanied by unit tests. See [unit testing](Unit-Testing).

### Bonus
- [Tool tasks](Tool-tasks) let us automatically update [our docs](https://github.com/AuthMe/AuthMeReloaded/tree/master/docs) and our plugin.yml
- We have [expiring structures](https://github.com/AuthMe/AuthMeReloaded/tree/master/src/main/java/fr/xephi/authme/util/expiring) (collections which let entries "expire" after a configured timeout)
- Permission nodes are handled as enums extending [PermissionNode](https://github.com/AuthMe/AuthMeReloaded/blob/master/src/main/java/fr/xephi/authme/permission/PermissionNode.java) (e.g. [PlayerPermission](https://github.com/AuthMe/AuthMeReloaded/blob/master/src/main/java/fr/xephi/authme/permission/PlayerPermission.java))