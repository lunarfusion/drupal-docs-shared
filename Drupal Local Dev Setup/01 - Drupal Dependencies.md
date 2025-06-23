UPDATED: JUNE 17, 2025

**CONTENTS**
1. Mac Installation
2. PC Installation (needs documentation)

------
In order to run a Drupal local development environment on your machine, you will need to install some dependencies. The following instructions should be carried out in your CLI.

-----
## Mac Installation

On mac, the CLI application is called Terminal. To access CLI on your mac, go to Applications > Terminal.

### 1 - Homebrew

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

#### Add Homebrew to your PATH

Run the following two commands in your terminal to add Homebrew to your **PATH**. Make sure to change "username" to your username as it is on your machine (find this in Macintosh HD > Users > username).

```
(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/username/.zprofile

eval "$(/opt/homebrew/bin/brew shellenv)"
```

### 2 - Git
```shell
brew install git
brew update
```


### 3- PHP
```shell
brew install php
```


### 4 - Composer
```shell
brew install composer
```

### 5 - Drush
https://github.com/drush-ops/drush-launcher#installation---phar

```shell
curl -OL https://github.com/drush-ops/drush-launcher/releases/latest/download/drush.phar
```

Make downloaded file executable: 

```shell
chmod +x drush.phar
```


Move drush.phar to a location listed in your `$PATH`, rename to `drush`:

```shell
sudo mv drush.phar /usr/local/bin/drush
```

### 6 - Orbstack

We use ddev with orbstack to manage our docker containers.

Download Orbstack:
https://orbstack.dev/download

or use Homebrew

```shell
brew install orbstack docker
```


### 7 - ddev

Ddev automates a lot of things that help us to spin up a local Drupal site.

```shell
brew install ddev/ddev/ddev
```

Confirm it is installed

```shell
ddev -v
```

Run mkcert -install so your browser trusts Ddev

```shell
mkcert -install
```


----

## PC Installation

TODO - Need help from a PC user to fill in this section.