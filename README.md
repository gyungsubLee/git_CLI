# git_정리(복습)

> ### sparta_git 3주차 정리 필요
> ### pull 재정리 필요
> ### reset-옵션(인덱스) 정리 필요

<br/>

## git 프로젝트 사용)
개인)

    1. 프로젝트에 git 연결하기 - 프로젝트 폴더 생성 및 git initailize(초기화)

    2. issue로 작업 구조화하기

    3. 작업 issue연동하여 commit하고 push하기


협업)

    1. issue 프로젝트 작업 나누고 할당하기

    2. 개인 branch를 만들어  할당된 작업 진행하기

    3. 각 작업 개발용 branch에 merge 하기

    4. PR, 코드리뷰를 진행하여 release용 branch에 merge하기 

    5. 작업이 끝난 branch 삭제하고 새 작업 branch 만들기 (branch 충돌 방지)

---

<br/>

+)

    issue는 branch 관계없이 #으로 tag가능

    sub branch의 cummit 내역은 main branch에 merge하지 않으면 반영이 안됨.

    시작 때 README issue도 만들어 정리 -> 깔끔함?, 굳이 필요없을 것 같다

    cummit을 기능 단위로 쪼개자. cummit message 규칙 정하고 쓰자.

<br/><br/>

# **git 명령어)**

## 👉 **프로젝트에 git 설정: git initailize(초기화)**

    git init

<br/>

## 👉 **변경사항 임시저장(stash)** 
> 다른 브랜치 checkout 시 현재 branch의 작업이 사라진다. 
**아직 완료되지 않는 작업**인 경우 commit 말고 **stash 처리 후** 다른 branch 작업 후 **다시 불러와 작업**을 진행한다. 

<br/>

### ● 완료되지 않는 작업 임시저장(stash 처리) 
>해당 명령어를 통해 스택에 새로운 stash를 만들어 저장<br/>
(staged(add)한 파일도 저장가능)

    git stash
    git stash save

<br/>

### ● 임시저장(stash) 목록 확인 
> 스택에 저장된 stash list를 확인 

    git stash list

<br/>

### ● stash 가져오기(임시저장한 작업 다시 가져오기)
> stash는 브랜치 상관없이 가져올 수 있으며 
>충돌이 일어난 경우 git이 알아서 알려준다. 

    git stash apply ( 가장 최근 stash 가져옴)

    git stash apply [stash명] ( <stash명(ex. stash@{2})> 가져옴 )

<br/>

>  위 명령어는 staged(add) 상태의 파일을 자동으로 staged(add) 상태로 만들어 주지 않는다.<br/>
> ```--index``` 옵션을 통해 stage 상태까지 복원 

    git stash apply --index

<br/>

### ● stash 제거
> stash를 가져온 후 스택에는 여전히 stash가 남아있다. 따라서 필요없는 stash는 제거한다.

    git stash drop  ( 가장 최근 stash 제거)

    git stash drop [stash명] (stash명 제거)

<br/> 

> stash 적용과 동시에 스택에서 제거

    git stash pop

<br/>

●  stash 되돌리기

    git stash show -p | git apply - R ( 가장 최근 stash 되돌리기)

    git stash show -p [stash명] | git apply -R (stash명 되돌리기)

<br/>

> Tip) alias -> 명령어 수정 -> 간편하게 사용

    git config --global alias.stash-unapply 'git stash show -p | git apply - R'( stash-unapply로 명령어 수정 )
    
    git stash apply
    #... work work work

    git stash-unapply

<br/>
<br/>


## 👉 **변경 사항 add(staged)** 

### ● 변경된 파일 및 add 상태 확인  
    
    git status

<br/>

### ● 변경 작업 add(staging) 

    git add <file>  -> add(staging) 할  파일 선택, 전체선택(.)

<br/>

### ● add 취소

    git restore <file> -> 취소할 파일 선택, 전체선택(.)


