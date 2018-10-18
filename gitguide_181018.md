# 181018_Today I learned

##Git Data Transport Commands

git init을 하는 순간, 
stage 와 local repository라는 가상공간이 2개 생긴다.

add하면 stage에 올라가고 그 자료를 라벨링 하는 것이 commit, 그러면 라벨링 되서 local repository로 들어간다.

push하면 remote repository로 넘어가는데 git에서 실제로 보여지게 된다.

## Git을 시작하는 2가지 방법

### 1. 첫번째방법

mkdir react-sample

directory이름과 폴더 이름을 같게 하는게 좋다

git --version : git을 command가 인식을 하고 있는지 부터 확인

git init 

git status : git initialize가 되었는지 확인

initial commit은 처음시작했다는 뜻이다.

touch README.md : 

vi README.md

vim에서는 아무것도 없는 상태에서 i를 입력하면 그때부터 텍스트 편집을 할 수 있다.
insert 모드를 켜서 편집을 하고 esc 로 나와서 다른 기능을 사용한뒤 다시 insert로 들어가서 편집.


:  - Shift + 세미콜론

:q!  => 이제까지 썼던 모든 내용을 저장하지 않고 나가기

:wq  => 저장하고 나가라

cat README.md  => 문서의 내용을 다 보여줌. catnate의 줄임말.

git config --global core.editor "vim" :나는 깃에서 vim으로 사용하겠다는 선언
 
git config --list : 사용자정보

```
DOC : Create README.md

I created README.md to describe this project.
```

### 2. 두번째 방법

git ignore이라는 방법이 있다.

GNU public license 조심 => 이런거 영리적으로 쓰면 소송당해염. 무서웡.

vi .gitignore : git이 볼필요 없는 파일들 리스트업하기 위해 쓰는 명령어

hidden/  => 히든이라는 파일을 만들어라 그럼 안에 있는 파일들이 다 무시된다.
*.py  => 확장자가 py인 모든 파일을 선택하는거야 
.gitignore =>  이 파일마저 무시해라 라는 의미

뭐든 쓸때 내용이랑 명령어랑 겹치지 않게 주의하기 !



## Branch
모든 Developer에서 Master로 Merge되는 과정.

### What is branch?
분기점을 생성하고 독립적으로 코드를 변경할 수 있도록 도와주는 모델

ex)

##### master branch

```
print('hello world!')

```
##### another branch

```
for i in range(1,10):
    print('hello world for the %s times!' % i)
```

##### branch 

- Show available local branch $ git branch

- Show available remote branch $ git branch -r

- Show available All branch $ git branch -a

- Create branch $ git branch stem

- Checkout branch $ git checkout stem

- Create & Checkout branch $ git checkout -b new-stem

- make changes inside readme.md $ git commit -a -m 'edit readme.md' $ git checkout master

- merge branch $ git merge stem



#### 협업할때 merge 하거나 conflict 해결하는 과정
--

1) 레포만들기 -> master, develop

2) 상대방 레포 방문한뒤, fork -> clone

3) branch 따서 작업하고 -> push(feature) -> push(develop)

4) git hub-> develop -> develop -> pull request 만들기

5) 그 저장소로 이동해서 간단한 내용에 대한 comment 남기기

6) Merge

--

## Reference

git pull origin master
몰라.. git flow 검색해봐 초로미..
http://woowabros.github.io/experience/2017/10/30/baemin-mobile-git-branch-strategy.html
=> 참고해 초로미 화이팅!

https://ko.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow
=> 이것도 참고해 초로미 화이팅 !



