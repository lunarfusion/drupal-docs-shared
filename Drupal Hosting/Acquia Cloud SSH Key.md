
Create an SSH key on your machine and then upload it via Acquia's website

----


## 1 - Generate the key in your Terminal

```
ssh-keygen
```


## 2 - When prompted for the directory, enter the following 
(in place of yourusername, type your own computer user directory name):

```
/Users/yourusername/.ssh/id_rsa.pub
```


## 3 - Copy the key

```
pbcopy < ~/.ssh/id_rsa.pub
```


## 4 -  Upload your SSH Key to Acquia

1. Log into Acquia and go to "SSH Keys" https://cloud.acquia.com/a/profile/ssh-keys
2. Select "Add SSH Key"
3. Paste in the key you copied 