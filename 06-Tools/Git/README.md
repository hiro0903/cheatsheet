讓git log比較好看(修改完config後, 新增alias: ```git lg```
```
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --"
```

### reference:
- [直接git config版](http://www.ityuedu.com/article/658875654/)
- [進config 編輯版](https://github.com/hunter99/WorkWithUbuntu12.04LTS/blob/master/Precise.mediawiki)