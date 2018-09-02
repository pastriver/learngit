# Note For  MarkDown and Git Learning

## Markdown简介

> Markdown 是一种轻量级标记语言,它允许人们使用易读易写的纯文本格式编写文档,然后转换成格式丰富的HTML页面.    —— [维基百科](https://zh.wikipedia.org/wiki/Markdown)

正如您在阅读的这份文档,它使用简单的符号标识不同的标题,将某些文字标记为**粗体**或者*斜体*,创建一个[链接](http://www.example.com)或一个脚注[^demo].下面列举了几个高级功能,更多语法请按`Ctrl + /`查看帮助.

### 代码块
``` python
@requires_authorization
def somefunc(param1='', param2=0):
    '''A docstring'''
    if param1 > param2: # interesting
        print 'Greater'
    return (param2 - param1 + 1) or None
class SomeClass:
    pass
>>> message = '''interpreter
... prompt'''
```
### LaTeX 公式

可以创建行内公式,例如 $\Gamma(n) = (n-1)!\quad\forall n\in\mathbb N$.或者块级公式:

$$	x = \dfrac{-b \pm \sqrt{b^2 - 4ac}}{2a} $$

### 表格
| Item      |    Value | Qty  |
| :-------- | --------:| :--: |
| Computer  | 1600 USD |  5   |
| Phone     |   12 USD |  12  |
| Pipe      |    1 USD | 234  |

### 流程图
```flow
st=>start: Start
e=>end
op=>operation: My Operation
cond=>condition: Yes or No?

st->op->cond
cond(yes)->e
cond(no)->op
```

以及时序图:

```sequence
Alice->Bob: Hello Bob, how are you?
Note right of Bob: Bob thinks
Bob-->Alice: I am good thanks!
```

> **提示:**想了解更多,请查看**流程图**[语法][3]以及**时序图**[语法][4].

### 复选框

使用 `- [ ]` 和 `- [x]` 语法可以创建复选框,实现 todo-list 等功能.例如:

- [x] 已完成事项
- [ ] 待办事项1
- [ ] 待办事项2

## Git简介
> Git(读音为/gɪt/.)是一个开源的分布式版本控制系统,可以有效、高速的处理从很小到非常大的项目版本管理.Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件.本文的Git学习来自于廖雪峰的Git教程.—— [廖雪峰Git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)

### Git安装
> - 在Linux上安装Git
首先,你可以试着输入git,看看系统有没有安装Git:

```
$ git
The program 'git' is currently not installed. You can install it by typing:
sudo apt-get install git
```
> 像上面的命令,有很多Linux会友好地告诉你Git没有安装,还会告诉你如何安装Git,如果你碰巧用Debian或Ubuntu Linux,通过一条`sudo apt-get install git`就可以直接完成Git的安装,非常简单.  
老一点的Debian或Ubuntu Linux,要把命令改为`sudo apt-get install git-core`,因为以前有个软件也叫GIT（GNU Interactive Tools）,结果Git就只能叫git-core了.由于Git名气实在太大,后来就把GNU Interactive Tools改成gnuit,git-core正式改为git.  
如果是其他Linux版本,可以直接通过源码安装.先从Git官网下载源码,然后解压,依次输入:`./config,make,sudo make install`这几个命令安装就好了.

- 在Mac OS X上安装Git
> 如果你正在使用Mac做开发,有两种安装Git的方法.  
一是安装homebrew,然后通过homebrew安装Git,具体方法请参考homebrew的文档:http://brew.sh/.  
第二种方法更简单,也是推荐的方法,就是直接从AppStore安装Xcode,Xcode集成了Git,不过默认没有安装,你需要运行Xcode,选择菜单`Xcode->Preferences`,在弹出窗口中找到`Downloads`,选择`Command Line Tools`,点`Install`就可以完成安装了.

- Windows上安装
> 在Windows上使用Git,可以从Git官网直接下载安装程序,（网速慢的同学请移步国内镜像）,然后按默认选项安装即可.安装完成后,在开始菜单里找到`Git->Git Bash`,蹦出一个类似命令行窗口的东西,就说明Git安装成功！  
安装完成后,还需要最后一步设置,在命令行输入:  
```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```
> 因为Git是分布式版本控制系统,所以,每个机器都必须自报家门:你的名字和Email地址.你也许会担心,如果有人故意冒充别人怎么办？这个不必担心,首先我们相信大家都是善良无知的群众,其次,真的有冒充的也是有办法可查的.  
注意`git config`命令的`--global`参数,用了这个参数,表示你这台机器上所有的Git仓库都会使用这个配置,当然也可以对某个仓库指定不同的用户名和Email地址.

### 创建版本库  

> 初始化一个Git仓库,使用git init命令.添加文件到Git仓库,分两步:
> - 使用命令git add <file>,注意,可反复多次使用,添加多个文件;
> - 使用命令git commit -m <message>,完成.  

### 时光穿梭机器   
> - 要随时掌握工作区的状态,使用`git status`命令.
> - 如果`git status`告诉你有文件被修改过,用`git diff`可以查看修改内容.

### 版本回退
> - HEAD指向的版本就是当前版本,因此,Git允许我们在版本的历史之间穿梭,使用命令`git reset --hard commit_id`.
> - 穿梭前,用`git log`可以查看提交历史,以便确定要回退到哪个版本.  
> - 要重返未来,用`git reflog`查看命令历史,以便确定要回到未来的哪个版本. 

### 了解工作区和缓存的概念  
-  [工作区和缓存的概念](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013745374151782eb658c5a5ca454eaa451661275886c6000)  

### 撤销修改
- 场景1：当你改乱了工作区某个文件的内容,想直接丢弃工作区的修改时,用命令`git checkout -- file`.  
- 场景2：当你不但改乱了工作区某个文件的内容,还添加到了暂存区时,想丢弃修改,分两步,第一步用命令`git reset HEAD <file>`,就回到了场景1,第二步按场景1操作.  
- 场景3：已经提交了不合适的修改到版本库时,想要撤销本次提交,参考版本回退一节,不过前提是没有推送到远程库.  

### 删除文件
>   命令`git rm`用于删除一个文件.如果一个文件已经被提交到版本库,那么你永远不用担心误删,但是要小心,你只能恢复文件到最新版本,你会丢失最近一次提交后你修改的内容.  

### 远程仓库   
1. 创建SSH key：
```
$ ssh-keygen -t rsa -C "youremail@example.com"
```
> 你需要把邮件地址换成你自己的邮件地址,然后一路回车,使用默认值即可,由于这个Key也不是用于军事目的,所以也无需设置密码.如果一切顺利的话,可以在用户主目录里找到.ssh目录,里面有`id_rsa和id_rsa.pub`两个文件,这两个就是`SSH Key`的秘钥对,`id_rsa`是私钥,不能泄露出去,`id_rsa.pub`是公钥,可以放心地告诉任何人.  
2. 登陆GitHub:
> 打开`Account settings`,`SSH Keys`页面,然后,点`Add SSH Key`,填上任意Title,在Key文本框里粘贴`id_rsa.pub`文件的内容.  

#### 添加远程仓库
> 要关联一个远程库,使用命令`git remote add origin git@server-name:path/repo-name.git`;  
关联后,使用命令`git push -u origin master`第一次推送`master`分支的所有内容;  
此后,每次本地提交后,只要有必要,就可以使用命令`git push origin master`推送最新修改;

#### 从远程仓库克隆 
```
$ git clone git@github.com:email/rep.git
```
#### 分支管理
>查看分支：`git branch`  
创建分支：`git branch <name>`
切换分支：`git checkout <name>`  
创建+切换分支：`git checkout -b <name>`  
合并某分支到当前分支：`git merge <name>`  
删除分支：`git branch -d <name>`  

#### 解决冲突  
>当Git无法自动合并分支时,就必须首先解决冲突.解决冲突后,再提交,合并完成.
解决冲突就是把Git合并失败的文件手动编辑为我们希望的内容,再提交.  
用`git log --graph`命令可以看到分支合并图.