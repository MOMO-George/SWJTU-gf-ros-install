## 安装Cuda：

```bash
#先用nvidia-smi查看自己的最高cuda，一般低一点点就行，我目前最高13.1，安装12.9
sudo sh cuda.run
#全部accept，注意driver不要确认，按enter取消确认
nvcc -V
```
