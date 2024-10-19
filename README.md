# JDInstaller

This Ansible playbook is designed to initialize a fresh Ubuntu installation with packages and configurations that suit my personal preferences. While it is
specifically tailored to my needs, it can be easily adapted to different setups. Every major Ansible role can be individually enabled or disabled by modifying
its respective value in `group_vars/all.yml`.

## Table of Contents

- [Introduction](#introduction)
- [How to Use](#how-to-use)
    - [Download the Repository](#download-the-repository)
    - [Run the Installation](#run-the-installation)
    - [Run Single Roles](#run-single-roles)
- [Playbooks](#playbooks)
- [Roles](#roles)
- [Contributions](#contributions)
- [Acknowledgements](#acknowledgements)

## Introduction

This project uses [Ansible](https://www.ansible.com/) to automate the setup of Ubuntu installations. By running the main playbook (`ubuntu-setup.yml`), the
system will be configured with a range of packages and settings that I prefer. You can easily customize the playbook by enabling or disabling specific roles in
`group_vars/all.yml`.

### What is a Role?

An Ansible role is a modular way of organizing playbooks. Roles allow you to break up a complex playbook into reusable components. Each role can include tasks,
variables, handlers, and more, and they are self-contained to allow easy inclusion into other playbooks. Roles in this project mainly deal with the installation
of various software packages.

## How to Use

### Download the Repository

You can either download the ZIP file of this repository or clone the repository using git.

#### Option 1: Download ZIP

1. Go to this link: [Download ZIP](https://github.com/leinardi/JDInstaller/archive/refs/heads/master.zip)
2. Extract the ZIP file:

   ```bash
   unzip JDInstaller-master.zip
   cd JDInstaller-master
   ```

#### Option 2: Clone via Git

1. Install `git` if it is not already installed:

   ```bash
   sudo apt update
   sudo apt install git
   ```

2. Clone the repository:

   ```bash
   git clone https://github.com/leinardi/JDInstaller.git
   cd JDInstaller
   ```

### Run the Installation

Once you have the repository on your machine, you can start the installation process by running:

```bash
make install
```

This command will:

1. Automatically install Ansible if it’s not already installed.
2. Launch the main playbook (`ubuntu-setup.yml`) to configure the system.
3. Prompt for the sudo password of the current user.

Alternatively, you can run the playbook manually:

```bash
ansible-playbook ubuntu-setup.yml --ask-become-pass
```

### Run Single Roles

Each role has an associated tag (same as the role name). To install a specific role, use the `TAGS` parameter like this:

```bash
make install TAGS=virtualbox
```

Or manually run the playbook with specific tags:

```bash
ansible-playbook ubuntu-setup.yml --ask-become-pass --tags=virtualbox
```

### Reset Configuration

To generate/reset the `group_vars/all.yml` file to the default values, run:

```bash
./generate-group-vars.sh
```

## Playbooks

Below is a list of the playbooks that are included in this project. You can enable or disable each one by modifying the respective variable in
`group_vars/all.yml`.

| Playbook          | Enabled by Default | Description                               |
|-------------------|--------------------|-------------------------------------------|
| `common.yml`      | ✅                  | Sets up common packages and settings.     |
| `desktop.yml`     | ✅                  | Installs desktop-specific applications.   |
| `development.yml` | ✅                  | Installs development tools and libraries. |
| `gaming.yml`      | ✅                  | Installs gaming-related tools.            |
| `work.yml`        | ⛔                  | Installs work-related applications.       |

## Roles

The tables below provide an overview of the roles included in this project. Each role can be enabled or disabled via `group_vars/all.yml`. The "Enabled by
Default" column shows whether the role is active by default. Even if a role is enabled by default, if the relative playbook is disabled via
`group_vars/all.yml`, the role will not be executed. To run a specific playbook or role, make sure both the playbook and the role are enabled in
`group_vars/all.yml`.

### Playbook: `common.yml`

| Role    | Enabled by Default | Description                                           |
|---------|--------------------|-------------------------------------------------------|
| `snapd` | ✅                  | Installs snapd for managing Snap packages.            |
| `ufw`   | ⛔                  | Installs and configures Uncomplicated Firewall (UFW). |

### Playbook: `desktop.yml`

| Role               | Enabled by Default | Description                                           |
|--------------------|--------------------|-------------------------------------------------------|
| `chrome`           | ✅                  | Installs Google Chrome.                               |
| `chromium`         | ✅                  | Installs the open-source Chromium browser.            |
| `doublecmd`        | ✅                  | Installs Double Commander, a file manager.            |
| `earth`            | ✅                  | Installs Google Earth Pro.                            |
| `edge`             | ⛔                  | Installs Microsoft Edge browser.                      |
| `firefox`          | ✅                  | Installs Mozilla Firefox.                             |
| `flatpak`          | ✅                  | Installs Flatpak for managing app installations.      |
| `gimp`             | ✅                  | Installs GIMP, a graphic editor.                      |
| `gparted`          | ✅                  | Installs GParted, a partition editor.                 |
| `graphics_drivers` | ✅                  | Installs proprietary drivers for graphics cards.      |
| `gsettings`        | ✅                  | Configures GNOME settings via gsettings.              |
| `handbrake`        | ⛔                  | Installs HandBrake, a video transcoder.               |
| `inkscape`         | ✅                  | Installs Inkscape, a vector graphics editor.          |
| `insync`           | ✅                  | Installs Insync, a Google Drive sync client.          |
| `libreoffice`      | ✅                  | Installs LibreOffice, a free office suite.            |
| `mainline`         | ✅                  | Installs Mainline, a tool for managing Linux kernels. |
| `meld`             | ✅                  | Installs Meld, a file comparison tool.                |
| `nautilus_plugins` | ⛔                  | Installs plugins for the Nautilus file manager.       |
| `nordvpn`          | ✅                  | Installs NordVPN client.                              |
| `openjre`          | ⛔                  | Installs OpenJRE, a Java runtime environment.         |
| `sweethome3d`      | ✅                  | Installs Sweet Home 3D, an interior design app.       |
| `timeshift`        | ⛔                  | Installs Timeshift for system backups.                |
| `ulauncher`        | ✅                  | Installs Ulauncher, an application launcher.          |
| `virtualbox`       | ✅                  | Installs VirtualBox for running virtual machines.     |
| `vlc`              | ✅                  | Installs VLC media player.                            |
| `xfburn`           | ✅                  | Installs Xfburn, a tool for burning CDs and DVDs.     |

### Playbook: `development.yml`

| Role        | Enabled by Default | Description                                       |
|-------------|--------------------|---------------------------------------------------|
| `filezilla` | ✅                  | Installs FileZilla, an FTP client.                |
| `filezilla` | ✅                  | Installs FileZilla, an FTP client.                |
| `git`       | ✅                  | Installs Git, a version control system.           |
| `openjdk`   | ✅                  | Installs OpenJDK, a Java development environment. |
| `python`    | ✅                  | Installs Python.                                  |
| `slack`     | ⛔                  | Installs Slack for team communication.            |

### Playbook: `gaming.yml`

| Role       | Enabled by Default | Description                                      |
|------------|--------------------|--------------------------------------------------|
| `discord`  | ✅                  | Installs Discord for chatting and VoIP.          |
| `gamemode` | ✅                  | Installs GameMode, a tool for optimizing gaming. |
| `mangohud` | ✅                  | Installs MangoHud, a gaming performance overlay. |
| `steam`    | ✅                  | Installs Steam, a gaming platform.               |

### Playbook: `work.yml`

| Role                        | Enabled by Default | Description                                   |
|-----------------------------|--------------------|-----------------------------------------------|
| `globalprotect_openconnect` | ✅                  | Installs OpenConnect for GlobalProtect VPN.   |
| `mattermost`                | ✅                  | Installs Mattermost, a team chat application. |
| `zoom`                      | ✅                  | Installs Zoom, a video conferencing tool.     |

Each playbook can be customized, and roles enabled or disabled as required via `group_vars/all.yml`. By default, the roles listed in `work.yml` are disabled,
but can be easily enabled if needed.

## Contributions

Bug fixes and improvements to the Ansible code are welcome. However, please note that the list of default software installations is strictly based on my
personal preferences. I will accept pull requests adding roles for software that I don't use, but they must be disabled by default via `group_vars/all.yml`.

**Before opening a pull request, please create an issue to describe the feature you would like to add and wait for my approval.** This helps avoid unnecessary
work.

You can run static analysis on shell and YAML files with:

```bash
make check
```

This command will also regenerate the `group_vars/all.yml` file.

## Acknowledgements

This project is inspired by [ansible-ubuntu-desktop](https://github.com/sys0dm1n/ansible-ubuntu-desktop). Many thanks
to [@sys0dm1n](https://github.com/sys0dm1n) for sharing their playbook.

