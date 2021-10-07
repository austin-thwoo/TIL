# 2. setUp

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
 ![picture/git auto crlf.png](core.autocrlf)
 