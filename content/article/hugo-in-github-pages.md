---
title: "Hugo in Github Pages"
date: 2018-01-05T10:35:27+08:00

categories: ['Code', 'Tutorials']
tags: ['Hugo', 'Tutorials']
author: "LuoYong"
---
这是第一篇自己的博客,讲述使用`github pages`和`hugo`创建自己的个人博客的教程,说实话,经历两天的摸索,终于能够使用简单的操作,将自己写的`markdown`上传到博客上.
这里讲一下事情的原委:
之前在阿里云上面注册了一个域名[bootloader.cn](http://bootloader.cn),但是我却不知道有什么用,2018年伊始,郭神的博客推送了一片免费创建个人博客网站的文章,我觉得是时候对自我进行一个投资了(之前看书的时候就有人建议过,作为程序员,要树立自己的品牌形象,让更多的人了解你),当然,在技术行业,也要具有分享精神.当我搭建完自己的博客后,我决定将我的搭建过程分享出来,给大家参考.

1. 首先,你需要一个github的账号.账号肯定是在[github.com](https://github.com/)官网上注册咯.但是我相信,每一个技术人员都有一个自己的github账号.(注册流程我就不说了)

2. 在自己github上`new repository`,可以是一个项目比如`project`,也可以是`<UerName>.github.io`其中`<UerName>`要一起替换掉自己的`github`名称.当你创建`<UerName>.github.io`的一个`repository`的时候,只需要在`<UerName>.github.io`根目录下面放上一个`index.html`,就可以通过`htps://<UerName>.github.io`来进行访问了;

3. 如果你想最简单的创建自己的博客网站,那么`fork`一下[jekyll- now](https://github.com/barryclark/jekyll-now),然后Settings-->Repository name 改为`<UerName>.github.io`-->RENAME;Settings-->GitHub Pages-->Source-->master branch;Code-->_config.yml-->Edit This File;按照需求修改,现在你就可以通过`htps://<UerName>.github.io`访问你的博客了,当然你后续的要上传的文章,需要写成`.md`(markdown)的文件上传到`_posts`文件夹下面github会自动帮你生成.本文是Hugo的文章,所以这里就简单的介绍了一下jekyll
4. 安装[Hugo](https://gohugo.io/getting-started/installing), 英文版的教程,看着头大,还好有google翻译,整个流程是:新建Hugo的文件夹(在你想要放置hugo的任意位置),在Hugo文件夹下面新建bin和Seits文件夹,下载对应的[Hugo发行版](https://github.com/gohugoio/hugo/releases),将文件解压到bin文件夹下面,将可执行文件更名为hugo.exe,设置环境变量Path添加路径指向到bin文件夹,打开控制台,输入`hugo help`,显示
```
hugo is the main command, used to build your Hugo site.

Hugo is a Fast and Flexible Static Site Generator
built with love by spf13 and friends in Go.

Complete documentation is available at https://gohugo.io/.
```
说明hugo安装成功了,如果失败,请参照[Hugo安装文档](https://gohugo.io/getting-started/installing)

5. 安装[Git](https://git-scm.com/downloads),我是用的windows系统,并且下载的是`Git for Windows Portable（“thumbdrive edition”）`版本,解压到你想要的路径,然后配置环境变量中Path添加路径指向到Git安装路径的bin文件夹,打开控制台,输入git,如果出现
```
usage: git [--version] [--help] [-C <path>] [-c name=value]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone      Clone a repository into a new directory
   init       Create an empty Git repository or reinitialize an existing one

work on the current change (see also: git help everyday)
   add        Add file contents to the index
   mv         Move or rename a file, a directory, or a symlink
   reset      Reset current HEAD to the specified state
   rm         Remove files from the working tree and from the index

examine the history and state (see also: git help revisions)
   bisect     Use binary search to find the commit that introduced a bug
   grep       Print lines matching a pattern
   log        Show commit logs
   show       Show various types of objects
   status     Show the working tree status

grow, mark and tweak your common history
   branch     List, create, or delete branches
   checkout   Switch branches or restore working tree files
   commit     Record changes to the repository
   diff       Show changes between commits, commit and working tree, etc
   merge      Join two or more development histories together
   rebase     Reapply commits on top of another base tip
   tag        Create, list, delete or verify a tag object signed with GPG

collaborate (see also: git help workflows)
   fetch      Download objects and refs from another repository
   pull       Fetch from and integrate with another repository or a local branch
   push       Update remote refs along with associated objects

'git help -a' and 'git help -g' list available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.
```
说明git环境变量添加成功,然后输入`sh`控制台会切换到`Git-bash`的环境下面,然后输入`ssh`控制台会返回
```
usage: ssh [-46AaCfGgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-E log_file] [-e escape_char]
           [-F configfile] [-I pkcs11] [-i identity_file]
           [-J [user@]host[:port]] [-L address] [-l login_name] [-m mac_spec]
           [-O ctl_cmd] [-o option] [-p port] [-Q query_option] [-R address]
           [-S ctl_path] [-W host:port] [-w local_tun[:remote_tun]]
           [user@]hostname [command]
```
然后在输入指令`ssh-keygen -t rsa`
>什么意思呢？就是指定 rsa 算法生成密钥，接着连续三个回车键（不需要输入密码），然后就会生成两个文件 id_rsa 和 id_rsa.pub ，而 id_rsa 是密钥，id_rsa.pub 就是公钥。这两文件默认分别在如下目录里生成：Linux/Mac 系统 在 ~/.ssh 下，win系统在 /c/Documents and Settings/username/.ssh 下，都是隐藏文件，相信你们有办法查看的。
接下来要做的是把 id_rsa.pub 的内容添加到 GitHub 上，这样你本地的 id_rsa 密钥跟 GitHub 上的 id_rsa.pub 公钥进行配对，授权成功才可以提交代码。

6.回到你的github主页,点击你头像倒三角,点击`Settings`,进入 GitHub 上的设置页面，点击最左侧 `SSH and GPG keys`然后点击右上角的 New SSH key 按钮,需要做的只是在 Key 那栏把 id_rsa.pub 公钥文件里的内容复制粘贴进去就可以了，Title 那栏不需要填写，点击 Add SSH key 按钮就ok了。

这里提醒下，怎么查看 id_rsa.pub 文件的内容？
Linux/Mac 用户执行以下命令：
```
cd ~/.ssh
cat id_rsa.pub
```
Windows用户，设置显示隐藏文件，可以使用 文本编辑器 打开复制就行了。

SSH key 添加成功之后，输入 ssh -T git@github.com 进行测试，如果出现以下提示:
`Hi UesrName! You've successfully authenticated, but GitHub does not provide shell access.`
证明添加成功了。

7.切换bash路径到Hugo/Sites文件夹下面(注意:cmd用的`"\"`而bash用的`"/"`),然后输入指令`git clone git@github.com:<UserName>/<UserName>.github.io.git`或者`git clone git@github.com:<UserName>/<project>.git `(注意:请将上文中<UserName>和<project>连同`<>`一起替换掉),先在你可以看到Sites文件夹下面多了一个项目文件夹

8.打开控制台,切换到Sites文件夹下面,现在使用命令`hugo new site example.com`,其中`example.com`是刚才使用git从github上clone下来的文件夹名称,现在你可以看到`example.com`文件夹下面生成了很多文件夹比如:
```
C:\Hugo\Sites> cd example.com
C:\Hugo\Sites\example.com> dir
Directory of C:\hugo\sites\example.com

04/13/2015  10:44 PM    <DIR>          .
04/13/2015  10:44 PM    <DIR>          ..
04/13/2015  10:44 PM    <DIR>          archetypes
04/13/2015  10:44 PM                83 config.toml
04/13/2015  10:44 PM    <DIR>          content
04/13/2015  10:44 PM    <DIR>          data
04/13/2015  10:44 PM    <DIR>          layouts
04/13/2015  10:44 PM    <DIR>          static
               1 File(s)             83 bytes
               7 Dir(s)   6,273,331,200 bytes free
```
hugo的主要目录已经生成完成.

8.在hugo官网有很多主题可以选择,我选择了[bilberry-hugo-theme](https://github.com/Lednerb/bilberry-hugo-theme),打开控制台,切换到上文生成的`themes`文件夹,然后使用git命令`git clone https://github.com/Lednerb/bilberry-hugo-theme.git`然后,依次再在控制台输入`sh` ,`cp -r bilberry-hugo-theme/exampleSite/* ../` ,`cd ../` ,`hugo server -D`
控制台会输出
```
[K25lBuilding sites … [?25h
                   | EN
+------------------+----+
  Pages            |  3
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  0
  Processed images |  0
  Aliases          |  0
  Sitemaps         |  1
  Cleaned          |  0

Total in 74 ms
Watching for changes in F:\Hugo\Sites\bootloader.cn\{content,data,layouts,static}
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```
说明运行没有问题 `Ctrl+C`结束进程.
9.修改`config.toml`文件的内容,如果你github上的项目是`<UserName>.github.io.git`,则再config.homl里面添加`publishDir = "pubic"`如果是<project>形式,则添加`publishDir = "docs"`,修改完成之后,记得执行一次`hugo server`预览效果.接着执行`"hugo"`命令,在你的项目文件下面会根据publishDir生成对应的文件夹,以及资源文件.如果你选择的是<UserName>.github.io,你现在只需要将public文件夹下面的内容上传到github的master下面,然后Settings-->GitHub Pages-->Source-->master branch;你就可以通过`<UserName>.github.io.git`访问你的博客网站了,如果你选择的是`project`形式,按照上面的操作,通过`<UserName>.github.io.git/<project>`访问,但是这不是最优的选择.
10.你可以通过bash脚本,将项目上传到github上面
```
#!/bin/bash

echo -e "\033[0;32mDeploying updates to GitHub...\033[0m"

# Build the project.
hugo # if using a theme, replace with `hugo -t <YOURTHEME>`

# Go To Public folder
cd public
# Add changes to git.
git add .

# Commit changes.
msg="rebuilding site `date`"
if [ $# -eq 1 ]
  then msg="$1"
fi
git commit -m "$msg"

# Push source and build repos.
git push origin master

# Come Back up to the Project Root
cd ..
```
将上文代码复制下来,粘贴到文本文件,修改文件名为`deploy.sh`,将脚本放在你的<project>目录下,控制台切换到<project>目录,执行`sh` `./deploy.sh`,现在查看github上,是否已经将文件上传了(注意:如果提示输入github账户密码,则你输入github的账户密码,不要拒绝),如果上传成功,修改`Settings-->GitHub Pages-->Source-->master branch /docs folder`;通过`<UserName>.github.io.git/<project>`访问,你可能觉得这一步是多余的,但是,你已经将hugo编译文件和源文件分开放在github上面了.
11.最后一步,绑定域名.你可以在Hugo\Sites\project\static文件夹下新建文件`CNAME`用文本编辑器打开添加你的域名比如`bootloader.cn`,然后重新执行脚本.你也可以在github project的设置界面`Custom domain` 添加你的域名.或者直接在docs文件夹下面新建文件CNAME.最后,打开你的域名解析网站,将你的域名解析到`<UserName>.github.io`,你现在就可以用你的域名访问你的个人博客了;
