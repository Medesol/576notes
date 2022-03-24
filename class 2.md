# Aquisition and Basics
- real world is **pysical**
- multimedia is **digital**

## Digital Aquisition
camera
1. light
2. analog signal (continuous) through sampling(采样) and quantization(量化) becomes
3. digital signal (discrete)

### 采样

每T时间对信号采样，得到信号相应的  值

### 量化

对采样后的值进行零一量化，得到相应的比特值

用b bits, 假设range是R，$max Error = \frac{1}{2}(\frac{R}{2^b-1})$

### 比特率

bitrate = bit/sec = bit/sample \* sample/sec = Q \* F

### LTI(Linear Time Invariant)
Linear: $f(ax_1+bx_2) = af(x_1)+bf(x_2)$

### What should T and b be?

b: 直到人类分不出区别
T: should be at least 2\*max frequency of the signal
max frequency 由傅立叶变换后最大的非0参数的频率决定，由人类可观测最大频率决定

### 电视和摄像机同步

电流频率，所以NTSC是30fps
interlated scanning：隔行扫描，先扫奇数行，然后扫偶数行，解决flikering

YUV subsampling


