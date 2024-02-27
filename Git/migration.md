### svn을 git으로 옮기는 방법

    git svn init [svn 주소] -T trunk -b branches -t tags

    git svn fetch

    git branch -a

    git remote add origin [git 주소]

    git remote -v

    git push origin master

    git branch [remote brach] [옮길 svn brach]
