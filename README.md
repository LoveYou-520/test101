## Git 配置
Git 提供了一个叫做 git config 的工具，专门用来配置或读取相应的工作环境变量。
这些环境变量，决定了 Git 在各个环节的具体工作方式和行为。这些变量可以存放在以下三个不同的地方：
  - /etc/gitconfig 文件：系统中对所有用户都普遍适用的配置。若使用 git config 时用 --system 选项，读写的就是这个文件。
  - ~/.gitconfig 文件：用户目录下的配置文件只适用于该用户。若使用 git config 时用 --global 选项，读写的就是这个文件。
  - 当前项目的 Git 目录中的配置文件（也就是工作目录中的 .git/config 文件）：这里的配置仅仅针对当前项目有效。每一个级别的配置都会覆盖上层的相同配置，所以 .git/config 里的配置会覆盖 /etc/gitconfig 中的同名变量。
  
在 Windows 系统上，Git 会找寻用户主目录下的 .gitconfig 文件。主目录即 $HOME 变量指定的目录，一般都是 C:\Documents and Settings\$USER。
此外，Git 还会尝试找寻 /etc/gitconfig 文件，只不过看当初 Git 

### 用户信息
配置个人的用户名称和电子邮件地址：

    ``git config --global user.name "runoob"`` 
    ``git config --global user.email test@runoob.com``
    
如果用了 --global 选项，那么更改的配置文件就是位于你用户主目录下的那个，以后你所有的项目都会默认使用这里配置的用户信息。        
如果要在某个特定的项目中使用其他名字或者电邮，只要去掉 --global 选项重新配置即可，新的设定保存在当前项目的 .git/config 文件里。

### 查看配置信息
要检查已有的配置信息，可以使用 git config --list 命令：
- ``git config --list``

有时候会看到重复的变量名，那就说明它们来自不同的配置文件（比如 /etc/gitconfig 和 ~/.gitconfig），不过最终 Git 实际采用的是最后一个。

## Git 创建仓库
#### git init
Git 使用 git init 命令来初始化一个 Git 仓库，Git 的很多命令都需要在 Git 的仓库中运行，所以 git init 是使用 Git 的第一个命令。<br>
行完成 git init 命令后，Git 仓库会生成一个 .git 目录，该目录包含了资源的所有元数据，其他的项目目录保持不变
#### 使用方法
   - `git init`
   
使用我们指定目录作为Git仓库。<br>
   -  `git init newrepo`
   
先用 git add 命令告诉 Git 开始对这些文件进行跟踪，然后提交<br>
- `git add *.c`<br> 
    + 所有.c 结尾的将该文件添加到缓存
- `git add ./`<br>
    + 在该项目下的所有文件添加到缓存
- `git add commit -m '初始化项目版本'`
    + 提交缓存区内容添加到仓库中
#### 可以一次性把我们修改的代码放到文章里（版本库）
 >`git commit -all -m '初始化项目版本'`<br>
 >> --all 表示把所有修改的文件提交到版本库
#### 查看当前的状态 
> 可以用来查看当前代码有没胡被放到仓储中去
>>命令：<br>
>>> `git status`<br>
    
#### git clone
使用 git clone 拷贝一个 Git 仓库到本地，让自己能够查看该项目，或者进行修改。
   > `git clone [url]` __[url] 为你想要复制的项目__

例如我们克隆 Github 上的项目
> `git clone git@github.com:schacon/simplegit.git`

#### 查看日志
> `git log` __查看历史提交的日志__ <br>
> `git log --online` __可以看到简洁版的日志__

#### 回退到指定的版本
- `git reset --hard Head~0` *****表示回退到上一次代码提交时的状态*****
- `git reset --hard Head~1` ____表示回退到上上次代码提交时的状态____
- `git reset --hard [版本号]` __可以通过版本号的回退到某一冷饮提交时的状态, 也可以回退到已经回退的版本号__
- `git reflog` __可以看到每一次切换版 本的记录:可以看到所有提交的版本__
________________________________________

### 分支 
> 默认是有一个主分支master

#### 创建分支
- `git branch dev` *创建了一个dev分支*
    + 在刚创建时dev分支里的东西和master分支里的东西是一样的 

#### 切换分支
- `git checkout dev` *切换到指定的分支,这里的切换到名为dev的分支*
- `git branch` *可以查看当前有哪些分支*

#### 合并分支
- `git merge dev` *合并分支内容,把当前分支与指定的分支(dev),进行合并*
    + 当前分支指的是`git branch`命令输出的前面有*号的分支
- 合并时如果有冲突,需要手动去处理,处理后还需要再提交一次. 

#### 删除分支
- `git branch -d (branchname)`

### GitHub
- https://github.com
- 还是git,只是一个网站
- 只不过这个网站提供了允许别通过git上传代码的功能

#### 提交代码到 github (当作git服务器来用)
- `git push [地址] master`
 + 示例 : `git push `
 + 会把当前分支的内容上传到远程的master分支上
 
 - `git pull [地址] master`
 + 示例 ： `git pull https://github.com/LoveYou-520/test100.git master`
 + 会把远程分支的数据得到 :(*注意本地-要初始一个仓库*)
 
 - `git clone [地址]`
 +会得到远程仓储相同的数据，如果多次执行会覆盖本地内容。
 
 #### 流行框架 
 ##### ssh 方式上传代码
 - 公钥 私钥 ，两者之间是有关联的
 - 生成公钥，和私钥 
    + 