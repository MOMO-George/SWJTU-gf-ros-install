## 安装ubuntu操作顺序：

#### 1、制作启动盘iso（我自己有就不说细节了，可以私信我发你）

#### 2、提前划分好空闲区域给ubuntu，推荐使用Disk Genius专业版对重要资料进行备份，再用winPE的无损分盘进行空闲区域的划分，非常推荐这个ventoy他们家的这个U盘多个iso烧录，1盘多用，也很实用。

#### 3、如果进入U盘黑屏，首先将系统改为混显模式，再将启动盘自带驱动nouveau列入黑名单，启动的时候按e，___后面删除改为nomode。

#### 4、正常分区efi，snap，/，视觉用雷达就给200G，其他100G就够用。这里的安装有教程在相应文件夹里，建议swap虚拟内存设为32G/64G，这样跑点云不是很卡，看你们，都可以。

#### 5、装好重启后进入Ubuntu，先打开软件更新，更换下载源为阿里云，国内源都可以，并将旧驱动加入黑名单，让其自动屏蔽nouveau：

```bash
sudo gedit /etc/modprobe.d/blacklist.conf 
blacklist nouveau
sudo update-initramfs -u
```

#### 6、先把apt给升级了，还有把编译的基础东西都下了。

```bash
sudo apt update
sudo apt upgrade
sudo apt install build-essential #安装gcc、make、libglvnd-dev、pkg-config这四个依赖
```

#### 7、然后先把所有的nvidia的驱动都删了，然后在官网下载最新的。

```bash
dpkg --list | grep -i nvidia
sudo apt purge -y libnvidia* linux-objects-nvidia* screen-resolution-extra 
sudo apt autoremov
sudo apt autoclean 
sudo bash NVIDIA-Linux-x86_64-590.44.01.run #装新驱动
#注意：选NVIDIA的库，不要MIT，然后一路continue，全部yes就行。
nvidia-smi #重启后如果黑屏换独显，然后执行这条，应该是有显示显卡信息和cuda版本就成功了
```

#### 8、同步windows与linux系统的时间

```bash
sudo apt install ntpdate
sudo ntpdate time.windows.com
sudo hwclock --localtime --systohc 
#重启电脑去看看时间应该同步了。
```

#### 9、更改启动菜单默认项

```bash
sudo gedit /etc/default/grub
#将GRUB DEFAULT的值改为2，也就是第三行为我的window，你们按需修改。
sudo update-grub
```

#### 10、开始装其他软件

```bash
#我的建议是先把qq装了，目前wx没有linux，用qq来通信，好用一些，比如用qq下载好.deb或者.sh等文件直接传过来执行就好了，毕竟外网速度慢很多。
1、装QQ，便于通信使用。
2、装clash-verge，便于下载包。
3、microsoft-edge，便于找网站。
4、随便下软件，比如typora,miniconda,vscode,百度网盘,cuda等等
####下载比较难的软件我有写教程到文件夹中，请自便查取。
```

