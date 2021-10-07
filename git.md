- [branch](#branch)
  - [1.브랜치를 쓰는 이유](#1브랜치를-쓰는-이유)
  - [2.브랜치 기본 사용법](#2브랜치-기본-사용법)
  - [3. 머지란?](#3-머지란)
  - [4. conflict 해결 방법](#4-conflict-해결-방법)
- [두개의 git 계정 사용하기](#두개의-git-계정-사용하기)

# branch

## 1.브랜치를 쓰는 이유

master - 상품에 포함되어도 되는 내용
기능별, 리팩토링별, 버그픽스별 브랜치를 사용한다면 병렬적 업무진행 가능
깃의 전환이 빠른이유 : 이전버전을 포인터 형태로 가리키고 있기때문에, 변경되지 않은 커밋은 그 이전 데이터를 가리키는 포인터 형태로 있기때문에

## 2.브랜치 기본 사용법

![스크린샷 2021-10-05 오후 6 03 12](https://user-images.githubusercontent.com/70263597/135993570-06c64b7e-83ad-4578-8241-2e1d84d288c5.png)

- **git branch** -> 현재 repository안에 있는 브랜치 확인 가능-> 내컴퓨터 안에 있는 브런치만 보여줍니다
- **git branch --all** 서버(github와 같은)에있는 브랜치를 볼 수 있습니다.
- **git branch new-branch** ->new-branch라는 이름의 브랜치가 만들어졌고 무언가가 새로 만들어진게 아니라 new-branch라는 새로운 포인터가 동일한 커밋을 가르키고 있습니다.
만들어지기만 하고 현재 브랜치는 여전히 masterbranch
- **git switch new-branch** -> 새로운 브랜치로 이동이 가능
ex) git switch master
- **git switch -C new-branch2** -> 만들어짐과 동시에 현재 브랜치를 이동시키는 명령
- **git checkout** -> git log or git hist로 해쉬값 복사후 -> git checkout [해쉬] 해당하는 커밋으로 이동-> git hist ->방금 체크아웃한 버전에 해당하는 버전으로 이동가능
- **git checkout -b testing** -> 새로운 브랜치가 만들어지고 원하는 경로로 이동가능
- **git branch -v** ->간단한 정보 열람가능
- **git --merge** 머지된것 볼 수 있음
- **git branch --no-merge** -> masterbranch에서 파생된 다른 커밋
- **git branch -d new-branch2** -> new-branch2 삭제
- **git push origin --delete new-branch2** -원격 서버에 저장된 new-branch2 삭제
- **git branch --move fix fix-wlecome**-> fix가 fix-welcome으로 변경
- **git push --set-upstream origin fix-welcome** -> 원격 서버에 저장된 이름변경

- *git checkout -b test
echo test > test.txt
git  add .
git commit -m"test"
git checkout master
git hist master..test or git log master..test 마스터와 테스트 사이에 있는 커밋만 볼 수 있음
git diff master..test* ->코드도 확인 할 수 있음

## 3. 머지란?
  
- 3.1 fast-forward merges 가장 깔끔,간단
  - 단점 : masterbranch에 머지가 되었다는 히스토리가 남지 않습니다.
  - git hist
  - git git checkout feature-a(브랜치이름) git checkout master
  - git merge feature-a -> master 브랜치에 머지
  - git branch -d feature-a -> 필요없어진 feature-a를 삭제</br>
  
- 3.2 히스토리를 남기고 싶다면 기존의 masterBranch를 가리키고 있던브랜치와 masterBranch를 합쳐서 새로운 커밋을 만들면 됩니다
  - git merge --no-ff feature-c(새로만들고 커밋한 브랜치) ->커밋명령어 입력하라고 나옵니다 -> 종료후 gitist -> merge commit을 확인 가능 git branch -d feature-c -> 로그로 표기됨

</br>
  
- 3.3 tree-way merge

  - fast-forward가 불가능하다면 commit 메세지를 입력하도록 진행합니다.
  - git hist
  - git merge feature-b -> 안됨-> 커밋메세지 뜸
  - -> git hist를 이용해 보면 새로운 머지 커밋이 만들어져있는것 확인 가능

## 4. conflict 해결 방법

**-> 깃이 머지를 할떄 자동적으로 해결이 안되서 충돌이 날때 ex) 두가지의 브랜치에서 동일한 파일을 수정햇다면 어떤 내용을 적용해야할지 모르겠을때 conflic이 발생하게 됨
git status로 확인을 해보면 에러메세지 확인 가능**

ex) open main.txt ->파일을 열어 선택해서 나머지 수동으로 삭제 해주고     tip.은근슬쩍 변경사항 자잘한거 꽂아놓으면 안됨
 -> 저장후 git status ->git add 이용하라고 메세지뜸
 ->git add main.txt
 git status -> git merge --continue -> fast-forward가 아니기떄문에 커밋메세지가 뜹니다.
 ->git hist 으로 확인
  checkcheck

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
cheeck
