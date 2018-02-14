## Compile and install argon2 library on a linux os based 

```bash
git clone https://www.github.com/P-H-C/phc-winner-argon2.git argon2-src;
cd argon2-src && sudo make && sudo make install;
```

### Distribution dependent

If you use one of the distributions listed below, you can use your package manager to install the library. You are not required to download and compile it yourself.

#### ArchLinux

`$ pacman -S argon2`

#### Debian based (Debian, Ubuntu, ...)

`$ apt install libargon2-0-dev`

#### NixOs

`$ nix-env -iA nixos.libargon2`

#### OpenSUSE## 

`$ zypper install argon2-devel`

## Compile and install argon2 library on Windows: 

**IN THEORY : Install [MINGW for Windows](https://sourceforge.net/projects/mingw/files/Installer/) and [Git Bash for Windows](https://git-for-windows.github.io/), open a git bash _as Administrator_ somewhere, and do as follows:**

```
git clone https://www.github.com/P-H-C/phc-winner-argon2.git argon2-src ;
cd argon2-src && make && make install;
```

We wrote IN THEORY because the Makefile says to do with MINGW but we cannot test the compilation correctly

## Modify your authme config.yml: 
```yaml
    security:
        passwordHash: 'ARGON2'
```