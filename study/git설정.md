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
