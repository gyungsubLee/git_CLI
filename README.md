# git_test@@
 
 git - 복습)

keyword)
 cummit, push, pull, issue, branch, merge


주제) 김치로 만드는 요리 ( 김치찌개, 김치전, 김치볶음밥 )


진행과정)

    1. 각 요리마다 issue와 branch를 만든다.

    2. 각 branch마다 작업한 cummit을 issue 와 연동 시킨다.

    3. 각 branch를 main에 merge 시킨다.


학습내용)

    issue는 branch 관계없이 #으로 tag가능

    sub branch의 cummit 내역은 main branch에 merge하지 않으면 반영이 안됨.

    시작 때 README issue도 만들어 정리 -> 깔끔함?, 굳이 필요없을 것 같다

    cummit을 기능 단위로 쪼개자. cummit message 규칙 정하고 쓰자.


git 명령어)

    

    branch 변경: git checkout 브랜치명

    branch 병합: (main으로 checkout 후) git merge 브랜치명



    로컬 cummit 취소: git reset HEAD 파일명(없으면 add한 cummit 전체취소)