>![add(staging)취소, 파일 디렉토리](https://user-images.githubusercontent.com/95308384/170196847-1284dc2d-72db-4d81-8f9b-5d6b790ea595.png)
>
>
>![터미널 디렉토리](https://user-images.githubusercontent.com/95308384/170198540-a9d794c7-3874-4948-ae0f-2bf0136e4df2.png)
>
>파일은 터미널 디렉토리 기준으로 작성<br/>
파일명에 "" 안해도 됨

<br/><br/>


## 👉 **git commit, push**

add한 파일 commit

    git commit -m "메세지 입력"

commit 추적

    git log (나가기:Q)

git branch 이름변경(Master -> Main)
    
    git branch -M main

로컬repo, 원격repo 연결(branch Tracking)

    git remote add <branch명(main -> origin> <url> (url -> github-repo에서 확인)

push

    git push -u origin main ( 자세한 내용 밑의 push section에서 확인)

---
<br/><br/>

## 👉 **commit 수정**
### ● 로컬repo commit 수정
> ```작업 내역 수정```의 경우 수정한 작업을 add(staged)한 후 commit_amend 

    git commit --amend -m <수정메세지>

<br/>

### ● 원격repo commit  수정

    git push --force <branch명>

> 로컬repo의 commit history를 원격repo의 commit history에 덮어씌운다.(```강제push```) 

---
<br/>

## 👉 **commit 삭제 (revert, reset)** -> revert, reset-옵션 추가정리 필요
### ● 로컬repo commit 삭제

    git reset <옵션><돌아가고싶은 커밋 id>

<br>

    git reset HEAD 파일명(없으면 add한 cummit 전체취소)

> HEAD: 가장 최신commit <br/>
> HEAD ~ '숫자': HEAD에서 HEAD기준으로 '숫자'번째까지 아래 commit) 

<br>

옵션: 3가지

    --hard: 돌아가려는지점 이후 모든 내용 삭제.

    --soft: 돌아가려는 지점으로 돌아가지만 add 내용은 남아 있는다.

    --mixed: default 값이다. 돌아가려는 지점으로 돌아가지만 인덱스는 초기화 된다. 

<br/>

### ● 원격repo commit 삭제

    git push -f <원격repo_branch명> <로컬repo_branch명>

<br/>

> -f : force의 약어 <br/>
> origin: 원격repo의 main branch <br/>
> main: 로컬repo의 main branch


    git push -f origin main (로컬_main의 commit_history를 원격_main에 덮씌운다.)



---


<br/><br/>

## 👉 **PUSH**

    push: git push <원격저장소명> <브랜치명>
>git clone을 통해 가져왔다면  기본 원격저장소 이름은 origin(main_branch)이다.

<br>

### ● 인자생략1

    git push -u orign my-feature

-u : 옵션을 사용하여 최최의 한 번만 저장소명과 브랜치 명을 입력하고 그 이후에 모든 인자 생략 가능
    
    ex)
    git commit -m "change 1"
    git push

<br>

### ● 인자생략2

    git config --global push.defalut current

    -> git push

여러 브랜치를 넘나 들면서 작업하는 경우 최초의 한번 인자는 넘기는 것도 귀찮다.
대부분의 경우 로컬repo와 원격repo가 동일한 branch 이름을 사용하기 때문에 현재 branch를 기준으로 git push 명령어가 작동되가 설정한다. 
<br>
> **push.default**,**current**로 가능

 

<br>

### ● 원격repo에 강제 push (변경된 commit(코드) 덮씌우기)
```force 옵션```을 통해 강제로 push 한다.

    git push -f <원격repo_branch명> <로컬repo_branch명>

> -f : force의 약어 <br/>
> origin: 원격 repo의 main branch



---
<br/>


## 👉 **Pull**
 local repository와 비교하여 병합, local repository에 저장( add )까지 수행
> git pull = git fetch + git merge 
- **git fetch**: local에 연결된 remote repository의 브랜치 목록과 그 파일 내용을 최신으로 업데이트 하는 명령어
(local과 remote의 싱크를 맞추는 새로고침 역할)

- **git merge**는 두 개의 branch를 병합하는 명령어

협업 과정에서 **프로젝트의 최신 코드를 local로 가져오는 역할**로 많이 사용

     git pull <원격repo_branch명> <로컬repo_branch명>

<br/>

**rebase**: 병합하는 명령어 중 하나<br/>
Git에서는 최신 코드로 업데이트 할 때 rebase를 사용할 것을 권장<br/>
**rebase 명령어**는 merge 명령어보다 **히스토리( log )가 깔끔**해진다
> **git pull --rebase** = git fetch + git rebase

     git pull --rebase <원격repo_branch명> <로컬repo_branch명>


<br/>


## 👉 **Clone**
프로젝트 처음, 중간에 git이 꼬여 초기화 시 등 초기 설정 시 사용<br/>
원격repo에 연결하여 작업 내역 모두 로컬repo에 가져옴. <br/><br/>

### ● 원격repo clone

     git clone { 원격 저장소 URL }

<br/>

### ● 특정 브랜치를 clone

     git clone -b { 브랜치명 } { 원격 저장소 URL }


---
<br/><br/>

## 👉 **remote(원격 repo) command** 

    로컬repo에 연결된 원격repo 확인: git remote -v

    로컬repo와 원격repo 연결: git remote add <branch명> <url> 
                              (url -> github 홈페이지 확인)

    로컬repo에서 원격repo 연결 제거: git remote remove <브랜치명?>
    (origin이라 표현하는 main은 뜻하는지 branch 전체를 뜻하는지 정확히 
    모르겠다...)

<br/><br/>

## 👉 **branch(브랜치) command**

    branch 조회: git branch

    branch 생성: git branch 브랜치명

    branch 이름 변경: git branch -m 기존명 변경명

    branch 삭제: git branch -d 브랜치명

    branch 전환: git checkout 브랜치명

    branch 병합: (main으로 checkout 후) git merge 브랜치명




clone과 merge의 차이)<br>
clone: 로컬-원격: 일치
pull: ... + merge

따라서 pull은 병합과정도 포함되어 있기 때문에 pull하기 전에 commit을 하지 않으면 충돌 발생 -> 덮어쓰기로 commit 삭제될 수 있다. 
=> 기존 작업에 대한 commit을 미리 해두고 pull  수행

---

<br/><br/>

주제) 김치로 만드는 요리 ( 김치찌개, 김치전, 김치볶음밥 )


프로젝트 진행)

    1. 각 요리마다 issue와 branch를 만든다.

    2. 각 branch마다 작업한 cummit을 issue 와 연동 시킨다.

    3. 각 branch를 main에 merge 시킨다.

