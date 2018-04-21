### ** Docker镜像安装方法**

**安装方法一**
　　使用编写docker file的方式，该种方法Docker image的安装可以通过以下两个步骤来实现。
1、编写Dockerfile
　　dockerfile是为快速构建docker image而设计的，当你编写好docker file后，进行安装（调用docker　build 命令）的时候，docker 会读取当前目录下的命名为Dockerfile(首字母大写)的纯文本文件并执行里面的指令构建出一个docker image。**注意：文件名称是区分大小写的，必须是Dockerfile**。
　　例如: docker 镜像中安装RseQC软件，Dockerfile的编写如下：
```
　　FROM 192.168.1.162:5000/basepython:201701
　　MAINTAINER ZongJie <zongjie@novelbio.com>
　　ADD /software /bin/software/
　　RUN cd /bin/software/ \
　　\# ===bowtie====
　　&& ln -s /bin/software/bowtie/* /bin/ \
　　\# ===samtools====
　　&& ln -s /bin/software/samtools/samtools /bin/samtools \

　　\# ================= trinity ==================
　　&& cd /bin/software/trinityrnaseq-2.1.1 \
　　&& make \
　　&& ln -s /bin/software/trinityrnaseq-2.1.1/Trinity /bin/Trinity 
```
每行命令简单解释如下：
**FROM**  　
　　dockerfile里的第一条指令，后面跟有效的镜像名（如果该镜像你的本地仓库没有则会从远程仓库Pull取）。后面的指令在些镜像中执行。
　　FROM &lt;image&gt;:&lt;tag&gt;
　　如：FROM 192.168.1.162:5000/basepython:201701
　　表示新创建的镜像，继承于“192.168.1.162:5000/basepython:201701”这个镜像，也就是说“192.168.1.162:5000/basepython:201701”镜像中安装的软件，新创建的镜像中也已经安装过了，可以直接使用的，其中“192.168.1.162:5000/basepython”是&lt;image&gt;，“201701”是&lt;tag&gt;。

**MAINTAINER**
　　MAINTAINER &lt;name>　作者信息  用来注释Dockerfile是谁编写的。

**ADD**
　　ADD &lt;dir1>　&lt;dir2>  用来拷贝文件夹或者文件的，将当前路径下&lt;dir1&gt;的文件夹或文件，拷贝到镜像中的这个路径&lt;dir2&gt;中。
　　如：ADD /software /bin/software/
　　表示将当前路径中的/software 文件夹，拷贝到镜像中的/bin/software/，注意，当前文件路径的书写方式，是“/software”，而不是“./software”。 
    
**RUN**    
　　之后跟要执行的linux命令，每一条RUN指令（可能会有多条linux命令）会在当前容器最上面的可读写层执行并且提交成一个新的镜像层，接下来的指令会在这个新的镜像层里执行。
RUN &lt;command&gt; (the command is run in a shell – /bin/sh -c – shell form)。

　　RUN ["executable", "param1", "param2"] (exec form)
　　如：cd /bin/software/ \       
　　表示进入镜像中的“/bin/software/”路径中。
　　注意多个命令行的CMD命令可以使用，如下的方式。
```
RUN cd /bin/software/ \
\# ===bowtie====    注释信息，不执行
&& ln -s /bin/software/bowtie/* /bin/ \
\# ===samtools====   注释信息，不执行
&& ln -s /bin/software/samtools/samtools /bin/samtools 
```
　　注意下面的情况： 　
　　1. 不要在一条RUN指令里单一使用apt-get update命令，这样可能会导致以后的apt-get install 安装出错。
　　2. 避免使用RUN apt-get upgrade 或者dist-upgrade，这样有些重要的软件包可能更新失败，如果你确实想要更新某个包A，使用apt-get install install  -y A 。这样会自动更新这个软件包。更多请参考官方文档。
　　3. 要求Dockerfile和存放软件的software文件夹在相同的路径下，如：
 <div style="text-align:center">
<img data-src="1.png" width="280px"></img>
</div>
 **关于Dockerfile编写更详细的说明请见第二个文档“dockerfile编写规则”**
 
 2、运行Dockerfile
　　写好Dockerfile文件后就可以在该目录下运行“docker build .”命令了（可以用 -t 参数指定镜像名称和tag）。
　　如： docker build -t 192.168.199.101:5000/basepython:201701 .
　　其中“192.168.199.101:5000/basepython”为镜像名称，“201701”为tag；需要注意的有两点，1.镜像名称中不能有大写字母；2.安装命令后面的“.”不能少。
  
---

** 安装方法二**
　　而另一种构建docker iamge 的方法是pull一些基础镜像下来启动成容器，然后进入容器内安装各种需要的程序以及配置好需要的环境，最后commit成一个镜像。但是相比之 Dockerfile的方法会更加自动化，更加方便快捷，而且功能也更强大。
　　如：
　　#从仓库中pull下来镜像，如果本台服务器已经有这个镜像，可不用执行该命令。
　　docker pull 192.168.1.161:5000/base:201701 
　　#创建一个新容器
　　docker run -it 192.168.1.161:5000/base:201701
　　#执行一些安装软件的命令,如make 等
　　…..
　　#安装完后，调用软件，检查软件安装成功，可退出容器
　　exit
　　#使用commmit命令进行提交
　　docker commit 56c0160d1450 localhost:5000/biornaseq:201703
　　其中“56c0160d1450”为容器ID，如：
  <div style="text-align:center">
