# LF will be replaced by CRLF 에러
[해결] (https://dabo-dev.tistory.com/13)

[해결2] https://blog.jaeyoon.io/2018/01/git-crlf.html

# Git repo 커밋을 유지하면서 병합

[해결]https://mansoo-sw.blogspot.com/2017/08/git-repository-merge.html

[해결2]https://hanco.tistory.com/9
* 난 해결2 링크로 해결했다.


# commit으로 merge하지 않고 넘어가는 방법
> 내가 push :개인 branch에 push를 함 -> PR 요청 -> mrege -> 다른 팀원이 master branch에서 pull


> 팀원이 push :PR요청 확인 -> merge -> (작업중인 내용이 있다면 stash) ->master branch로 이동하여 pull -> 개인 branch로 이동 -> 개인 branch에 master merge -> stash apply

# commit 없이 merge 하는 법
1. git stash (임시 보관함에 저장)
2. git checkout main (메인으로 넘어가서)
3. git pull origin main (풀받고)
4. git checkout hoon(작업 브랜치로 와서)
5. git merge main (메인에서 받은 내용을 합쳐준다)
6. git stash apply (보관함에서 가져온다)

# 디렉토리 화살표 표시 해결
https://zzang9ha.tistory.com/346

# reset 과 revert의 차이

+ reset은 과거로 돌아가면서 돌아가는 시점이 최신인 상태
+ revert는 과거로 돌아가되 돌아가기 전의 시점은 남겨두고 돌아가는 것
+ 여담으로 이 차이를 쉽게 설명하기위해 문득 든 생각은 어벤져스에서 5년전의 과거로 돌아가는 시점을 생각해보면 과거의 시점으로 돌아가는 영웅들은 현재의 기억을 가지고 과거로 가므로 revert이고 과거로 돌아가서 만난 그 시점의 사람들은 reset의 상태라고 생각해봤다. 

# git reflog

+ git reset --hard 를 사용하더라도 돌아갈 수 있다.
+ git reflog를 치면 모든 로그가 뜨고 돌아갈 시점으로 git reset --hard 로그코드 를 사용하면 돌아갈 수 있다.

# ignore
https://coding-groot.tistory.com/59

# 좋은 커밋 메세지를 위한 영어 사전

https://blog.ull.im/engineering/2019/03/10/logs-on-git.html