# rpm yum & apt dpkg

## rpm

```bash
包含了所有的软件包

rpm -ivh xxx

rpm -evh xxx

rpm包的依赖性

树状依赖（从最底层开始安装）

A->B->C

环形依赖

A->B->C->A

模块依赖

A->B软件的函数或函数库

rpm -qi 包名 查看已安装的软件包信息

rpm -qpi 包名 查看未安装的软件包信息

-q 查询

-p

-l

-f 删除
```





### yum

yum是一个数据库客户端工具，底层仍然是rpm。

yum就是访问软件仓库的元数据，进而根据元数据里面的记录自动解决软件包的依赖关系



## 软件仓库

所谓软件仓库，包含两部分，第一部分就是所有的软件包（rpm），第二部分指的就是所有的软件包的元数据，元数据相当于所有软件包的名字和所有软件包的依赖关系。元数据文件远远小于整个仓库的文件大小。

### 配置本地软件仓库

todo

### 配置internet软件仓库

```bash
# 找到对应的镜像源的链接(在系统内的目录中)，如下时AppStream的url
https://mirrors.tuna.tsinghua.edu.cn/centos/8-stream/AppStream/x86_64/os/

# 配置url
cat > internet.repo << EOF
[appstream]
name=appstream
gpgcheck=0
enable=yes
baseurl=https://mirrors.tuna.tsinghua.edu.cn/centos/8-stream/AppStream/x86_64/os/
EOF

# 加载
yum repolist
yum makecache
```