<img data-src="2.png" width="800px"></img>
</div>


### **NovelBio Docker Image 创建规范**
  
---

　　我们对第一种安装方法进行了改进，可以达到使用一条命令进行多个镜像一起安装的目的。
　　使用背景：
　　　　1. 大部分用户的文件存储路径拥有权限，而docker直接创建的镜像是root权限，使用root镜像会导致分析得到的结果无法被删除或下载。为了规避这种情况，我们需要对镜像设置权限，譬如novelbio权限。
　　　　2. docker有一些问题。如果存在一个压缩包blast.zip，大小为200MB。
　　　　　　使用ADD命令将blast.zip添加进入镜像，此时镜像大小为200MB
　　　　　　在镜像内部解压缩该压缩包，此时镜像大小为400MB
　　　　　　删除blast.zip，此时镜像大小不变
　　　　　　对blast/文件夹赋权限，此时镜像大小为600MB
　　　　这样会导致本来比较小的Docker镜像变得非常大。
　　因此我们提出了一个Docker镜像的创建规范，并提供了软件**dockerRun.jar**来进行自动化docker image构建
　　**规范**
1. 全部镜像放在一个总的文件夹下，如/home/mypath/dockerImages。文件名可以随便起名。
2. 在文件夹dockerImages/下，一个文件夹代表一个镜像，如：
　　/home/mypath/dockerImages/
　　　　----------------------/biobase
　　　　----------------------/biodna
　　　　----------------------/biorna
 <div style="text-align:center">
<img data-src="3.png" width="700px"></img>
</div>
**注意**：文件夹的名称会是创建镜像名称中的一部分，所以名称中不要有大写字母和特殊字符。

3. 每个镜像文件夹的结构如下
```
　　/biobase/
　　　　-----/bin/                                   #存放编译好的软件
　　　　---------/blastp                             #译好的软件 
　　　　---------/samtools

　　　　-----/software/                              #存放等待编译的软件，注意压缩文件只能是zip、tar.gz、tar.bz2、tar的压缩方式
　　　　--------------/pysam-0.8.4.tar.gz            #压缩包，无需解压
　　　　--------------/stringtie-1.33.tar.gz         #压缩包，无需解压
　　　　--------------/hisat2-2.2.1_linux_x86_64.zip #无需编译的软件，无需解压

　　　　-----/software201801patch/                   #这个软件可以专门给版本201801使用。

　　　　-----/r_install                              #R语言相关包的安装脚本

　　　　-----/DockerfileTmplt@201701                 #Dockerfile模板文件，版本201701
　　　　-----/DockerfileTmplt@201801                 #Dockerfile模板文件，版本201801
```　　
　　　　其中bin中存放编译好的软件，直接ADD进去就可以运行。software中保存需要编译的软件压缩包。r_install等脚本是需要安装R包或者其他perl包的脚本。DockerfileTmplt@201701是Dockerfile的模板文件，名字必须为DockerfileTmplt@<version>的格式。其中201701是待编译Dockerfile的版本号。
　　　　**以上 /biobase/ 会编译出两个镜像**，分别为 ${ip:port}/biobase:201701 和 ${ip:port}/biobase:201801

4. DockerfileTmplt@<version>命名规范
　　一个docker image文件夹中可以存放多个DockerfileTmplt文件，表示该docker镜像的多个版本。如DockerfileTmplt@201701、DockerfileTmplt@201801。当然也可以写成DockerfileTmplt@v1.1这种形式。
　　注意：NovelBrain在运行docker镜像时，如果存在多个版本，并且没有指定版本，会按照**比较字符串**的方式比较版本名并选择排序最大的那个版本号。譬如201703 > 201701；v12 > v11; **v3 > v12 **。因此注意版本号的命名规范。

5. DockerfileTmplt的内容
　　DockerfileTmplt写法基本同常规Dockerfile，略有不同。典型的DockerfileTmplt的写法如下：

```
　　FROM ${repoIpPort}/base:201701

　　MAINTAINER ZongJie <zongjie@novelbio.com>

　　ADD /bin/ /bin/software/
　　ADD /r_install /bin/software/
　　ADD /software/ /bin/software/

　　# ================= Pysam 安装 ==================
　　# 直接cd进入解压后的文件夹中然后编译
　　RUN cd /bin/software/pysam-0.8.4 \
　　&& python setup.py install \

　　# ================= stringtie 安装 ==================
　　# 直接cd进入解压后的文件夹中然后编译
　　&& cd /bin/software/stringtie-1.3.3 \
　　&& make \
　　&& ln -s /bin/software/stringtie-1.3.3/stringtie /bin/stringtie \

　　# ================= hisat2 =================
　　# 无需解压，直接做软链接
　　&& ln -s /bin/software/hisat2-2.1.1/hisat2 /bin/hisat2 \
　　&& ln -s /bin/software/hisat2-2.1.1/hisat2-build /bin/hisat2-build \
　　&& ln -s /bin/software/hisat2-2.1.1/extract_splice_sites.py /bin/extract_splice_sites.py

```
　　5.1 Dockerfile中的第一行，如FROM 192.168.1.162:5000/basepython:201701 ，写为FROM ${repoIpPort}/basepython:201701 ，其中${repoIpPort}参数，可以从后续安装命令中获取具体值。base:201701是继承的镜像。如果继承的镜像也在文件夹 /home/mypath/dockerImages 中。则dockerRun.jar 会递归编译该镜像。
　　5.2 ADD进去的压缩包无需解压，直接可以编译或使用。
　　5.3 所有操作权限均为root。

