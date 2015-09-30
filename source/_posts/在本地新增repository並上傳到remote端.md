title: 在本地新增 repository 並上傳到 remote 端
date: 2015-09-30 23:04:51
tags: [github]
---
0. 假設在 local 端完成一個專案，資料夾名稱叫 `typeScript-OOP-practices`
```{console}
$ mkdir -p ~/javascript/typeScript-OOP-practices
$ cd ~/javascript/typeScript-OOP-practices
$ touch test.js
```

1. 先到自己的 github上 創一個 repository (假設也叫 `typeScript-OOP-practices`)
![](/img/git/1.png)

2. 回到 local端的 `typeScript-OOP-practices` 資料夾，並將此資料夾初始化為 git 的 repository
```{shell}
$ cd ~/javascript/typeScript-OOP-practices
$ git init
```

3. 將資料夾內的所有檔案進行追蹤
```{bash}
$ git add -A
```

4. 進行第一次 commit
```{bash}
$ git commit -m 'my first commit lol'
```
5. 接著再回到 github 上，將先前創好的 repository 位址複製起來
![](/img/git/2.png)

6. 新增一個 remote repository
```{bash}
$ git remote add origin https://github.com/joyfeel/typeScript-OOP-practices.git
$ git remote -v
```

7. 輸入帳號密碼後，將 local repository 推送到 remote repository，就可上 github 看看是否成功
```{bash}
$ git push origin master
```

Reference: [Adding an existing project to GitHub using the command line](https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/)