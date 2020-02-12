git subrepo push --allすると以下のエラーが出る時がある。

/usr/bin/git-subrepo/lib/git-subrepo: line 612: cd: .git/tmp/subrepo/packages/xxxx: No such file or directory

よくわからないが、上記のエラーが出たら個別のディレクトリを指定してsubrepo pushすると治る。
git subrepo push packages/xxxx
