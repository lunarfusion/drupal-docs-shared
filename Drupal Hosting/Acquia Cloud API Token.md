
Create a token on Acquia's site, then authorize it on your machine with Acquia's CLI software.

-----


## Install Acquia CLI
https://docs.acquia.com/acquia-cloud-platform/add-ons/acquia-cli/acquia-cli-installation

### 1 - Download Acquia CLI

```
curl -OL https://github.com/acquia/cli/releases/latest/download/acli.phar
```


### 2 - Make the download executable

```
chmod +x acli.phar
```


### 3 - Move the download and make it globally accessible

```
mv acli.phar /usr/local/bin/acli
```


If the response is "Permission denied," do

```
sudo mv acli.phar /usr/local/bin/acli
```

-----
## Create an Acquia API Token


### 1 - Generate the Key

1. Go to https://profile.acquia.com/tokens
2. Log in
3. Select "+ Create token"
4. Copy the two numbers it displays (the ID and the Secret)


### 2 - In your Terminal, do

```
acli auth:login
```


### 3 - When it asks if you want to generate a new key, type 

```
no
```

It will then prompt you to enter your Key ID and Secret (the two numbers you copied when you created the token)

### 4 - Paste token ID and Secret