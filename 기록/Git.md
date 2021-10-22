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