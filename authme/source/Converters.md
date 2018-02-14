To switch from another auth plugin to AuthMe, you can preserve your data by using one of our converters. Converters are run as a command, `/authme converter <name>`, and the converters are configured in the "Converter" section of config.yml.

- [AuthMe](#authme): from one database type to another
- [CrazyLogin](#crazylogin)
- [LoginSecurity](#loginsecurity)
- [Rakamak](#rakamak)
- [RoyalAuth](#royalauth)
- [vAuth](#vauth)
- [xAuth](#xauth)

## AuthMe
It is possible to convert your data from one AuthMe database type to another.

#### SQLite to MySQL
Command: `/authme converter sqliteToSql`  
Set your config.yml to use the MySQL database you want to convert to. The SQLite database must be in `plugins/AuthMe` and have the same name as the configured database name ("DataSource.mySQLDatabase" in config.yml).

#### MySQL to SQLite
Command: `/authme converter mysqlToSqlite`  
Set your config.yml to use the SQLite database you want to convert to. The MySQL settings in config.yml are used to connect to the MySQL database.

## CrazyLogin
Command: `/authme converter crazylogin`  
Flat file support only. Copy the flat file DB in the plugins/AuthMe folder and configure `Converter.CrazyLogin.fileName` in config.yml to the name of your file.

## LoginSecurity
Command: `/authme converter loginsecurity`  
Supports both flat file and MySQL – as configured in config.yml (see "Converter.loginSecurity"). In case of flat file, the flat file DB must be at its regular location, namely at `plugins/LoginSecurity/LoginSecurity.db`.

## Rakamak
🕸 Dead for years, probably not used by anyone anymore?  
Command: `/authme converter rakamak`  
Supports flat file only, see "Converter.rakamak" in config.yml.

## RoyalAuth
Command: `/authme converter royalauth`  
Only migrates name, password and lastlogin.

## vAuth
🕸 Dead for years, probably not used by anyone anymore?  
Command: `/authme converter vauth`

## xAuth
Command: `/authme converter xauth`  
This converter requires that the xAuth plugin be loaded in order to work! It migrates whatever database xAuth is configured to use.