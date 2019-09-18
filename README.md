# learning-how-to-use-git
#### 准备工作

* Git 使用 `git init` 命令来初始化一个 Git 仓库   使用当前目录作为Git仓库，我们只需使它初始化。 生成` .git `文件

* 使用以下命令生成 SSH Key：   `$ ssh-keygen -t rsa -C "youremail@example.com"`

* 成功的话会在 ~/ 下生成` .ssh` 文件夹，进去，打开` id_rsa.pub`，复制里面的 key，填入github中

* 为了验证是否成功，在git bash下输入： ` $ ssh -T git@github.com`
* 如果是第一次的会提示是否continue，输入yes就会看到：`You've successfully authenticated, but GitHub does not provide shell access` 。这就表示已成功连上github。

```git
$ mkdir runoob-git-test                     # 创建测试目录
$ cd runoob-git-test/                       # 进入测试目录
$ echo "# Git 测试" >> README.md     # 创建 README.md 文件并写入内容
$ ls                                        # 查看目录下的文件
	README
$ git init                                  # 初始化
$ git add README.md                         # 添加文件
$ git commit -m "添加 README.md 文件"        # 提交并备注信息
[master (root-commit) 0205aab] 添加 README.md 文件
 1 file changed, 1 insertion(+)
 create mode 100644 README.md

# 提交到 Github
$ git remote add origin git@github.com:tianqixin/runoob-git-test.git
$ git push -u origin master
```

#### 提交文件

* 第一步：使用命令 `git add readme.md`添加到暂存区里面去。

* 第二步：用命令 `git commit`告诉Git，把文件提交到仓库。     //git commit -m "内容"
                  我们下面可以通过命令`git status`来查看是否还有文件未提交，
                  使用`git diff readme.md `看下`readme.md`文件到底改了什么内容
              
* 第三步：用命令` git push `更新github
                  知道了对readme.txt文件做了什么修改后，我们可以放心的提交到仓库了，
                  提交修改和提交文件是一样的2步(第一步是`git add `第二步是：`git commit`，中间可以用`git status`检查)。
              
              
              
#### 版本回退

* 想查看下历史记录，如何查呢？我们现在可以使用命令 `git log `
  如果嫌显示的信息太多的话，我们可以使用命令 `git log –pretty=oneline`
* 我想把当前的版本回退到上一个版本，可以使用如下2种命令，
  第一种 是：`git reset --hard HEAD^` 那么如果要回退到上上个版本只需把`HEAD^ `改成 `HEAD^^ `以此类推。
  第二种 那如果要回退到前100个版本的话,我们可以使用下面的简便命令操作：`git reset --hard HEAD~100` 即可。
* 可以通过 `cat textme.md` 查看文件内容 但是现在我想回退到最新的版本，我们可以通过版本号回退，使用命令方法如下：`git reset --hard` 版本号
  可以通过如下命令即可获取到版本号：`git reflog `
  再用` cat` 命令查看内容

#### 工作区与暂存区的区别 

*  **工作区**：就是你在电脑上看到的目录，比如目录下testgit里的文件(.git隐藏目录版本库除外)。
                  或者以后需要再新建的目录文件等等都属于工作区范畴。

*  **版本库(Repository)**：工作区有一个隐藏目录.git,这个不属于工作区，这是版本库。
                                          其中版本库里面存了很多东西，其中最重要的就是stage(暂存区)，
                                          还有Git为我们自动创建了第一个分支master,以及指向master的一个指针HEAD。

* 我们前面说过使用Git提交文件到版本库有两步：

  第一步：是使用 git add 把文件添加进去，实际上就是把文件添加到暂存区。

​        第二步：使用git commit提交更改，实际上就是把暂存区的 所有内容 提交到当前分支上。(包括修改和新建文件 都一次性提交)

#### Git撤销修改和删除文件操作 
* 一  撤销修改：
  	在我未提交之前，我发现添加的内容有误，所以我得马上恢复以前的版本，现在我可以有如下几种方法可以做修改：

  ​	第一：如果我知道要删掉那些内容的话，直接手动更改去掉那些需要的文件，然后add添加到暂存区，最后commit掉。

  ​	第二：我可以按以前的方法直接恢复到上一个版本。使用 git reset --hard HEAD^

  ​	但是现在我不想使用上面的2种方法，我想直接想使用撤销命令该如何操作呢？
  ​	首先在做撤销之前，我们可以先用 git status 查看下当前的状态。如下所示：
  ​	可以发现，Git会告诉你，git checkout -- file 可以丢弃工作区的修改
  ​    git checkout -- readme.txt
  
* 二  删除文件：
   一般情况下，可以直接在文件目录中把文件删了，或者使用如上rm命令：rm b.txt ，

   果我想彻底从版本库中删掉了此文件的话，可以再执行commit命令提交掉

   只要没有commit之前，如果我想在版本库中恢复此文件，可以使用如下命令 git checkout -- b.txt

#### 远程仓库

* 一  通过本地库到远程库
  git remote add origin https:// ..... 命令 

  再使用 git push -u origin master 命令 把本地库推送到远程

  之后 只要是本地提交 就直接通过 git push origin master 命令 把本地master分支的最新修改推送到github上

* 二  如何从远程库克隆
  git clone https://.....  命令

#### 分支管理

