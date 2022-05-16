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


## git 명령어)
<br/>

### **로컬repo** 

    git initailize(초기화): git init


    로컬 cummit 취소: git reset HEAD 파일명(없으면 add한 cummit 전체취소)

    정리)keyword
    버전관리, commit(커밋), commit내역(history), push, pull, clone, tracking

    완료)git초기화


### **remote(원격 repo)** 

    로컬repo에 연결된 원격repo 확인: git remote -v

    로컬repo와 원격repo 연결: git remote add <branch명> <url> 
                              (url -> github 홈페이지 확인)

    로컬repo에서 원격repo 연결 제거: git remote remove <브랜치명?>
    (origin이라 표현하는 main은 뜻하는지 branch 전체를 뜻하는지 정확히 
    모르겠다...)

<br/>

### **branch(브랜치)**

    branch 조회: git branch

    branch 생성: git branch 브랜치명

    branch 이름 변경: git branch -m 기존명 변경명

    branch 삭제: git branch -d 브랜치명

    branch 전환: git checkout 브랜치명

    branch 병합: (main으로 checkout 후) git merge 브랜치명



