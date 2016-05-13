# stephenzhao.github.io

#Usage

##install

``` 
$ npm install -g hexo 
$ hexo init
$ hexo g
$ hexo s

```
浏览器localhost:4000

##复制主题：

```
git clone https://github.com/cnfeat/cnfeat.git themes/jacman
```

##启用cnfeat的主题

修改Hexo目录下的config.yml配置文件中的theme属性，将其设置为jacman。同时请设置stylus属性中的compress值为true。

*theme: jacman*

##更新主题
```
$ cd themes/jacman
$ git pull
```

##本地查看调试
```
$ hexo g #生成
$ hexo s #启动本地服务，进行文章预览调试
```

或者直接作用组合命令
```
$ hexo d -g
```

#将独立域名与GitHub Pages的空间绑定
##GitHub Pages的设置
方法一：在Repository的根目录下面，新建一个名为CNAME的文本文件，里面写入你要绑定的域名，比如cnfeat.com。

方法二：到我的github仓库，点击右下角的「Download ZIP」，下载源文件，解压，找到CNAME文件，用记事本打开，将cnfeat.com修改成你的域名，放进Hexo\source目录下，用hexo命令提交上去。
```
$ hexo d -g
```

#Hexo命令
常用命令：
```
hexo new "postName" #新建文章
hexo new page "pageName" #新建页面
hexo generate #生成静态页面至public目录
hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
hexo deploy #将.deploy目录部署到GitHub
```
常用复合命令：
```
hexo d -g #生成加部署
hexo s -g #预览加部署
```
简写：
```
hexo n == hexo new
hexo g == hexo generate
hexo s == hexo server
hexo d == hexo deploy
```
安装插件
添加sitemap和feed插件
```
$ npm install hexo-generator-sitemap
$ npm install hexo-generator-feed
```
修改_config.yml，增加以下内容
```
#Extensions
Plugins:
- hexo-generator-feed
- hexo-generator-sitemap

#Feed Atom
feed:
  type: atom
  path: atom.xml
  limit: 20

#sitemap
sitemap:
  path: sitemap.xml
```

##Hexo上传README文件
Github的版本库通常建议同时附上README.md说明文件，但是hexo默认情况下会把所有md文件解析成html文件，所以即使你在线生成了README.md，它也会在你下一次部署时被删去。怎么解决呢？

在执行hexo deploy前把在本地写好的README.md文件复制到.deploy文件夹中，再去执行hexo deploy。

##404页面
GitHub Pages有提供制作404页面的指引：Custom 404 Pages。

直接在根目录下创建自己的404.html或者404.md就可以。但是自定义404页面仅对绑定顶级域名的项目才起作用，GitHub默认分配的二级域名是不起作用的，使用hexo server在本机调试也是不起作用的。

推荐使用腾讯公益404。



#页面布局结构
```
.
├── languages  #多语言
|   ├── default.yml#默认语言
|   └── zh-CN.yml  #中文语言
├── layout #布局，根目录下的*.ejs文件是对主页，分页，存档等的控制
|   ├── _partial   #局部的布局，此目录下的*.ejs是对头尾等局部的控制
|   └── _widget#小挂件的布局，页面下方小挂件的控制
├── source #源码
|   ├── css#css源码 
|   |   ├── _base  #*.styl基础css
|   |   ├── _partial   #*.styl局部css
|   |   ├── fonts  #字体
|   |   ├── images #图片
|   |   └── style.styl #*.styl引入需要的css源码
|   ├── fancybox   #fancybox效果源码
|   └── js #javascript源代码
├── _config.yml#主题配置文件
└── README.md  #用GitHub的都知道
```