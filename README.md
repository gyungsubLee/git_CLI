# git_test@@
 
 git - 복습)

keyword)
 git init, Tracking, cummit, push, pull, issue, branch, merge


git 프로젝트 사용)

    1. 프로젝트에 git 연결하기 - 프로젝트 폴더 생성 및 git initailize(초기화)




주제) 김치로 만드는 요리 ( 김치찌개, 김치전, 김치볶음밥 )


프로젝트 진행)

    1. 각 요리마다 issue와 branch를 만든다.

    2. 각 branch마다 작업한 cummit을 issue 와 연동 시킨다.

    3. 각 branch를 main에 merge 시킨다.


학습내용)

    issue는 branch 관계없이 #으로 tag가능

    sub branch의 cummit 내역은 main branch에 merge하지 않으면 반영이 안됨.

    시작 때 README issue도 만들어 정리 -> 깔끔함?, 굳이 필요없을 것 같다

    cummit을 기능 단위로 쪼개자. cummit message 규칙 정하고 쓰자.


# git 명령어)

## **로컬repo** 

    git initailize(초기화): git init

    변경된 파일 및 add 상태 확인 : git status

    변경 작업 add: git add [파일이름] 
                              -> add 할 파일을 정한다(staging), 전체선택(.)

    add한 파일 commit: git commit -m "메세지 입력"

    commit 추적: git log (나가기:Q)

    git branch 이름변경(Master -> Main): git branch -M main

    commit들 push: git push -u origin main

---

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

## **remote(원격 repo)** 

    로컬repo에 연결된 원격repo 확인: git remote -v

    로컬repo와 원격repo 연결: git remote add <branch명> <url> 
                              (url -> github 홈페이지 확인)

    로컬repo에서 원격repo 연결 제거: git remote remove <브랜치명?>
    (origin이라 표현하는 main은 뜻하는지 branch 전체를 뜻하는지 정확히 
    모르겠다...)

<br/>

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



