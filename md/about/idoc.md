#### 写在前面
1. github仓库的默认分支是master
2. gh-pages分支默认是不存在的，gh-pages分支上的内容可以显示成网站的样子
3. 这个地方就是gh-pages分支所生成的静态网站,  http://koreabright.github.io/<所要显示成网站的项目> 

#### idoc的使用方法 (如何在本地构建gh-pages分支的内容, 也就是网页的内容)
1. 任意目录下新建test文件夹，并进入test文件夹 如：mkdir test && cd test。
2. 在你在的目录下面建立 md 文件夹专门放你的所有 md 文件。
3. 导航菜单是根据 md 里面的文件目录结构生成 导航菜单。
4. 在 test 文件夹根目录初始化运行 idoc init 命令，自动生成 package.json 文件。
5. 生成静态页面，运行 idoc build 命令。
6. 运行 idoc server 预览生成的静态页面。默认预览地址为 http://localhost:1987/。
7. 这个时候你可以将生成的文件上传至 github 的 gh-pages 分支中，外网预览。     

#### 如何在github上面创建gh-pages分支
1. 在test目录中执行，git init, 使这个目录变成一个git仓库
2. 创建gh-pages分支, 执行 git checkout --orphan gh-pages
3. 将代码加到缓存区， 执行 git add . && git commit -m '说明文字'
4. 关联仓库，执行 git remote add origin git@github.com:KoreaBright/KoreaBright.github.io.git(自己的仓库)
5. git push -u origin gh-pages