### **1 版本控制工具应该具备的功能**

- 协同修改
    - 多人并行不悖的修改[服务器](https://cloud.tencent.com/act/pro/promotion-cvm?from_column=20065&from=20065)端的同一个文件。
- 数据备份
    - 不仅保存目录和文件的当前状态，还能够保存每一个提交过的历史状态。
- 版本管理。
    - 在保存每一个版本的文件信息的时候要做到不保存重复数据，以节约存储空间，提高运行效率。这方面 **SVN** **采用的是增量式管理的方式**，而 **Git**采取了**文件系统**快照的方式**。
- 权限控制
    - 对团队中参与开发的人员进行权限控制。
    - 对团队外开发者贡献的代码进行审核 -> Git 独有。
- 历史记录
    - 查看修改人、修改时间、修改内容、日志信息。
    - 将本地文件恢复到某一个历史状态。
- 分支管理
    - 允许开发团队在工作过程中多条生产线同时推进任务，进一步提高效率。

### **2 版本控制简介**

#### **2.1 版本控制**

> 工程设计领域中使用版本控制管理工程蓝图的设计过程。在 IT 开发过程中也可以使用版本控制思想管理代码的版本迭代。

#### **2.2 版本控制工具**

思想：版本控制

实现：版本控制工具

集中式版本控制工具：

  CVS、SVN、VSS ……

![](https://ask.qcloudimg.com/http-save/yehe-3541135/6vmtioctkb.png)

分布式版本控制工具：

  Git、Mercurial、Bazaar、Darcs ……

![](https://ask.qcloudimg.com/http-save/yehe-3541135/ev36ixcuvk.png)

### **3 Git 简介**

#### **3.1 Git 的简史**

![](https://ask.qcloudimg.com/http-save/yehe-3541135/si0eznlrtf.png)

#### **3.2 Git 官网和 Logo**

官网地址：[https://git-scm.com/](https://cloud.tencent.com/developer/tools/blog-entry?target=https%3A%2F%2Fgit-scm.com%2F&source=article&objectId=1388538)

![](https://ask.qcloudimg.com/http-save/yehe-3541135/xueoetlewz.png)

#### **3.3 Git 的优势**

- 大部分操作在本地完成，不需要联网
- 完整性保证
- 尽可能添加数据而不是删除或修改数据
- 分支操作非常快捷流畅
- 与 Linux 命令全面兼容

#### **3.4 Git 的安装**

参考链接文章：[https://cloud.tencent.com/developer/article/1379679](https://cloud.tencent.com/developer/article/1379679?from_column=20421&from=20421)

`注：`

  1、安装到一个没有中文和没有空格的目录

  2、Git的默认编辑器：建议使用Vim编辑器

#### **3.5 Git 的本地结构**

![](https://ask.qcloudimg.com/http-save/yehe-3541135/et8v7xiv63.png)

#### **3.6 Git 和代码托管中心**

> 代码托管中心的任务：维护远程仓库。

- 局域网环境下
    - GitLab 服务器
- 外网环境下
    - GitHub
    - 码云
    - Coding

#### **3.7 本地仓库和远程仓库**

##### **3.7.1 团队内部协作**

![](https://ask.qcloudimg.com/http-save/yehe-3541135/v1k48q5dyt.png)

##### **3.7.2 跨团队协作**

![](https://ask.qcloudimg.com/http-save/yehe-3541135/vziqekhtnd.png)

### **4 Git 命令行操作**

#### **4.1 本地仓库初始化**

命令：git init

效果：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/upvm15ueu9.png)

`注：`.git目录中存放的是本地库相关的子目录和文件，不要删除，也不要胡乱修改。

#### **4.2 设置签名**

形式：

  用户名：tom

  Email地址：goodMorning@atguigu.com

作用：区分不同开发人员的身份。

辨析：这里设置的签名和登录远程库(代码托管中心)的账号、密码没有任何关系。

命令：

  项目级别/仓库级别：仅在当前本地库范围内有效

    git config user.name zackCao

    git config user.email shuoc186@gmail.com

    设置的信息保存位置：`./.git/config 文件`

![](https://ask.qcloudimg.com/http-save/yehe-3541135/wj3pdrkamo.png)

  系统用户级别：登录当前操作系统的用户范围

    git config --global user.name zackCao_glb

    git config --global user.email shuoc186@gmail.com

    设置的信息保存位置：`~/.gitconfig 文件`

![](https://ask.qcloudimg.com/http-save/yehe-3541135/04njews2zh.png)

  级别优先级：

    就近原则：项目级别优先于系统用户级别，二者都有时采用项目级别的签名。

    如果只有系统用户级别的签名，就以系统用户级别的签名为准。

    二者都没有不允许。

`实际开发中我们设置的是系统用户级别较多`。

#### **4.3 基本操作**

##### **4.3.1 状态查看**

git status

  查看工作区、暂存区状态

##### **4.3.2 添加**

git add filename

  将工作区的“新建/修改”添加到暂存区

##### **4.3.3 提交**

git commit -m "commit message" filename

  将暂存区的内容提交到本地仓库

以上三个命令的实际操作图解如下：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/i6kdkjf98n.png)

##### **4.3.4 查看历史记录**

git log

  多屏显示控制方式：

  空格向下翻页

  b 向上翻页

  q 退出

![](https://ask.qcloudimg.com/http-save/yehe-3541135/60jvdj0czb.png)

git log --pretty=oneline

![](https://ask.qcloudimg.com/http-save/yehe-3541135/1sws0lmoix.png)

git log --oneline

![](https://ask.qcloudimg.com/http-save/yehe-3541135/76k6gl5xwl.png)

git reflog

![](https://ask.qcloudimg.com/http-save/yehe-3541135/mmns43ch5s.png)

HEAD@{移动到当前版本需要多少步}

##### **4.3.5 版本的前进后退**

本质：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/c960ch086.png)

基于索引值操作推荐

  git reset --hard 局部索引值

  git reset --hard c433284

使用^符号：只能后退

  git reset --hard HEAD^

  注：一个^表示后退一步，n个^表示后退n步

使用~符号：只能后退

  git reset --hard HEAD~n

  注：表示后退n步

![](https://ask.qcloudimg.com/http-save/yehe-3541135/dkb8cioy5u.png)

查看文件的最后3行数据：

  tail -n 3 good.txt

![](https://ask.qcloudimg.com/http-save/yehe-3541135/qnpfwoen93.png)

##### **4.3.6 reset命令的三个参数对比**

打开Git命令的本地帮助文档：

  $ git help reset

![](https://ask.qcloudimg.com/http-save/yehe-3541135/4o1ikfih16.png)

注：打开的是本地的帮助文档

![](https://ask.qcloudimg.com/http-save/yehe-3541135/spyminqzra.png)

--soft 参数

  表示仅仅在本地库中移动HEAD指针

![](https://ask.qcloudimg.com/http-save/yehe-3541135/7ku2p0a222.png)

--mixed 参数

  表示在本地库移动HEAD指针

  且重置暂存区（修改）

![](https://ask.qcloudimg.com/http-save/yehe-3541135/flfe266q92.png)

--hard 参数

  表示在本地库移动HEAD指针

  且重置暂存区（index file）

  且重置工作区（working tree）

![](https://ask.qcloudimg.com/http-save/yehe-3541135/sq2u7k0vz7.png)

##### **4.3.7 删除文件并找回**

演示前提：删除前，文件存在的状态是已提交到了本地库后再进行删除操作。

操作：git reset --hard 指针位置

  删除操作已经提交到本地库：`指针位置指向历史记录`

  删除操作尚未提交到本地库：`指针位置使用HEAD`

任何一个`已经提交`的版本操作，就会在本地版本库中有一个确定的记录，记录着该文件的操作，即便我们做的是`提交删除`的操作，那么该记录也是不可磨灭的。

> Git只会增加版本，而不会把任何一个版本删除。 本地库 == 本地仓库 == 本地版本库

删除操作已经提交到本地库完整截图如下：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/9ibcvlgkjk.png)

找回删除操作已经提交到本地库完整截图如下：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/ixghgwxadd.png)

删除操作尚未提交到本地库完整截图如下：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/s2dhanyhof.png)

找回删除操作尚未提交到本地库完整截图如下：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/4wmu5ptecf.png)

##### **4.3.8 比较文件差异**

> git 是以行为单位进行文件管理的。

git diff 文件名

  将工作区中的文件和暂存区中的文件进行比较

git diff 本地库中某一历史版本

  将工作区中的文件和本地库历史记录进行比较

![](https://ask.qcloudimg.com/http-save/yehe-3541135/dl59k1hota.png)

注：不指定具体文件名时候表示比较多个文件。

![](https://ask.qcloudimg.com/http-save/yehe-3541135/g9ebaorc0j.png)

#### **4.4 分支管理**

##### **4.4.1 什么是分支**

![](https://ask.qcloudimg.com/http-save/yehe-3541135/88lnilncf9.png)

在版本控制过程中，使用多条线同时推进多个任务。

##### **4.4.2 分支的好处**

　　1、同时并行推进多个功能开发，提高开发效率。

　　2、各个分支在开发过程中，如果某一个分支开发失败，不会对其他分支有任何影响。失败的分支删除重新开始即可。

##### **4.4.3 分支的具体操作**

创建分支

  git branch 分支名

查看分支

  git branch -v

切换分支

  git checkout 分支名

![](https://ask.qcloudimg.com/http-save/yehe-3541135/5pfxrypxbk.png)

合并分支

  第一步：切换到接受修改的分支（即被合并，增加新内容的分支）上

  git checkout 被合并的分支名

  第二步：执行merge命令

  git merge 有新内容的分支名

![](https://ask.qcloudimg.com/http-save/yehe-3541135/m4aktoeff2.png)

解决冲突

  冲突的表现

![](https://ask.qcloudimg.com/http-save/yehe-3541135/k3vrryyflc.png)

  冲突的解决

    第一步：编辑文件，删除特殊符号

    第二步：把文件修改到满意的程度（`需要与他人沟通或者自己决定`），保存退出

![](https://ask.qcloudimg.com/http-save/yehe-3541135/e0h0ognnlk.png)

    第三步：git add 文件名

    第四步：git commit -m "日志信息"

    注意：此时commit一定不能带具体文件名

### **5 Git 的基本原理**

#### **5.1 哈希**

![](https://ask.qcloudimg.com/http-save/yehe-3541135/2q735gy8r3.png)

> 哈希是一个系列的加密算法，各个不同的哈希算法虽然加密强度不同，但是有以下几个共同点：   ① 不管输入数据的数据量有多大，输入同一个哈希算法，得到的加密结果长度固定。   ② 哈希算法确定，输入数据确定，输出数据能够保证不变。   ③ 哈希算法确定，输入数据有变化，输出数据一定有变化，而且通常变化很大。   ④ 哈希算法不可逆。(但可以穷举) Git底层采用的是`SHA-1算法`。 `哈希算法可以被用来验证文件`。原理如下图所示：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/lripcb1fxm.png)

Git就是靠这种机制来从根本上保证数据完整性的。

#### **5.2 Git 保存版本的机制**

##### **5.2.1 集中式版本控制工具的文件管理机制**

  以文件变更列表的方式存储信息。这类系统将它们保存的信息看作是一组基本文件和每个文件随时间逐步累积的差异。

![](https://ask.qcloudimg.com/http-save/yehe-3541135/n4ee15hwbl.png)

##### **5.2.2 Git的文件管理机制**

  Git把数据看作是小型文件系统的一组快照。每次提交更新时Git都会对当前的全部文件制作一个快照并保存这个`快照的索引`。为了高效，如果文件没有修改，Git不再重新存储该文件，而是只保留一个链接`指向`之前存储的文件。所以Git的工作方式可以称之为`快照流`。

![](https://ask.qcloudimg.com/http-save/yehe-3541135/3ocmj3l19c.png)

##### **5.2.3 Git 文件管理机制细节**

Git的“提交对象”：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/rmphihwipg.png)

提交对象及其父对象形成的链条

![](https://ask.qcloudimg.com/http-save/yehe-3541135/icfhfh3ihp.png)

> `类似于比特币`：比特币内部管理交易和Git里面管理文件有很大的相似点，Git里面的每一个文件，相当于比特币内部管理的一个交易。   比特币是把所有的交易（包括交易本身）两两做哈希运算，一直归并为最后的一个哈希，这就成了一个区块，每一个区块还要保存上一个区块里面的哈希和下一个区块里面的哈希。所以通过哈希算法就构成一个严密严谨的数据链条，其中的任何一个数据，只要做过哈希了，区块确认过了，就不能被修改了。

#### **5.3 Git 的分支管理机制**

##### **5.3.1 分支的创建**

![](https://ask.qcloudimg.com/http-save/yehe-3541135/6h6g77xrz6.png)

##### **5.3.2 分支的切换**

1、

![](https://ask.qcloudimg.com/http-save/yehe-3541135/taurc3wvsv.png)

2、

![](https://ask.qcloudimg.com/http-save/yehe-3541135/7w07m8vxn9.png)

3、

![](https://ask.qcloudimg.com/http-save/yehe-3541135/r7ve0b90w2.png)

4、

![](https://ask.qcloudimg.com/http-save/yehe-3541135/yql3ajfn8k.png)

### **6 GitHub**

#### **6.1 创建GitHub账号**

GitHub首页就是注册页面：[https://github.com/](https://cloud.tencent.com/developer/tools/blog-entry?target=https%3A%2F%2Fgithub.com%2F&source=article&objectId=1388538)

为了演示方便，注册了3个人github的账号：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/lq19ln05te.png)

以下演示，本博主只有一个GitHub远程仓库。

#### **6.2 创建远程仓库**

本地库先做一个准备工作，如下图所示：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/7jbc7f1usj.png)

创建以一个远程仓库

![](https://ask.qcloudimg.com/http-save/yehe-3541135/8mtreocil2.png)

输入一些信息后，点击创建

![](https://ask.qcloudimg.com/http-save/yehe-3541135/s3x8u2yx7r.png)

远程仓库创建成功后的截图

![](https://ask.qcloudimg.com/http-save/yehe-3541135/1rsnmt8q5s.png)

#### **6.3 在本地创建远程仓库地址别名**

git remote -v 查看当前所有远程地址别名

git remote add 别名

注：别名起什么都可以！

![](https://ask.qcloudimg.com/http-save/yehe-3541135/xtqxdsa0lq.png)

#### **6.4 本地仓库推送到远程仓库**

git push 别名

`注：`首次推送需要填写GitHub账号和密码。

![](https://ask.qcloudimg.com/http-save/yehe-3541135/bupnjtw8l2.png)

#### **6.5 克隆**

git clone [https://github.com/heizemingjun/huashan.git](https://cloud.tencent.com/developer/tools/blog-entry?target=https%3A%2F%2Fgithub.com%2Fheizemingjun%2Fhuashan.git&source=article&objectId=1388538)

![](https://ask.qcloudimg.com/http-save/yehe-3541135/lhvriobqt.png)

效果：

  1、完整的把远程库下载到本地

  2、创建origin作为远程仓库地址别名

  3、初始化本地库

#### **6.6 邀请团队成员**

> `注：`以下演示，使用的是“6.1 创建GitHub账号”中的三个GitHub账号为准！

以“岳不群”的身份去邀请“令狐冲”加入团队：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/adwo12blt2.png)

“岳不群”通过其他方式把邀请链接发送给“令狐冲”，“令狐冲”登录自己的GitHub账号，访问邀请链接。即可加入团队！

![](https://ask.qcloudimg.com/http-save/yehe-3541135/zfd3pqnofe.png)

我们发现输入GItHub的账户和密码之后，下次就不用再输入了，为什么呢？

答：对于http连接来说，Git本身没有记住账户名和密码的功能，是因为我们Win10系统有一个【凭据管理器】记住了GitHub的账户名和密码。

打开【控制面板】-->【类别】-->【小图标】

![](https://ask.qcloudimg.com/http-save/yehe-3541135/6m50cd03gd.png)

点击【凭据管理器】

![](https://ask.qcloudimg.com/http-save/yehe-3541135/v4zp6xcd13.png)

再点击【Windows凭据】

![](https://ask.qcloudimg.com/http-save/yehe-3541135/t4rz7ew8ua.png)

如果下次我们想切换别的GitHub账号和密码进行登录的话，就将该选项删除掉。点击【删除】选项即可。

![](https://ask.qcloudimg.com/http-save/yehe-3541135/wp2iue5552.png)

#### **6.7 拉取**

  pull=fetch+merge

  git fetch 远程库地址别名 该操作只是把远程仓库的内容下载到本地，但并没有修改本地工作区的文件，该命令的作用是：先抓取下来查看下，没有问题才去合并。这样保险！

  git merge 远程库地址别名/远程分支名

  git pull 远程库地址别名

`注：`fetch和pull属于读操作，不需要登录账号和密码！

`补：`

  git checkout orgin/master 切换到远程仓库的主分支

  git checkout master 切换到本地仓库的主分支

#### **6.8 解决冲突**

要点：

  如果`不是基于GitHub远程库的最新版所做的修改`，不能直接推送，必须先拉取。

  拉取下来后如果进入冲突状态，则按照【分支冲突的解决】操作解决即可。

类比：

  债权人：老王（发债的人）

  债务人：小刘（欠债的人）

  老王说：10天后归还。小刘接受，双方达成一致。

  老王媳妇说：5天后归还。小刘不能接受。老王媳妇需要找老王确认后再执行。

#### **6.9 跨团队协作**

**Fork**

![](https://ask.qcloudimg.com/http-save/yehe-3541135/uohc3zdeat.png)

正在Forking……请稍等！

![](https://ask.qcloudimg.com/http-save/yehe-3541135/bacvkip08x.png)

Fork成功后的截图：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/ru2dxf9nhk.png)

“东方不败”将远程仓库的内容克隆到本地仓库后，进行修改，然后推送到“自己的远程仓库”。

---

“东方不败”将“自己的远程仓库”推送到“岳不群的远程仓库”的操作：

点击【Pull requests】

![](https://ask.qcloudimg.com/http-save/yehe-3541135/116sldv4z7.png)

再点击【New pull request】

![](https://ask.qcloudimg.com/http-save/yehe-3541135/efxi1kzrty.png)

再点击【Create pull request】

![](https://ask.qcloudimg.com/http-save/yehe-3541135/vn81tjznr3.png)

填写此次修改的【标题】和【修改说明】后，再点击【Create pull request】

![](https://ask.qcloudimg.com/http-save/yehe-3541135/pzl4696x69.png)

创建拉取请求成功后的页面：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/w5w96xn9xu.png)

---

岳不群这边点击【Pull requests】按钮

![](https://ask.qcloudimg.com/http-save/yehe-3541135/lgtctxalcu.png)

岳不群可以查看东方不败发过来的消息

![](https://ask.qcloudimg.com/http-save/yehe-3541135/6ky6egwofd.png)

消息详情如下：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/ufo30k22gt.png)

**对话/评论**

![](https://ask.qcloudimg.com/http-save/yehe-3541135/bchqpzxt7x.png)

对话细节：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/fykat0rnc2.png)

**审核代码**

经过一番唇枪舌战之后，岳不群要合并代码了，合并代码前需要先审核代码：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/kk2rk286t0.png)

**合并代码**

岳不群审核代码没有问题，就可以进行代码合并了！点击【Conversation】

![](https://ask.qcloudimg.com/http-save/yehe-3541135/v2qc0gfhqg.png)

填写本次操作的日志信息：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/pizid4dhyd.png)

岳不群再将远程仓库的修改拉取到本地仓库，远程团队协作完成。

#### **6.10 SSH登录**

>   如果Windows系统没有凭据管理器为我们保存GitHub的账号和密码，那么我们`基于Http地址`的方式进行push操作的时候，就需要每次输入GitHub的账号和密码，比较麻烦，有没有别的方法呢？   答：答案是肯定的！使用`SSH方式`登录。缺点：这种方式只能为一个账号和密码进行设置，实际开发中，我们有一个GitHub账号已经够用了。

**演示SSH登录**

进入当前用户的家目录

`$ cd ~`

删除.ssh目录

`$ rm -rvf .ssh`

运行命令生成.ssh密钥目录

`$ ssh-keygen -t rsa -C heizemingjun@gmail.com`

`注意：`这里-C这个参数是大写的C。

  需要确认几个信息，我们点击几下回车即可。回车表示使用默认值。

进入.ssh目录查看文件列表

`$ cd .ssh`

`$ ls -lF`

查看id_rsa.pub文件内容

`$ cat id_rsa.pub`

![](https://ask.qcloudimg.com/http-save/yehe-3541135/grjl0eyjzi.png)

复制id_rsa.pub文件内容，登录GitHub，点击用户头像 -> Settings -> SSH and GPG keys -> New SSH Key

输入复制的密钥信息，随意起一个“Title”名称。再点击【And SSH key】。

再回到客户端Gitbash创建远程地址别名

`git remote add orgin_ssh git@github.com:heizemingjun/huashan.git`

推送文件进行测试，没有问题

![](https://ask.qcloudimg.com/http-save/yehe-3541135/ka48i1rbiw.png)

### **7 Eclipse操作**

#### **7.1 将Maven工程初始化为本地仓库**

工程 -> 右键 -> Team -> Share Project -> Git

![](https://ask.qcloudimg.com/http-save/yehe-3541135/p3sj0m41n0.png)

选中项目后点击【Create Repository】

![](https://ask.qcloudimg.com/http-save/yehe-3541135/6bvi3vyeue.png)

就会在该项目目录下创建.git目录，点击【Finish】

![](https://ask.qcloudimg.com/http-save/yehe-3541135/06zq0uhzqr.png)

查看该工程的配置

![](https://ask.qcloudimg.com/http-save/yehe-3541135/ccw7gx9x2r.png)

**在****Eclipse****中设置本地仓库的范围签名**

点击【And Entry…】，输入用户名

![](https://ask.qcloudimg.com/http-save/yehe-3541135/ag20e71cjz.png)

输入邮箱，同理。

设置好后的效果：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/afqw1czyew.png)

**在Eclipse中Git图标的介绍**

![](https://ask.qcloudimg.com/http-save/yehe-3541135/zqd69r2hjw.png)

#### **7.2 Eclipse中忽略文件**

![](https://ask.qcloudimg.com/http-save/yehe-3541135/mfqf8uc5pv.png)

**概念：Eclipse特定文件**

这些都是Eclipse为了管理我们创建的工程而维护的文件，和开发的代码没有直接关系。最好不要在Git中进行追踪，也就是把它们忽略。

  .classpath 文件

  .project 文件

  .settings 目录下所有文件

**为什么要忽略Eclipse特定文件呢？**

  同一个团队中很难保证大家使用相同的IDE工具，而IDE工具不同时，相关工程特定文件就有可能不同。如果这些文件加入版本控制，那么开发时很可能需要为了这些文件解决冲突。

![](https://ask.qcloudimg.com/http-save/yehe-3541135/kz4cewm62n.png)

**GitHub官网样例文件**

[https://github.com/github/gitignore](https://cloud.tencent.com/developer/tools/blog-entry?target=https%3A%2F%2Fgithub.com%2Fgithub%2Fgitignore&source=article&objectId=1388538)

[https://github.com/github/gitignore/blob/master/Java.gitignore](https://cloud.tencent.com/developer/tools/blog-entry?target=https%3A%2F%2Fgithub.com%2Fgithub%2Fgitignore%2Fblob%2Fmaster%2FJava.gitignore&source=article&objectId=1388538)

**编辑本地忽略配置文件，文件名任意**

Java.gitignore

代码语言：javascript

复制

```javascript
# Compiled class file
*.class

# Log file
*.log

# BlueJ files
*.ctxt

# Mobile Tools for Java (J2ME)
.mtj.tmp/

# Package Files #
*.jar
*.war
*.nar
*.ear
*.zip
*.tar.gz
*.rar

# virtual machine crash logs, see http://www.java.com/en/download/help/error_hotspot.xml
hs_err_pid*

.classpath
.project
.settings
target
```

推荐放置忽略文件的目录：C:\Users\bruce目录下

在`~/.gitconfig`文件中引入上述文件

代码语言：javascript

复制

```javascript
[core]
    excludesfile = C:/Users/bruce/Java.gitignore
```

`注意：`这里路径中一定要使用“/”，不能使用“\”，linux中只识别正斜杠。

**Eclipse中查看忽略文件是否被读取成功**

![](https://ask.qcloudimg.com/http-save/yehe-3541135/3e2he8pn8a.png)

效果：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/fch0yxcufv.png)

**Eclipse中本地仓库的基本操作**

1、将工程添加至本地暂存区

![](https://ask.qcloudimg.com/http-save/yehe-3541135/c2er08qjbi.png)

效果：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/l328cb60y7.png)

2、将工程提交至本地仓库

![](https://ask.qcloudimg.com/http-save/yehe-3541135/053jmtxv2n.png)

效果：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/9gs6pzoa5a.png)

3、填写提交的日志信息后点击【提交】按钮

![](https://ask.qcloudimg.com/http-save/yehe-3541135/vta820bf4e.png)

角标变为小金桶

![](https://ask.qcloudimg.com/http-save/yehe-3541135/8twzo5o4s2.png)

#### **7.3 推送到远程仓库**

0、准备工作：先在GitHub上新建一个与Eclipse工程名相同的远程仓库TestGit。

1、然后在Eclipse上进行操作

![](https://ask.qcloudimg.com/http-save/yehe-3541135/xzpx10xxpv.png)

2、填写相关信息：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/a4qy7b39tg.png)

3、点击【Add All Branches Spec】

![](https://ask.qcloudimg.com/http-save/yehe-3541135/h0et8wyity.png)

4、填写特定的日志信息，一般我们使用默认的即可

![](https://ask.qcloudimg.com/http-save/yehe-3541135/yid0yrnrzc.png)

5、操作成功后的截图

![](https://ask.qcloudimg.com/http-save/yehe-3541135/8sll83ho8n.png)

#### **7.4 Oxygen Eclipse 克隆工程操作**

1、Import…导入工程

![](https://ask.qcloudimg.com/http-save/yehe-3541135/93otolwwwh.png)

2、Clone URI

![](https://ask.qcloudimg.com/http-save/yehe-3541135/9zkmx847bc.png)

3、到远程库复制工程（仓库）地址

![](https://ask.qcloudimg.com/http-save/yehe-3541135/kptvgfw2hg.png)

4、粘贴

![](https://ask.qcloudimg.com/http-save/yehe-3541135/jqq0odimff.png)

5、选择分支

![](https://ask.qcloudimg.com/http-save/yehe-3541135/3waipzdwwp.png)

6、指定工程的保存位置

![](https://ask.qcloudimg.com/http-save/yehe-3541135/3p4nj61xf1.png)

7、指定工程导入方式，这里只能用：Import as general project

![](https://ask.qcloudimg.com/http-save/yehe-3541135/83ozb6t4vq.png)

8、填写工程名，点击【Finish】

![](https://ask.qcloudimg.com/http-save/yehe-3541135/fxm40rr3lg.png)

9、转换工程类型

![](https://ask.qcloudimg.com/http-save/yehe-3541135/ahnoo18nv5.png)

10、最终效果

![](https://ask.qcloudimg.com/http-save/yehe-3541135/fc5mvp34sj.png)

#### **7.5 KeplerEclipse 克隆工程操作**

其余步骤同上。

问题：不能保存到当前Eclipse工作区目录

![](https://ask.qcloudimg.com/http-save/yehe-3541135/wlph6e1ar0.png)

正确做法：保存到工作区以外的目录中

![](https://ask.qcloudimg.com/http-save/yehe-3541135/doe0h4y0ee.png)

#### **7.6 解决冲突**

![](https://ask.qcloudimg.com/http-save/yehe-3541135/zhgwv1f5k8.png)

冲突文件 -> 右键 -> Team -> Merge Tool

修改完成后正常执行add/commit操作即可。

### **8 Git 的工作流**

#### **8.1 概念**

> 在项目开发过程中使用Git的方式。

#### **8.2 分类**

##### **8.2.1 集中式工作流**

> 像SVN一样，集中式工作流以中央仓库作为项目所有修改的单点实体。所有修改都提交到Master这个分支上。 这种方式与SVN的主要区别就是开发人员有本地库。Git很多特性并没有用到。

![](https://ask.qcloudimg.com/http-save/yehe-3541135/63e7mbidzi.png)

##### **8.2.2 GitFlow工作流**

> Gitflow工作流通过为功能开发、发布准备和维护设立了独立的分支，让发布迭代过程更流畅。严格的分支模型也为大型项目提供了一些非常必要的结构。

![](https://ask.qcloudimg.com/http-save/yehe-3541135/0ilznspc8j.png)

##### **8.2.3 Forking工作流**

> Forking工作流是在GitFlow基础上，充分利用了Git的Fork和pull request的功能以达到`代码审核`的目的。更适合安全可靠地管理大团队的开发者，而且能接受不信任贡献者的提交。

![](https://ask.qcloudimg.com/http-save/yehe-3541135/xvorudmaex.png)

#### **8.3 详解**

##### **8.3.1 分支种类**

**主干分支 master**

  主要负责管理正在运行的生产环境代码。永远保持与正在运行的生产环境完全一致。

**开发分支 develop**

  主要负责管理正在开发过程中的代码。一般情况下应该是最新的代码。

**bug修理分支 hotfix**

  主要负责管理生产环境下出现的紧急修复的代码。从主干分支分出，修理完毕并测试上线后，并回主干分支。并回后，视情况可以删除该分支。

**准生产分支（预发布分支） release**

  较大的版本上线前，会从开发分支中分出准生产分支，进行最后阶段的集成测试。该版本上线后，会合并到主干分支。生产环境运行一段阶段较稳定后可以视情况删除。

**功能分支 feature**

  为了不影响较短周期的开发工作，一般把中长期开发模块，会从开发分支中独立出来。开发完成后会合并到开发分支。

##### **8.3.2 GitFlow工作流举例**

![](https://ask.qcloudimg.com/http-save/yehe-3541135/q3h4pf84nr.png)

##### **8.3.3 分支实战**

![](https://ask.qcloudimg.com/http-save/yehe-3541135/bci0390pfe.png)

`注：`创建分支、审查代码、合并分支这些操作都在本地做，不在远程做。而且往master上去合并代码时，一定是有经验的程序员（比如项目经理、架构师等）去合并，这样有保障！

##### **8.3.4 具体操作**

对于令狐冲来说：

**创建分支**

![](https://ask.qcloudimg.com/http-save/yehe-3541135/7sbw49h84a.png)

**给分支起名字**

![](https://ask.qcloudimg.com/http-save/yehe-3541135/gn87zj2zlk.png)

完成后会自动切换到`hot_fix分支`，我们在`本地hot_fix分支上`做一些修改，再将该分支上的修改提交到本地仓库（快捷键方式Ctrl + `#`），然后将hot_fix分支上的修改推送到远程仓库。

---

对于岳不群来说：

执行拉取操作后，切换到分支审查代码

![](https://ask.qcloudimg.com/http-save/yehe-3541135/pc42te5jb9.png)

选择远程的分支

![](https://ask.qcloudimg.com/http-save/yehe-3541135/zxlgc161c1.png)

点击【Check out as New Local Branch】(检出为本地的新的分支)

![](https://ask.qcloudimg.com/http-save/yehe-3541135/mz61yhlkgm.png)

点击【Finish】即可

![](https://ask.qcloudimg.com/http-save/yehe-3541135/s0ivdn9n5i.png)

这样就检出远程的新的分支了！

> `岳老板`发现代码有的地方写的不够好，需要`小冲`继续修改，就`发微信`给`小冲`让他如何如何改，`小冲`在`本地hot_fix`分支继续修改后，再将该分支上的修改提交到本地仓库（快捷键方式Ctrl + `#`），然后将`hot_fix分支`上的修改推送到远程仓库。岳老板重新进行拉取，切换分支，审查代码……如此反复，直到没有问题了，这时候`岳老板`就在本地将`hot_fix分支`合并到主分支master上，操作如下：

先要从`hot_fix分支`切换回master分支

![](https://ask.qcloudimg.com/http-save/yehe-3541135/d2q2lpj7qq.png)

再进行合并分支操作

![](https://ask.qcloudimg.com/http-save/yehe-3541135/zlkk3zz79c.png)

使用本地的`hot_fix分支`

![](https://ask.qcloudimg.com/http-save/yehe-3541135/uf3kfbdrfr.png)

合并结果

![](https://ask.qcloudimg.com/http-save/yehe-3541135/ix8r2e4xwi.png)

本地合并成功后，需要把master推送到远程。

![](https://ask.qcloudimg.com/http-save/yehe-3541135/wds8abq3ag.png)

### **9 GitLab 服务器搭建过程**

> GitLab是局域网环境内的代码托管中心。

准备工作：

[VMware10.0 && VMware12.0 Pro && VMware14.0 Pro && VMware 15.0 Pro 的安装与破解](https://cloud.tencent.com/developer/article/1375840?from_column=20421&from=20421)

[VMware12.0 Pro 中安装 CentOS-7.5(桌面版)](https://cloud.tencent.com/developer/article/1375840?from_column=20421&from=20421)

[虚拟机CentOS 7.5 如何固定IP地址](https://cloud.tencent.com/developer/article/1375840?from_column=20421&from=20421)

  使用终端工具链接远程服务器：推荐使用全能终端：**MobaXterm_Personal_11.0.exe**，此乃神器中的神器！！！比SecureCRT、Xsheel要好！！！

#### **9.1 官网地址**

  首页：[https://about.gitlab.com/](https://cloud.tencent.com/developer/tools/blog-entry?target=https%3A%2F%2Fabout.gitlab.com%2F&source=article&objectId=1388538)

  安装说明：[https://about.gitlab.com/installation/](https://cloud.tencent.com/developer/tools/blog-entry?target=https%3A%2F%2Fabout.gitlab.com%2Finstallation%2F&source=article&objectId=1388538)

#### **9.2 安装命令摘录**

代码语言：javascript

复制

```javascript
sudo yum install -y curl policycoreutils-python openssh-server cronie
sudo lokkit -s http -s ssh
sudo yum install postfix
sudo service postfix start
sudo chkconfig postfix on
curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.rpm.sh | sudo bash 
sudo EXTERNAL_URL="http://gitlab.example.com" yum -y install gitlab-ee
```

实际问题：yum安装gitlab-ee(或ce)时，需要联网下载几百M的安装文件，非常耗时，所以应提前把所需RPM包下载并安装好。

下载地址为：

代码语言：javascript

复制

```javascript
https://packages.gitlab.com/gitlab/gitlab-ce/packages/el/7/gitlab-ce-10.8.2-ce.0.el7.x86_64.rpm
```

#### **9.3 调整后的安装过程**

代码语言：javascript

复制

```javascript
sudo rpm -ivh /opt/gitlab-ce-10.8.2-ce.0.el7.x86_64.rpm
sudo yum install -y curl policycoreutils-python openssh-server cronie
sudo lokkit -s http -s ssh
sudo yum install postfix
sudo service postfix start
sudo chkconfig postfix on
curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.rpm.sh | sudo bash 
sudo EXTERNAL_URL="http://gitlab.example.com"
```

安装过程中的截图：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/blvdt4b5u0.png)

当前步骤完成后重启虚拟机，命令：reboot。

#### **9.4 gitlab服务操作**

初始化配置gitlab

  gitlab-ctl reconfigure

启动gitlab服务

  gitlab-ctl start

查看gitlab服务运行状态

  gitlab-ctl status

停止gitlab服务

  gitlab-ctl stop

#### **9.5 浏览器访问**

访问Linux服务器IP地址即可，如果想访问`EXTERNAL_URL`指定的域名还需要配置域名服务器nginx和本地hosts文件。

初次登录时需要为gitlab的root用户设置密码。

  用户名：root

  密码：root1234

![](https://ask.qcloudimg.com/http-save/yehe-3541135/4bdhazga12.png)

> `注：`CenOS7需要停止防火墙服务：service firewalld stop，实际生产环境中需要设置相应的`防火墙策略`，用什么端口打开即可，不用的端口一律屏蔽；端口使用多少时间，也要设定。我们学习的时候，建议关闭虚拟机的防火墙。

登陆成功的界面：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/zo59ufjfuh.png)

后续操作同GitHub上的操作，大同小异，例如：创建一个项目（仓库），点击Create a project：

![](https://ask.qcloudimg.com/http-save/yehe-3541135/3i5lby2lrl.png)