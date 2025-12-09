## 安装Issac的SIM和LAB：

```bash
#22.04可以pip下SIM，20.04的就老实地去给我下源码
#我的是16G内存和6G显存，3060，跑得老慢了，但也能用。
#先把SIM的源码包下完
cd Isaac/isaac-sim/
./post_install.sh 
./isaac-sim.selector.sh 
#选择直接Start，包卡的，耐心多等一会儿。
#下一步，安装LAB
cd ..
git clone https://github.com/isaac-sim/IsaacLab.git
#最恶心的就是他说支持SIM4.5，然后出现下面这个报错，就因为这个是更新的包
ModuleNotFoundError: No module named 'omni.metrics'
#但有大佬解答了，说是可以直接回到以前的可以运行的版本
git reset --hard 7e2aba2
#这个原链接：https://github.com/isaac-sim/IsaacLab/issues/4057
conda create -n robo python=3.10
conda activate robo
cd IsaacLab/
ln -s ../isaac-sim/ _isaac_sim #创建符号链接，说白了就是快捷方式
./isaaclab.sh -i #开装，十分漫长，挂着把
#装好了就可以开始测试了，随便跑应该都没啥问题，成功安装，祝你好运，RCer。
```
