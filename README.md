# document
1、2接口是DSP的Jtag接口，3是FPGA的jtag接口； 4是LVDS接口

![Image](https://github.com/19801201/Image/blob/main/tup.jpg)

![Image](https://github.com/19801201/Image/blob/main/kuangjia.png)

整体的架构如上所示：从相机接收的数据首先通过软协议转化为LVDS的物理层协议，然后通过板卡中的模块转化部分转化为可以用于FPGA的数据形式。
经过Img对传入的数据预处理之后，就可以通过AXI总线传入到FPGA中进行前向推理。推理结果需要与DSP进行交互，DSP可以当作PC端控制FPGA并且和FPGA进行数据交换。
