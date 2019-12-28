这里是hexo的源文件，更换主机时可以下载本分支。
然后执行
```
git checkout source
npm install hexo-cli -g
npm install
```
即可重新安装好hexo环境。

发布文章流程
```
hexo g -d # 生成文章，并将网页更新发至master分支
git add .
git commit
git push # 将源文件更新至source分支
```

新增文章路程
```
# 新创建一篇文章。其实直接在对应文件夹下面创建一个新文件也行，但是这样得自己写开头的格式。
hexo n <title>
```