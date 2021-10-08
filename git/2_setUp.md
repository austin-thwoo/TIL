# 2. setUp

 [1. installation of necessary things](#1-installation-of-necessary-things)
 [2. user setting](#2-user-setting)
 [3. git command](#3-git-command)
 [4. git init](#4-git-init)

## 1. installation of necessary things

[linux command](https://youtu.be/EL6AQl-e3AQ)

```java
if(you use vscode){
Markdown All in One
Markdown Preview Enhanced
Markdownlint
-> Extentions plz
} 
```

git install confirm

```
austin@laonstory-mac-austinui-MacBookPro ~ % git --version
git version 2.31.1
```

[gitDown](git-scm.com/downloads)

## 2. user setting

```
 austin@laonstory-mac-austinui-MacBookPro ~ % git config --list
credential.helper=osxkeychain
user.name=laon-public
user.email=public@laonstory.com
core.autocrlf=input
alias.st=status
alias.hist=log --graph --all --pretty=format:'%C(yellow)[%ad]%C(reset) %C(green)[%h]%C(reset) | %C(white)%s %C(bold red){{%an}}%C(reset) %C(blue)%d%C(reset)' --date=short
austin@laonstory-mac-austinui-MacBookPro ~ % 
```  

```
git config --global user.name "[userName]"
git config --global user.email [userEmail]
git config user.name
git config user.email
got config --global core.autocrlf input/true
```

 ![picture/git auto crlf.png](git/../picture/git%20auto%20crlf.png)

## 3. git command

- git + [명령어] + [옵션]
  ex) git add -option

## 4. git init

```
 - mkdir git
 - cd git 
 - ls -al ->아무것도 없음
 - git init -> 깃초기화
 - ls -al 
- rm -rf .git ->깃 삭제
- git init ->깃 초기화
- git status 
- git config --global aliast.st status
- git st == git status
- git config --h
```
