##

```
git config --global pull.ff true
git config --global pull.rebase true

git pull 명령어 입력시 기존에는 pull. ff 항목에 false로 처리되어 있어서 항상 merge 커밋이 만들어졌었는데
pull.ff를 true로 생성하면 가능하면 fast-forward 방식으로 병합하게 됩니다.
pull.ff는 true가 기본값이므로 삭제해도 되지만 명시적으로 true로 설정해 놓는 것이 좋습니다.

앞서 수업 시간에 이 부분이 제대로 동작하지 않은 이유는 rebase까지 false로 처리했기때문입니다.
pull.rebase 는 true로 지정하면 pull 의 경우 git fetch와 git rebase를 수행하기때문에
충돌이 없다면 병합 커밋은 생성되지 않습니다.
```

#리셋
git reset ORIG_HEAD : 해당 git 을 되돌리는 것
git reset <커밋해시>

git reset --soft HEAD~ :  
커밋만 되돌리고 스테이징된 파일과 워킹 디렉토리는 그대로 둔다
커밋만 취소됨, git add 상태는 유지됨, 코드 내용 그대로

git reset --mixed HEAD~
: 커밋과 스테이징만 되돌리고, 워킹 디렉토리는 그래도 둔다
커밋 취소됨, stage 취소됨, 파일 내용은 살아 있음
따로 설정하지 않으면 mixed로 됨
git reset HEAD~ == git reset --mixed HEAD~

커밋 + 스테이징 + 파일 내용까지 전부 되돌린다.
커밋 사라짐, stage 삭제, 로컬 파일 변경까지 삭제

git reset --hard HEAD~

#git restore

1. 작업 디렉토리에서 코드를 되돌릴 때
   git restore file.js
   수정한 파일을 마지막 커밋 상태로 되돌림

2. 스테이지를 취소할 때 (git add 취소)
   git restore --staged file.js

git reset : 커밋을 묶어야하거나 오타가 났을 때 사용 가능
--soft : 변경내용 유지 + 스테이징 영역으로 이동
--mixed: 변경내용 유지 + wd 영역으로 이동
-- hard : 변경내용 삭제 + 커밋도 삭제

사용 방법
git reset --hard HEAD~
두단계
git reset --hard HEAD~2

reset전 되돌아가기
git reset ORIG_HEAD

삭제한 해쉬코드 찾는법
git reflog

\*브랜치 변경
git switch -c ui

\*파일의 변경 내용을 임시로 숨겨둠
git stash

\*브랜치 변경
git switch main

\*해당 메세지가 떠야지 브랜치 이동할 수 있음
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

\*브랜치 이동
git switch ui

\*숨겨놓은 목록 조회
git stash list
git stash show

\*숨겨놓은 변경사항을 다시 브랜치로 가져옴
git stash apply 꺼내고 복사  
git stash pop 꺼냄과 동시에 삭제

\*숨겨놓은 이력 삭제
git stash drop

\*git push
git add index.html style.css
git commit -m "하이퍼링크 스타일링"
git push

#git 보는거
git remote -v

#과제 받기
git pull origin main

#과제 올리기
git push -u mine main

#과제
git push -u mine main
