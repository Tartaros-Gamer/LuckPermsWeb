![](https://i.imgur.com/ToguFkQ.png "Banner")
# LuckPermsWeb
[![Netlify Status](https://api.netlify.com/api/v1/badges/1858b23b-5dcb-49e3-ad54-45ca005de4e0/deploy-status)](https://app.netlify.com/sites/luckpermseditor/deploys)
[![Discord](https://img.shields.io/discord/241667244927483904.svg?logo=discord&label=)](https://discord.gg/luckperms)

[LuckPerms](https://github.com/lucko/LuckPerms) is a permission plugin for Minecraft servers, written in Java.

LuckPermsWeb (this repository) contains the website for the project and a number of web apps which supplement the plugin, all written in HTML/JavaScript using the [Vue](https://vuejs.org/) framework.

### Branches

* Development takes place on the `master` branch.
* The production site at [luckperms.net](https://luckperms.net/) is automatically built from the `production` branch.
* An older (pre Vue rewrite) version of the site is on the `v1` branch.

### Status

The current master branch is a full re-write and not complete.

**To do:**
- [x] Home page (unrelesased)
- [x] Download page (unreleased)
- [x] Wiki (unreleased)
- [x] Web editor (live beta)
- [x] Verbose report (unreleased)
- [x] Tree report (unreleased)

Most of the above is in development on the `website` branch. A live version of this branch can be found at https://luckperms.turbotailz.com

## Setup

### Automatic setup
The automatic setup is fairly straight forward.

#### Installation
Just run those commands as a user that has `sudo` permissions:

```sh
git clone --branch website https://github.com/lucko/LuckPermsWeb.git
LuckPermsWeb/installer/install.sh
```

Answer the questions and it will install all missing prerequisites and the editor itself.

#### Update
Just update the repo and run the install script again:

```sh
cd LuckPermsWeb
git reset --hard
git pull
installer/install.sh
```

#### Uninstallation
Run this command:

```sh
LuckPermsWeb/installer/uninstall.sh
```

#### Caveats
There are a few things to watch out for:

- This is designed to use [nginx](https://www.nginx.com/) as the webserver. Support for Apache is planned (if you know Apache well enough, consider reaching out
  to us so we can add it!)
- Automatic package installation only works on Debian-based distros, as `apt-get` is used to install the missing prerequisites. If you're not on Debian-based
  distro, be sure to have these commands available, then it'll work too:
  - `java` (needed for bytebin)
  - `jq`
  - `nc`
  - `nginx`
  - `netstat`
  - `sed`
  - `wget`
  - `certbot` (only if you want to use HTTPS and want the certificate to be generated by Let's Encrypt)
- The bytebin will be setup using a systemd config. If you are not running on a system that uses systemd, the script will not work and you have to set it up
  yourself.

### Manual setup
Setting up the project manually locally is simple, all you need is Node installed on your computer, then you can clone the repo and run:
```
npm install
```

#### Compile and setup hot-reloads for development
Once you've installed the dependencies, you can run the project locally easily by running:
```
npm run serve
```

#### Compile and minify for production
If you want to build the project to a folder that can be access via a webserver, running this command will build the project in the `dist` folder:
```
npm run build
```
