# document
1、2接口是DSP的Jtag接口，3是FPGA的jtag接口； 4是LVDS接口

![Image](https://github.com/19801201/Image/blob/main/tup.jpg)

![Image](https://github.com/19801201/Image/blob/main/kuangjia.png)

整体的架构如上所示：从相机接收的数据首先通过软协议转化为LVDS的物理层协议，然后通过板卡中的模块转化部分转化为可以用于FPGA的数据形式。
经过Img对传入的数据预处理之后，就可以通过AXI总线传入到FPGA中进行前向推理。推理结果需要与DSP进行交互，DSP可以当作PC端控制FPGA并且和FPGA进行数据交换。




![Image](https://github.com/19801201/Image/blob/main/new.png)

Dsp 的主要作用：1、读写DDR，2、读写reg，3、响应FPGA的发起信号
如上图所示：User_app 作为控制FIFO的逻辑，Srio_Control作为控制SRIO_Ip的逻辑，两者需要进行交互，SRIO_IP 通过SRIO接口与DSP 
进行数据交互，包括接收从FPGA传来的数据，以及向FPGA中写数据（写DDR和REG）该阶段包括写指令，写权重以及写图像数据
DSP在整个工程中的作用与上位机类似，起到接收数据，控制FPGA的读写


![Image](https://github.com/19801201/Image/blob/main/old.png)
之前的工程主要使用PCIE连接PC 和FPGA
