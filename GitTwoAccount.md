# 두개의 git 계정 사용하기
  https://dublin-java.tistory.com/62
cd  .ssh/
`vi config`  `cat ~/.ssh/config`
```
# personal account-austin 
Host github.com-austin-thwoo
	HostName austin-thwoo@naver.com
	User austin-thwoo
   	IdentityFile ~/.ssh/austin
# company
Host github.com-company
	HostName public@laonstory.com
	User laon-public
	IdentityFile ~/.ssh/company
```
ssh
clone  git@github.com:austin-thwoo/TIL.git
->
git clone git@github.com:austin-thwoo/TIL.git
git clone git@github.com:company/TIL.git
git commit & git push 
git config --local user.namm&user.email

