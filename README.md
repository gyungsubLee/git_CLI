# git_복습

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

<br/><br/>

학습내용)

    issue는 branch 관계없이 #으로 tag가능

    sub branch의 cummit 내역은 main branch에 merge하지 않으면 반영이 안됨.

    시작 때 README issue도 만들어 정리 -> 깔끔함?, 굳이 필요없을 것 같다

    cummit을 기능 단위로 쪼개자. cummit message 규칙 정하고 쓰자.

<br/><br/>

# git 명령어)

## **프로젝트에 git 설정: git initailize(초기화)

    git init

<br>

# **git commit하기**

변경된 파일 및 add 상태 확인  
    
    git status

변경 작업 add

    git add [파일이름]  -> add 할 파일을 정한다(staging), 전체선택(.)

add한 파일 commit

    git commit -m "메세지 입력"

<br/>

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

## **commit 메세지 수정**
-로컬repo commit 메세지 수정

    git commit --amend -m <수정메세지>

-원격repo commit 메세지 수정

    git push --force <branch명>

로컬 변경 내용 강제 push -> 개인 프로젝트만... 협업시에는 망함


## **commit 삭제**
-로컬repo commit 삭제

    git reset <옵션><돌아가고싶은 커밋 id>

옵션: 3가지

    --hard: 돌아가려는지점 이후 모든 내용 삭제.

    --soft: 돌아가려는 지점으로 돌아가지만 add 내용은 남아 있는다.

    --mixed: default 값이다. 돌아가려는 지점으로 돌아가지만 인덱스는 초기화 된다. 

원격repo에 덮어 씌우기

    git push -f origin master





---

<br/><br/>

## **PUSH**

    push: git push <원격저장소명> <브랜치명>
(git clone을 통해 가져왔다면  기본 원격저장소 이름은 origin이다.)

<br>

인자생략1)

    git push -u orign my-feature

-u : 옵션을 사용하여 최최의 한 번만 저장소명과 브랜치 명을 입력하고 그 이후에 모든 인자 생략 가능
    
    ex)
    git commit -m "change 1"
    git push

인자생략2)

    git config --global push.defalut current

여러 브랜치를 넘나 들면서 작업하는 경우 최초의 한번 인자는 넘기는 것도 귀찮다.
대부분의 경우 로컬repo와 원격repo가 동일한 branch 이름을 사용하기 때문에 현재 branch를 기준으로 git push 명령어가 작동되가 설정한다. 
<br><br>
**push.default**,  **current**로 가능하다

    git push

코드 변경이력 덮어쓰기)

    git push -f origin my-feature



<br>

    ** commit 취소
    로컬 commit 취소: git reset HEAD 파일명(없으면 add한 cummit 전체취소)
    원격 commit 취소: 

    정리)keyword
    버전관리pull, clone

    완료)git초기화, commit(커밋), commit내역(history), push


---

<br/><br/>

## **remote(원격 repo)** 

    로컬repo에 연결된 원격repo 확인: git remote -v

    로컬repo와 원격repo 연결: git remote add <branch명> <url> 
                              (url -> github 홈페이지 확인)

    로컬repo에서 원격repo 연결 제거: git remote remove <브랜치명?>
    (origin이라 표현하는 main은 뜻하는지 branch 전체를 뜻하는지 정확히 
    모르겠다...)

<br/><br/>

## **branch(브랜치)**

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

