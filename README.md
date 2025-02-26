srb2bld is a shell script, that automates and simplifies process of downloading source code, configuring, compilation, installation to system or creating portable executable bundles of various SRB2 related builds.

https://user-images.githubusercontent.com/16626326/162315944-86dc5997-cfc4-463a-96ca-b5630b85e022.mp4

# Features
- Compiling and installing 32-bit/64-bit binaries of SRB2, SRB2 Uncapped Plus, SRB2 NetPlus, SRB2 rphys, SRB2 VR, SRB2 v2.1 Legacy, SRB2 v2.0, SRB2 Final Demo, SRB2 Persona, SRB2 Kart or SRB2 Kart Moe Mansion, SRB2 Kart VR, wadcli and SLADE on Linux, macOS (tested on version 10.14/Mojave, 10.15/Catalina and 11/Big Sur) and Windows. Check "Compatibility" section or enter the script's -c/--compatibility option for information about which build compiles and run for each system and CPU architecture,
- Compiling and installing custom SRB2 builds from local or remote Git repository,
- Ability to set user's flags before compiling,
- Installing missing dependencies on host system (mostly binaries, except for SRB2 builds on macOS) based on user's set compilation flags,
- Supports installing SRB2 builds and its dependencies for glibc based Linux distros like: Debian, Ubuntu, Arch, Manjaro, Gentoo, OpenSUSE, Fedora, Void and musl based like: Void, Alpine,
- Systems with immutable root filesystems (Steam Deck's SteamOS, Fedora Silverblue/Kinoite) are supported too,
- Compiling builds on ARM CPU too (tested on ODROID XU4 with Ubuntu Linux 18.04),
- Creating customizable AppImages (Linux only) and App Bundles (macOS only) for x86/x64 and ARM CPUs,
- Removing installed SRB2 builds, source code and assets,
- Upgrading installed SRB2 builds,
- Runs on Linux, macOS and Windows (Git Bash).

# Dependencies
- Basic system utilities like GNU Coreutils, BusyBox or macOS out-of-the-box system utilities,
- Bash or any POSIX compliant shell,
- Findutils,
- Which,
- Curl,
- Gawk,
- Ncurses,
- Docker (Linux and Windows only),
- GNU Stow (Linux and macOS only),
- FUSE (Linux only),
- Patchelf (Linux only),
- Optionally for updating icons and menu entries: gtk-update-icon-cache or kservice (can be part of GNOME or KDE desktop environment package) (Linux only).

Windows users need to also have installed Git Bash to run this script.

As for macOS users, they need to install these additional dependencies:
- Cmake,
- Autoconf,
- Automake,
- Pkg-config,
- Libtool,
- P7zip,
- Unrar/Rar,
- Makeicns.

# Dependencies Installation
**Linux:**
1. In terminal enter this following command:
- Debian/Ubuntu/Debian based/Ubuntu based: `sudo apt install make git debianutils coreutils findutils ncurses-bin curl gawk docker.io stow fuse patchelf`,

- Arch/Arch based: `sudo pacman -S --needed make git which coreutils findutils ncurses curl gawk docker stow fuse patchelf`,

- Gentoo/Gentoo based: `sudo emerge -av git which coreutils findutils ncurses curl gawk docker stow fuse patchelf`,

- Fedora/Fedora based: `sudo dnf install make git which coreutils findutils ncurses curl gawk docker stow fuse patchelf`,

- Fedora Silverblue/Kinoite: `rpm-ostree install -A --allow-inactive make git which coreutils findutils ncurses curl gawk docker stow fuse patchelf`,

- OpenSUSE/OpenSUSE based: `sudo zypper in make git which coreutils findutils ncurses curl gawk docker stow fuse patchelf`,

- Void/Void based: `sudo xbps-install -S make git which coreutils findutils ncurses curl gawk docker stow fuse patchelf`,

- Alpine/Alpine based: `sudo apk add make git which coreutils findutils ncurses curl gawk docker stow fuse patchelf`,

- Solus/Solus based: `sudo eopkg it make git which coreutils findutils ncurses curl gawk docker stow fuse patchelf`,

- NixOS/NixOS based: `sudo nix-env -i gnumake git which coreutils findutils ncurses curl gawk stow fuse patchelf` or `sudo nix profile install nixpkgs#gnumake nixpkgs#git nixpkgs#which nixpkgs#coreutils nixpkgs#findutils nixpkgs#ncurses nixpkgs#curl nixpkgs#gawk nixpkgs#stow nixpkgs#fuse nixpkgs#patchelf --extra-experimental-features 'nix-command flakes'` or set those packages in "environment.systemPackages = with pkgs;". For Docker, set "virtualisation.docker.enable = true;" in "/etc/nixos/configuration.nix", so this should install and enable Docker as service running in the background of system with `sudo nixos-rebuild switch`.

- Systems with immutable root filesystems (with exception of home directory and others depending on distro) like Steam Deck's SteamOS need rootless method of getting dependencies to avoid issues with wiping out installed packages after system's update or not to be able to write to certain path, like "/usr/local":
	1. Docker (Rootless mode): run `curl -fsSL https://get.docker.com/rootless | sh` to install Docker to user's home directory. For more details read [HERE](https://docs.docker.com/engine/security/rootless),
	2. Package managers:
		- [Homebrew](https://brew.sh): `brew install make git coreutils findutils ncurses curl gawk stow patchelf`,
		- [Nix Portable](https://github.com/DavHau/nix-portable): `nix-env -i gnumake git which coreutils findutils ncurses curl gawk stow fuse patchelf` or `nix profile install nixpkgs#gnumake nixpkgs#git nixpkgs#which nixpkgs#coreutils nixpkgs#findutils nixpkgs#ncurses nixpkgs#curl nixpkgs#gawk nixpkgs#stow nixpkgs#fuse nixpkgs#patchelf --extra-experimental-features 'nix-command flakes'`.

**Windows:**
1. Installing Git Bash:
- Download from [HERE](https://git-scm.com/downloads),
- Watch this video from 7:19 to 9:33 in [HERE](https://youtu.be/SWYqp7iY_Tc?t=439),

2. Git Bash can be found on start menu,

3. The rest of dependencies are installed, if you followed video,

4. Installing Docker Desktop:
- Download from [HERE](https://www.docker.com/products/docker-desktop),
- Watch this video from 6:07 to 8:36 in [HERE](https://youtu.be/_9AWYlt86B8?t=518).

**macOS:**
1. In terminal enter this following command:
- Homebrew: `brew install cmake autoconf automake pkgconfig libtool gawk stow p7zip rar curl makeicns`,
- MacPorts: `sudo port -Ncb install cmake autoconf automake pkgconfig libtool gawk stow perl5.28 libiconv p7zip unrar curl makeicns`.

# Installation
**Linux:**
1. Open terminal,

2. Enter `git clone https://github.com/Bijman/srb2bld`,

3. Go to downloaded directory: `cd srb2bld`,

4. Enter `sudo make install`, which will install to "/usr/local/bin". You can specify your path with variable PREFIX, for example `make install PREFIX=$HOME/.local`, which will copy script to "$HOME/.local/bin". Alternatively manually place script to your path, which is readable by shell (PATH environment variable), and change script's permissions to be executable: `chmod 755 [path to srb2bld script]`,

5. Check if you set properly other settings from "Configuration" section of README.

**Windows:**
1. Open Git Bash,

2. Go to your user directory (usually "C:/Users/[your username]"): `cd ~`,

3. Enter `git clone https://github.com/Bijman/srb2bld`,

4. Create directory "bin" with command: `mkdir ~/bin`,

5. Copy script to "~/bin": `cp ~/srb2bld/srb2bld ~/bin`,

6. Change script's permissions to be executable: `chmod 755 ~/bin/srb2bld`,

7. Open text editor for "~/.bash_profile": `nano ~/.bash_profile`,

8. In the opened text editor from previous step write new path to executables with environment variable PATH like `export PATH="~/bin:$PATH"` in "~/.bash_profile",

9. Enter `source ~/.bash_profile` or restart Git Bash.

**macOS:**
1. Open terminal,

2. Enter `git clone https://github.com/Bijman/srb2bld`,

3. Go to downloaded directory: `cd srb2bld`,

4. Enter `sudo make install`, which will install to "/usr/local/bin". You can specify your path with variable PREFIX, for example `make install PREFIX=$HOME/.local`, which will copy script to "$HOME/.local/bin". Alternatively manually place script to your path, which is readable by shell (PATH environment variable), and change script's permissions to be executable: `chmod 755 [path to srb2bld script]`,

5. Check if you set properly other settings from "Configuration" section of README.

# Configuration
**Linux:**
1. Add user to the "docker" group `sudo usermod -aG docker [username]` and enable Docker service with `sudo systemctl enable docker` or `sudo rc-update add docker default` or `sudo ln -s /etc/sv/docker /var/service/`, and then start the service with `sudo systemctl start docker` or `sudo rc-service docker start` or `sudo sv up docker`. For immutable systems (Steam Deck's SteamOS, Fedora Silverblue/Kinoite) enter: `systemctl --user enable docker` and `systemctl --user start docker`. After that, logout or reboot the system.

**Windows:**
1. User is already added to "docker" group and service will run, if Docker Desktop is installed and the system is logged out or rebooted.

**macOS:**
1. Set SDKROOT environment variable in "\~/.zshrc" or "\~/.bash_profile": `export SDKROOT=[path to .sdk file]` (usually macOS .sdk file is located in "/Library/Developer/CommandLineTools/SDKs" path, if you installed Homebrew or entered `sudo xcode-select --install`),
2. Enter `source ~/.bash_profile` or `source ~/.zshrc` or restart terminal.

# Compatibility (as of 23-07-2022)
|                       | Linux (glibc) x86/x64 | Linux (musl) x86/x64 | Linux (glibc) ARM | Windows x86/x64 | macOS x86/x64 |
| :-------------------: | :-------------------: | :------------------: | :---------------: | :-------------: | :-----------: |
| SRB2                  |          ✅           |         ✅           |        ✅         |        ✅       |       ✅      |
| SRB2 Uncapped PLUS    |          ✅           |         ✅           |        ✅         |        ✅       |       🟨**    |
| SRB2 NetPlus          |          ✅           |         ✅           |        ✅         |        ✅       |       ⛔      |
| SRB2 rphys            |          ✅           |         ✅           |        ❔         |        ⛔       |       ⛔      |
| SRB2 VR               |          ✅           |         ✅           |        ✅         |        ✅*      |       ⛔      |
| SRB2 v2.1 Legacy      |          ✅           |         ✅           |        ✅         |        ✅       |       ✅      |
| SRB2 v2.0             |          ✅           |         ✅           |        ✅         |        ✅*      |       ⛔      |
| SRB2 Final Demo       |          ✅*          |         ⛔           |        ✅*        |        ✅*      |       ⛔      |
| SRB2 Persona          |          ✅           |         ✅           |        ✅         |        ✅       |       ✅      |
| SRB2 Kart             |          ✅           |         ✅           |        ✅         |        ✅       |       🟨***   |
| SRB2 Kart Moe Mansion |          ✅           |         ✅           |        ✅         |        ✅       |       ⛔      |
| SRB2 Kart VR          |          ✅           |         ✅           |        ✅         |        ✅*      |       ⛔      |
| wadcli                |          ✅           |         ⛔           |        ✅         |        ⛔       |       ⛔      |
| SLADE                 |          ✅           |         ✅           |        ⛔         |        ⛔       |       ✅      |

**Legend:**

✅ - Builds and runs successfully.

🟨 - Builds successfully, but may encounter errors, when starting game, or get performance issues. Patches may apply.

⛔ - Building failure.

*Only 32-bit binaries are currently supported. SRB2 v2.0 has graphical issues when running with OpenGL on Linux and Windows.

**Compiles successfully with patch for commit d4d1181ec6f without setting -DSRB2_CONFIG_HAVE_DISCORDRPC=ON compilation flag, but there may be some slowdowns, when running game.

***Compiles successfully, but it can throw SIGABRT error on some macOS versions. Compiled build runs fine on macOS 10.14/Mojave.

# Usage (from help text)
```
Build and install SRB2/SRB2Kart from source.

Usage: srb2bld [OPTIONS]
  OPTIONS:
     -h, --help                             Show this help text.
     -ab, --appbundle                       Compile and create distributable App Bundle of SRB2/SRB2Kart build, which is packaged in DMG file (macOS only).
     -ai, --appimage                        Compile and create distributable AppImage of SRB2/SRB2Kart build (Linux only).
     -c, --compatibility                    Display compatibility table of compiling SRB2/SRB2Kart builds for each operating system.
     -i, --install                          Compile and install SRB2/SRB2Kart build.
     -la, --listasset                       List downloaded SRB2/SRB2Kart assets.
     -lb, --listbuild                       List downloaded SRB2/SRB2Kart builds.
     -lc, --listconfig                      List compilation flags of installed SRB2/SRB2Kart builds.
     -li, --listinstalled                   List installed SRB2/SRB2Kart builds.
     -ra, --removeasset                     Remove downloaded asset for SRB2/SRB2Kart build.
     -rb, --removebuild                     Remove downloaded source code for SRB2/SRB2Kart build.
     -u, --user                             Install build to user's home directory (only works with -i/--install).
     -ui, --uninstall                       Uninstall SRB2/SRB2Kart build.
     -up, --upgrade                         Upgrade installed SRB2/SRB2Kart build.

  EXAMPLES:
     1. Compile and install SRB2/SRB2Kart build:
            srb2bld --install

     2. Compile and install SRB2/SRB2Kart build to user's home directory:
            srb2bld --install --user

     3. Compile and create AppImage of SRB2/SRB2Kart build (Linux only):
            srb2bld --appimage

     4. List installed SRB2/SRB2Kart builds:
            srb2bld --listinstalled

     5. Uninstall SRB2/SRB2Kart build:
            srb2bld --uninstall

     6. Display compatibility table of compiling SRB2/SRB2Kart builds for each operating system:
            srb2bld --compatibility

  NOTES:
     1. Old builds like SRB2 v2.0 and SRB2 Final Demo may not build/run properly on modern Linux distributions/macOS/Windows.

     2. WARNING for macOS users! This script makes changes from rpath to absolute paths within some libraries installed from Homebrew, MacPorts or compiled (mostly should affects libraries compiled by user), that are associated with SRB2 binary, so installing or making App Bundles would be successful. In the future this could make unexpected results with apps or SRB2 builds, that depend on those libraries.

     3. If you want to compile some builds with DiscordRPC support (SRB2 Uncapped Plus, SRB2 NetPlus, SRB2 Kart, SRB2 Kart Moe Mansion and SRB2 Kart VR), then type "HAVE_DISCORDRPC=1" (Linux/Windows) or "-DSRB2_CONFIG_HAVE_DISCORDRPC=ON" (macOS), when the script asks about optional compilation flags (using "srb2bld --install" command).

     4. If on Linux you get error with "/dev/fuse" or FUSE when running script, then load fuse module with "sudo modprobe fuse". You can write "fuse" in configuration file, usually in file "/etc/modules" or "/etc/modules-load.d/fuse.conf" or "/etc/conf.d/modules/fuse.conf", to automatically load this module at boot.

     5. If 64-bit Linux system has issues with creating or loading "Sonic Robo Blast 2 Final Demo" (AppImage or installed), make sure you have installed 32-bit versions of FUSE and glibc:

         - Debian/Ubuntu/Debian based/Ubuntu based: "sudo dpkg --add-architecture i386 && sudo apt update && sudo apt install fuse:i386 libc6:i386 zlib1g:i386",

         - Arch/Arch based: uncomment the [multilib] section in /etc/pacman.conf and do "sudo pacman -Syu --needed" and then use one of the AUR helpers that you have installed - "pikaur -S --needed lib32-fuse2 lib32-glibc" or "paru -S --needed lib32-fuse2 lib32-glibc" or "yay -S --needed lib32-fuse2 lib32-glibc",

         - Gentoo/Gentoo based: "ABI_X86=32 sudo -E emerge -av sys-fs/fuse sys-libs/glibc",

         - Fedora/Fedora based: "sudo dnf install fuse-libs.i686 glibc.i686" for Fedora Workstation/Server or "rpm-ostree install -A --allow-inactive fuse-libs.i686 glibc.i686" for Fedora Silverblue/Kinoite,

         - OpenSUSE/OpenSUSE based: "sudo zypper in libfuse2-32bit glibc-32bit",

         - Void: "sudo xbps-install -S void-repo-multilib && sudo xbps-install -Su && sudo xbps-install -S fuse-32bit glibc-32bit".

     6. If Linux system has issue with running build because of not found compiled libraries, even though they are installed, set: export LD_LIBRARY_PATH="/usr/local/lib:$LD_LIBRARY_PATH" in "~/.bash_profile" or "~/.zshrc".

     7. There are couple of patches applied within source code of games. Their purpose is to prevent conflicts of installing/running of multiple builds overlapping each other with the same names of directories for storing assets and configuration/saves. Other patches include fixing compilation for some builds on particular systems.

     8. If you choose branch other than default, configuration directory's name will be changed, for example ".srb2" will become ".srb2udmf", if "udmf" was chosen. Still remember to make backup of configuration/save files, before upgrading to next release of SRB2/SRB2Kart build, if you chose default branch or kept previously chosen different branch.

     9. In order to compile and install custom SRB2/SRB2Kart build (assuming it is not a very old one) from local or remote repository, write environment variables in shell's configuration file, like ".bash_profile" or ".zshrc", which are:

          - SRB2BLDGITPATH - path to local or remote repository,

          - SRB2BLDGITVER - chosen branch to download build from remote repository,

          - SRB2BLDASSETPATH - path to assets from local or remote path (supported links/paths:
               - websites with direct link to file, for example, "https://github.com/STJr/SRB2/releases/download/SRB2_release_2.2.10/SRB2-v2210-Full.zip",
               - mega.nz,
               - drive.google.com,
               - dropbox.com,
               - full path to downloaded archived file in formats supported by p7zip (https://www.7-zip.org) or full path to directory with build's assets, for example $HOME/Downloads/SRB2.zip for Linux and macOS or C:\Downloads\SRB2.zip for Windows.)

          EXAMPLES:
               1. export SRB2BLDGITPATH="https://github.com/STJr/SRB2"

               2. export SRB2BLDGITPATH="https://git.do.srb2.org/TehRealSalt/SRB2"

               3. export SRB2BLDGITPATH="$HOME/Builds/SRB2"

               4. export SRB2BLDGITPATH="C:\Builds\SRB2"

               5. export SRB2BLDGITVER="udmf"

               6. export SRB2BLDGITVER="master"

               7. export SRB2BLDASSETPATH="https://github.com/STJr/SRB2/releases/download/SRB2_release_2.2.10/SRB2-v2210-Full.zip"

               8. export SRB2BLDASSETPATH="https://mega.nz/file/JQswBDAA#IPXWeTmrXrI9YZx6zUznJQ2uIAHryv_WP1JxWfnKbts"

               9. export SRB2BLDASSETPATH="https://drive.google.com/file/d/1Vc-lHph8MxlnfaBZnv0NNpoFKhehmce6"

               10. export SRB2BLDASSETPATH="https://www.dropbox.com/s/5neoderzan6mbh3/SRB2PERSONA%20v1.3.3%20Full%20Installer.exe"

               11. export SRB2BLDASSETPATH="$HOME/Downloads/SRB2-Full.zip"

               12. export SRB2BLDASSETPATH="C:\Downloads\SRB2-Full.zip"

               13. export SRB2BLDASSETPATH="$HOME/Downloads/SRB2-Full"

               14. export SRB2BLDASSETPATH="C:\Downloads\SRB2-Full"

          Then choose "Build SRB2 Custom", when running script.

     10. Other environment variables to use. To activate them with value "1", do for example "export SRB2BLDDEBUG=1":

         - SRB2BLDDEBUG - Getting verbose output from script. Useful for reporting issues in https://github.com/bijman/srb2bld/issues.

         - SRB2BLDDEVMODE - For developers, who want to modify build's source code. Disables cleaning build and resetting changes to build's source code.
```

# Notes
1. Old builds like SRB2 v2.0 and SRB2 Final Demo may not build/run properly on modern Linux distributions/macOS/Windows.

2. WARNING for macOS users! This script makes changes from rpath to absolute paths within some libraries installed from Homebrew, MacPorts or compiled (mostly should affects libraries compiled by user), that are associated with SRB2 binary, so installing or making App Bundles would be successful. In the future this could make unexpected results with apps or SRB2 builds, that depend on those libraries.

3. If you want to compile some builds with DiscordRPC support (SRB2 Uncapped Plus, SRB2 NetPlus, SRB2 Kart, SRB2 Kart Moe Mansion and SRB2 Kart VR), then type "HAVE_DISCORDRPC=1" (Linux/Windows) or "-DSRB2_CONFIG_HAVE_DISCORDRPC=ON" (macOS), when the script asks about optional compilation flags (using "srb2bld --install" command).

4. If on Linux you get error with "/dev/fuse" or FUSE when running script, then load fuse module with `sudo modprobe fuse`. You can write "fuse" in configuration file, usually in file "/etc/modules" or "/etc/modules-load.d/fuse.conf" or "/etc/conf.d/modules/fuse.conf", to automatically load this module at boot.

5. If 64-bit Linux system has issues with creating or loading "Sonic Robo Blast 2 Final Demo" (AppImage or installed), make sure you have installed 32-bit versions of FUSE and glibc:

         - Debian/Ubuntu/Debian based/Ubuntu based: `sudo dpkg --add-architecture i386 && sudo apt update && sudo apt install fuse:i386 libc6:i386 zlib1g:i386`,

         - Arch/Arch based: uncomment the [multilib] section in /etc/pacman.conf and do `sudo pacman -Syu --needed` and then use one of the AUR helpers that you have installed - `pikaur -S --needed lib32-fuse2 lib32-glibc` or `paru -S --needed lib32-fuse2 lib32-glibc` or `yay -S --needed lib32-fuse2 lib32-glibc`,

         - Gentoo/Gentoo based: `ABI_X86=32 sudo -E emerge -av sys-fs/fuse sys-libs/glibc`,

         - Fedora/Fedora based: `sudo dnf install fuse-libs.i686 glibc.i686` for Fedora Workstation/Server or `rpm-ostree install -A --allow-inactive fuse-libs.i686 glibc.i686` for Fedora Silverblue/Kinoite,

         - OpenSUSE/OpenSUSE based: `sudo zypper in libfuse2-32bit glibc-32bit`,

         - Void: `sudo xbps-install -S void-repo-multilib && sudo xbps-install -Su && sudo xbps-install -S fuse-32bit glibc-32bit`.

6. If Linux system has issue with running build because of not found compiled libraries, even though they are installed, set `export LD_LIBRARY_PATH="/usr/local/lib:$LD_LIBRARY_PATH"` in "\~/.bash_profile" or "\~/.zshrc".

7. There are couple of patches applied within source code of games. Their purpose is to prevent conflicts of installing/running of multiple builds overlapping each other with the same names of directories for storing assets and configuration/saves. Other patches include fixing compilation for some builds on particular systems.

8. If you choose branch other than default, configuration directory's name will be changed, for example ".srb2" will become ".srb2udmf", if "udmf" was chosen. Still remember to make backup of configuration/save files, before upgrading to next release of SRB2/SRB2Kart build, if you chose default branch or kept previously chosen different branch.

9. In order to compile and install custom SRB2/SRB2Kart build (assuming it is not a very old one) from local or remote repository, write environment variables in shell's configuration file, like ".bash_profile" or ".zshrc", which are:

    - SRB2GITPATH - path to local or remote repository,

    - SRB2GITVER - chosen branch to download build from remote repository,

    - SRB2ASSETPATH - path to assets from local or remote path (supported links/paths:
        - websites with direct link to file, for example, "https://github.com/STJr/SRB2/releases/download/SRB2_release_2.2.10/SRB2-v2210-Full.zip",
        - mega.nz,
        - drive.google.com,
        - dropbox.com,
        - full path to downloaded archived file in formats supported by p7zip (https://www.7-zip.org) or full path to directory with build's assets, for example $HOME/Downloads/SRB2.zip for Linux and macOS or C:\Downloads\SRB2.zip for Windows.)
```
  EXAMPLES:
        1. export SRB2BLDGITPATH="https://github.com/STJr/SRB2"

        2. export SRB2BLDGITPATH="https://git.do.srb2.org/TehRealSalt/SRB2"

        3. export SRB2BLDGITPATH="$HOME/Builds/SRB2"

        4. export SRB2BLDGITPATH="C:\Builds\SRB2"

        5. export SRB2BLDGITVER="udmf"

        6. export SRB2BLDGITVER="master"

        7. export SRB2BLDASSETPATH="https://github.com/STJr/SRB2/releases/download/SRB2_release_2.2.10/SRB2-v2210-Full.zip"

        8. export SRB2BLDASSETPATH="https://mega.nz/file/JQswBDAA#IPXWeTmrXrI9YZx6zUznJQ2uIAHryv_WP1JxWfnKbts"

        9. export SRB2BLDASSETPATH="https://drive.google.com/file/d/1Vc-lHph8MxlnfaBZnv0NNpoFKhehmce6"

        10. export SRB2BLDASSETPATH="https://www.dropbox.com/s/5neoderzan6mbh3/SRB2PERSONA%20v1.3.3%20Full%20Installer.exe"

        11. export SRB2BLDASSETPATH="$HOME/Downloads/SRB2-Full.zip"

        12. export SRB2BLDASSETPATH="C:\Downloads\SRB2-Full.zip"

        13. export SRB2BLDASSETPATH="$HOME/Downloads/SRB2-Full"

        14. export SRB2BLDASSETPATH="C:\Downloads\SRB2-Full"
```
   Then choose "Build SRB2 Custom", when running script.

10. Other environment variables to use. To activate them with value "1", do for example "export SRB2BLDDEBUG=1":

        - SRB2BLDDEBUG - Getting verbose output from script. Useful for reporting issues in https://github.com/bijman/srb2bld/issues.

        - SRB2BLDDEVMODE - For developers, who want to modify build's source code. Disables cleaning build and resetting changes to build's source code.