6. 运行dockerRun.jar程序，进行批量安装镜像
使用命令如下：
sudo java -jar dockerRun.jar -d /home/mypath/docker_images  -n bioplot -r localhost:5000  -p 123456 -u novelbio:1000 -g novelbio:1000
其中参数说明如下：
“-d”：镜像所在的父路径，里面应该是很多文件夹，每个文件夹的名字为镜像名，里面就是具体需要安装的镜像dockerfile和软件；
“-n”是需要安装的镜像名称，即文件夹名称，如果不设置才参数，表示“-d”中的所有镜像全部安装；
“-r”：镜像需要推送到的ip和端口。也就是repository的ip和端口
“-e”：参数“-d”中哪些镜像不用安装，
“-p”：sudo的密码
“-u”：镜像最后的执行用户和用户uid 譬如 novelbio:1000
“-g”：镜像最后执行用户所在的用户组和gid 譬如 novelbio:1000


编译某个具体镜像的具体版本
sudo java -jar dockerRun.jar -d /home/mypath/docker_images  -n bioplot**@201701** -r 192.168.0.123:5000  -p 123456 -u novelbio:1000 -g novelbio:1000
编译某个具体镜像的全部版本
sudo java -jar dockerRun.jar -d /home/mypath/docker_images  -n bioplot -r 192.168.0.123:5000  -p 123456 -u novelbio:1000 -g novelbio:1000
编译全部镜像
sudo java -jar dockerRun.jar -d /home/mypath/docker_images -r 192.168.0.123:5000  -p 123456 -u novelbio:1000 -g novelbio:1000

**注意**：
1.	当运行完该命令之后，会在当前文件夹中生成两个日志文件“errorInfo”和“finishInfo”，分别记录安装失败的镜像（文件夹名称），和安装成功的镜像（文件夹名称）。
2.	当“finishInfo”文件中有记录的安装成功的镜像时，再一次运行dockerRun.jar程序，会自动跳过已经记录的安装成功的镜像，所以，如果再次安装已经安装成功的镜像，需要 将“finishInfo”文件中已经的镜像名称删掉。

**运行机制**
dockerRun.jar 首先会检查本镜像的依赖镜像。如果依赖镜像不存在，则会首先创建依赖镜像。
1. dockerRun.jar 解压缩 /home/mypath/dockerImages/biobase 中的全部压缩文件，并赋权限。权限可以在命令中设置-u novelbio:1000 -g novelbio:1000。
2. 以Root方式开始编译，并且编译得到镜像 192.168.0.123:5000/bioplot.root:201701。注意该镜像的权限为root
3. 将文件夹 /home/mypath/dockerImages/add-user 中的 adduser.dockerfile 添加到 Dockerfile中，并再次编译镜像。得到192.168.0.123:5000/bioplot:201701。注意该镜像的权限为命令中设置的 -u novelbio:1000 -g novelbio:1000 权限。

**注意事项**：

1.	镜像中使用到的软件和文件存放的规则：
（1）	可执行文件，放在bin/中；
（2）	需要解压和需要解压后安装的软件放在software中；
2.	放在software中的需要解压文件的操作命令不用写在dockerfile中，因为系统会在安装之前完成自动解压的操作。
3.	放在software中的软件或者文件夹推荐使用zip压缩成.zip的文件。
4.	由于我们需要给镜像添加权限，所以构建镜像时会生成两个镜像如：
 <div style="text-align:center">
<img data-src="4.png" width="800px"></img>
</div>
第二个localhost:5000/biornaseq.root:201701是用来继承使用的，即当有另外一个镜像需要继承biornaseq的时候，需要继承该localhost:5000/biornaseq.root:201701镜像。需要注意的是，当我们写继承镜像的dockerfile时，不需要写(.root)，因为系统会自动识别，即，编写时只需写成“FROM localhost:5000/biornaseq:20170”。又由于我们编写了批量安装docker镜像的程序，实现了一次性可以选择性的安装多个镜像的功能，在使用该功能的时候，dockerfile的REPOSITORY 需要修改为名为“${repoIpPort}”的参数，所以，最终编写的形式应该为：“FROM ${repoIpPort}/ biornaseq:20170”。
5.	通常情况下task使用的镜像应该设置为没有（.root）名称，因为(.root)的镜像用户是root，当task是有该镜像生成的结果文件，普通用户没有权限进行删除结果文件以及结果文件夹的操作。
