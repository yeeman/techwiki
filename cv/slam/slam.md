SLAM问题的处理方法主要分为滤波和图优化两类。滤波的方法中常见的是扩展卡尔曼滤波、粒子滤波、信息滤波等，
熟悉滤波思想的同学应该容易知道这类SLAM问题是递增的、实时的处理数据并矫正机器人位姿。
比如基于粒子滤波的SLAM的处理思路是假设机器人知道当前时刻的位姿，利用编码器或者IMU之类的惯性导航又能够计算下一时刻的位姿，
然而这类传感器有累计误差，所以再将每个粒子的激光传感器数据或者图像特征对比当前建立好的地图中的特征，
挑选和地图特征匹配最好的粒子的位姿当做当前位姿，如此往复。
当然在gmapping、hector_slam这类算法中，不会如此轻易的使用激光数据，激光测距这么准，当然不能只用来计算粒子权重，
而是将激光数据与地图环境进行匹配（scan match）估计机器人位姿，比用编码器之流精度高出很多。

