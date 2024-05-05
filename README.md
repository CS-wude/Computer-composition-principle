# 计算机组成原理 #
1.1 计算机系统简介  
1.1.1 计算机软硬件概念  
硬件：计算机的实体，如主机、外设  
软件：具有各类特殊功能的信息（程序）组成。软件又分为系统软件和应用软件。系统软件用来管理整个计算机系统，应用软件按任务需要编制成的各种程序。  
高级语言程序在计算机中翻译成目标程序后运行得到结果从计算机输出。  
1.1.2 计算机系统的层次结构  
微程序机器M0（微指令系统）、实际机器M1（机器语言）、虚拟机器（操作系统）、虚拟机器M2（汇编语言）、虚拟机器M3（高级语言）  
操作系统是软件和硬件的分界。  
1.1.3 计算机体系结构和计算机组成  
计算机体系结构：程序员所见到的计算机系统的属性，概念性的结构与功能特性。（指令系统、数据类型、寻址技术、I/O机理）  
计算机组成：主要指机器语言级机器的系统结构，实现计算机体系结构所体现的属性。（具体指令的实现）  
计算机体系结构关注的是有无乘法指令这一类，计算机组成原理关注的是如何实现乘法指令这一类。  
现在很多微处理器产品，他们的系统机体系结构相同，但组成不同。  
1.2 计算机的基本组成  
1.2.1 冯诺依曼计算机的特点：  
（1）计算机由五大部件组成，运算器，存储器，控制器，输入设备，输出设备。  
（2）指令和数据以同等地位存于存储器中，可按地址寻访。  
（3）指令和数据都按二进制代码表示。  
（4）指令由操作码和地址码组成。  
（5）存储程序。  
（6）以运算器为中心。  
1.2.2 计算机硬件  
运算器ALU和控制器CU组成CPU，存储器由主存和辅存组成，主存和CPU构成主机，输入设备和输出设备组成I/O，以上组成硬件。  
1.2.3 计算机的工作步骤  
程序指运算的全部步骤，指令指每一个步骤。  
之前说过指令由操作码和地址码组成，指令又是二进制代码表示，举例：取数的操作码是000001，a的地址码为0000001000，则这条指令组成0000010000001000，它表达的意思是[a] -> ACC,如果操作码是存数，那就是[ACC] -> a，以此类推加减乘除还有打印等操作。  
运算器中有ACC、MQ、ALU、X  
主存储器中有存储体、MAR、MDR  
存储体好比大楼，存储单元则是房间，存储元件（0/1）则是床位。存储单元存放一串二进制代码，存储字是存储单元中二进制代码的组合，存储字长是存储单元中二进制代码的位数，按地址寻访，每个存储单元赋予一个地址号。  
存储器的基本组成：MAR（存储器地址寄存器反应存储单元的个数），MDR（存储器数据寄存器反应存储字长）。设MAR=4位，MDR=8位，则存储单元个数等于2的4次方，16个，存储字长为8.  
控制器里有CU、IR、PC，完成一条指令需要进行取指令（PC）和分析指令（IR），这属于取指，还有执行指令（CU），这属于执行指令，他们都需要访存。PC存放当前欲执行的指令的地址，具有计数功能（PC）+1->PC，IR存放当前欲执行的指令。  
主机完成一条指令的过程（取数指令）：PC->MAR,MAR->存储体,存储体->MDR,MDR->IR,IR->CU,IR->MAR,MAR->存储体,存储体->MDR,MDR->ACC  
主机完成一条指令的过程（存数指令）：PC->MAR,MAR->存储体，存储体->MDR,MDR->IR,IR->MAR,MAR->存储体,ACC->MDR,MDR->存储体  
1.3 计算机硬件的主要技术指标  
（1）机器字长：CPU一次能处理的数据的位数与CPU中的寄存器位数有关。  
（2）运算速度：主频、吉普森法、MIPS每秒执行百万条指令、CPI执行一条指令所需的时钟周期数、FLOPS每秒浮点运算次数。  
（3）存储容量：存放二进制信息的总数量。存储容量分为主存容量（存储单元个数x存储字长）和辅存容量。  
  
2 计算机的发展及应用  
第一代（1946~1957） 硬件技术：电子管  
第二代（1958~1964） 硬件技术：晶体管  
第三代（1965~1971） 硬件技术：中小规模集成电路  
第四代（1972~1977） 硬件技术：大规模集成电路  
第五代（1978~现在）  硬件技术：超大规模集成电路  
  
3 系统总线  
3.1 总线的基本概念  
早起的计算机多数以运算器为中心，采用分散连接的方式。缺点是内部连接复杂，I/O与存储器交换信息要通过运算器，影响CPU工作效率。  
改进为存储器为中心的分散连接方式。优点是采用了中断、DMA等技术，CPU的工作效率得到提高。缺点是无法解决I/O设备与主存之间连接的灵活性。  
总线：是连接各个部件的信息传输线，是各个部件共享的传输介质。  
总线的分类：按数据传输方式可分为串行传输总线和并行传输总线。按总线的使用范围可分为计算机总线、测控总线、网络通信总线等。按连接部件的不同可分为片内总线、系统总线、通信总线。  
3.2 总线的分类  
（1）片内总线是CPU芯片内部的总线。  
（2）系统总线是计算机部件间的信息传输线。分为数据总线（双向，与机器字长、存储字长有关），地址总线（单向，与存储地址、I/O地址有关），控制总线（有出：存储器读写，总线允许，中断确认、有入：中断请求，总线请求）  
（3）通信总线是用于计算机系统之间或计算机系统与其他系统之间的通信，传输方式为串行通信总线和并行通信总线。  
3.3 总线的特性与性能  
总线的特性：机械特性（管脚数）、电气特性（电平）、功能特性（地址、数据、控制）、时间特性（时序）  
总线的性能指标：总线宽度（数据线的根数）、标准传输率（每秒传输的最大字节数例如MB/s）、时钟同步/异步、信号线数（地址线、数据线、控制线的总和）、总线的控制方式（并发、自动、仲裁、逻辑、计数）、负载能力  
还可以了解一下总线标准。  
3.4 总线结构  
（1）单总线结构，特点是结构简单、便于扩充，所有传输都通过这组共享总线。  
多总线结构：  
（2）双总线结构，特点是速度较低的I/O设备从单总线上分离出来，形成主存总线和I/O总线分开的结构。  
（3）三总线结构，特点是主存总线用于CPU与主存之间的传输，I/O总线提供CPU与各类I/O设备之间传递信息，DMA总线用于高速I/O设备与主存之间交换信息。这种三总线结构中，任何一时刻都只能使用一个。
（4）。。。  
3.5 总线控制  
3.5.1 总线判优控制（仲裁控制）  
（1）基本概念：主设备（模块）对总线有控制权，从设备（模块）响应从主设备发来的总线命令。总线判优控制分为集中式（链式查询、计数器定时查询、独立请求方式）和分布式。BS-总线忙 | BR-总线请求 | BG-总线同意  
（2）链式查询方式，特点是只需要很少的几根线就能按一定优先次序实现总线的控制，并且很容易扩充设备，但对电路故障很敏感，优先级别低的设备很难获取。
（3）计数器定时查询方式，特点是可以从0开始，设备的优先级递增顺序降序排列，计数器可以从上次计数的终止点开始，此时优先级相等；可以改变计数器的初始值改变优先级次序，这种方式对电路故障不如链式查询敏感，但增加了控制线数量，使得控制变得复杂。  
（4）独立请求方式，特点是响应速度快，优先次序控制灵活，即可通过程序改变优先次序，但控制线数量很多，总线控制更复杂。  
3.5.2 总线通信控制  
（1）目的：解决通信双方协调配合的问题。  
（2）总线传输周期，CPU完成一次访问MEM或I/O端口操作的时间。一个总线周期由几个时钟周期组成。分为:申请分配阶段（主模块申请，总线仲裁判定），寻址阶段（主模块向从模块给出地址和命令），传数阶段（主模块和从模块交换数据），结束阶段（主模块撤销有关信息）。  
（3）总线通信的四种方式：  
1、同步通信（由统一时标控制数据传送）：优点是规定明确统一，模块间配合简单一致。缺点是主、从模块间时间配合属于强制性同步。  
2、异步通信（采用应答方式，即握手方式，没有公共时钟标准）：优点是克服了同步通信的缺点，允许各模块速度不一致。应答方式又可分为不互锁、半互锁、全互锁三种。  
3、半同步通信（同步、异步结合）：同步部分，发送方用系统时钟前沿发信号，接收方用时钟后沿判断识别。异步部分，允许不同速度的模块和谐工作，增加一条“等待”响应信号wait。  
4、以上三种通信的共同点：一个时钟传输周期以输入数据为例，主模块发送地址、命令占用总线，从模块准备数据，不占用总线总线空间，从模块向主模块发数据占用总线  
5、分离式通信（充分挖掘系统总线每瞬间的潜力）  

----------------------  
5 输入与输出系统
5.1 概述
I/O与主机的联系方式：
（1）I/O编址方式：统一编址（用取数、存数指令），不统一编址（有专门的i/o指令）
（2）设备选址：用设备选择电路识别是否被选中
（3）传送方式：串行、并行
（4）联络方式：立即响应、异步工作采用应答信号、同步工作采用同步时标
（5）I/O与主机的连接方式：辐射式连接（每台设备都有一套控制路和一组信号线，不便于增删设备）、总线连接（便于增删设备）
信息传输控制：
（1）程序查询方式：CPU和I/O串行工作，踏步等待。
（2）程序中断方式：I/O工作中，自身准备阶段CPU不查询，与主机交换信息阶段CPU暂停现行程序，CPU与I/O并行工作，没有踏步等待现象，中断现行程序。
（3）DMA方式：主机和I/O之间有一条直接数据通道，不中断现行程序，进行周期挪用（周期窃取），CPU和I/O并行工作。
5.2 外部设备
外部设备大致分为三类：人机交互设备（键盘、鼠标、打印机、显示器等）、计算机信息驻留设备（磁盘等）、机-机通信设备（调制解调器等）
打印机是输出设备
5.3 I/O接口
（1）总线连接方式的I/O接口电路包含设备选择线、数据线、命令线、状态线
（2）接口的功能和组成
功能                组成
选址功能            设备选择电路
传送命令的功能      命令寄存器、命令译码器
传输数据的功能      数据缓冲寄存器
反映设备状态的功能  设备状态标记
（完成触发器D、工作触发器B、中断请求触发器INTR、屏蔽触发器MASK）
接口类型：
（1）按数据传送方式分类：串行接口、并行接口
（2）按功能选择的灵活性分类：可编程接口、不可编程接口
（3）按通用性分类：通用接口、专用接口
（4）按数据传输的控制方式分类：中断接口、DMA接口
5.4 程序查询方式
5.5 程序中断方式
所谓中断是出现异常情况或特殊请求时，计算机暂停现行程序运行，转而处理这些异常情况或特殊请求，处理结束后再返回到现行程序的间断出（断点），继续执行原程序。
接口电路：
（1）中断源配置中断请求（INTR中断请求触发器，INTR=1表示有请求，MASK中断屏蔽触发器，MASK=1表示被屏蔽，D完成触发器）
（2）排队器：硬件（在CPU内、在接口电路中，链式排队器）、软件
（3）中断向量地址形成部件：入口地址可由软件产生，也可硬件向量法（由硬件产生向量地址，再由向量地址找到入口地址）
（4）程序中断方式接口电路的基本组成
I/O中断处理过程：
（1）CPU响应中断的条件和时间：
条件：允许中断触发器EINT=1，用开中断指令置“1”EINT，用关中断指令置“0”EINT或硬件自动复位。
时间：当D=1且MASK=0时，在每条指令执行阶段结束前，CPU发送中断查询信号（将INTR置“1”）
（2）I/O中断处理过程：启动命令，启动设备，输入数据，设备工作结束，向INTR输入中断查询，INTR发出中断请求，中断响应INTA输入设备编码器，设备编码器输出向量地址。
中断服务程序流程：保护现场（由中断隐指令完成程序断点的保护，进栈指令完成寄存器内容的保护）、中断服务（对不同I/O设备具有不同内容的设备服务）、恢复现场（出栈指令）、中断返回（中断返回指令）。
有关中断的几点说明：CPU一旦响应了某中断源的中断请求后，便由硬件线路自动关中断，即中断允许触发器EINT被置“0”；程序中断方式克服了程序查询方式中的CPU“踏步”现象，实现了CPU与I/O的并行工作，提高了CPU的资源利用率。
单重中断和多重中断：单重中断不允许中断现行的中断服务程序，多重中断允许级别更高的中断源，中断现行的中断服务程序。
单重中断的开中断在中断返回时，多重中断则提前到了中断返回之前。
中断周期包含了中断响应，程序断点进栈，关中断，向量地址->PC
宏观上CPU和I/O并行工作，微观上CPU中断现行程序为I/O服务。
5.6 DMA方式
DMA方式与主存交换数据的三种方法：


7 指令系统  
7.1 机器指令  
一般格式：操作码字段+地址码字段  
操作码：长度固定，用于指令字长较长的情况。长度可变，操作码分散在指令的不同字段中。拓展操作码技术，操作码的位数随地址数的减少而增加。  
地址码：先不管四地址还是三二一零地址，一条指令是（A1）OP（A2）->A3，其中A是可以变成不同或者相同的，那就需要取两次操作数地址和一次OP，还有存一次结果，即4次访存。如果里面A换成了ACC这类寄存器，那还一个位置不管是存还是取都减一次访存，比如一地址情况，只有OP和A1那这个指令是（ACC）OP（A1）->ACC的话，就是两次访存。  
指令字长决定于操作码长度，操作数地址长度，操作数地址个数。指令字长是固定的（指令字长=存储字长），指令字长是可变的（按字节的倍数变化）。  
当用一些硬件资源替代指令中的地址码字段后，可扩大指令的寻址范围，可缩短指令字长，可减小访存次数。  
操作数类型：地址、数字、字符、逻辑数  
数据在存储器中的存放方式：字地址为低字节（0在右边），字地址为高字节（0在左边）  
操作类型：数据传送（MOVE、LOAD、STORE、POP、PUSH、）、算术逻辑操作（ADD、SUB、）、移位操作、转移（JMP、SKP、）、输入输出（OUT、）、其他  
7.3 寻址方式  
寻址方式：确定本条指令的操作数地址以及下一条欲执行指令的指令地址。寻址方式有指令寻址和数据寻址。  
7.3.1 指令寻址：顺序、跳跃  
7.3.2 数据寻址：操作码+寻址特征+形式地址A（形式地址是指令字中的地址，有效地址是操作数的真实地址，约定指令字长=存储字长=机器字长）  
（1）立即寻址：形式地址A就是操作数指令执行阶段不访存，立即数A可正可负为补码，A的位数限制了立即数的范围。  
（2）直接寻址：EA=A 有效地址由形式地址直接给出，执行阶段访问一次存储器，A的位数决定了该指令操作数的寻址访问，操作数的地址不易修改，必须改A。  
（3）隐含寻址：操作数地址隐含在操作码中，指令字少了一个地址字段，可缩短指令字长。  
（4）间接寻址：EA=(A)，有效地址由形式地址间接提供，一次间接寻址，执行指令阶段2次访存，可扩大寻址范围。还可以多次间接寻址。  
（5）寄存器寻址：EA=Ri，有效地址即为寄存器编号。执行阶段不访存，只访问寄存器，执行速度快。寄存器个数有限，可缩短指令字长。  
（6）寄存器间接寻址：EA=(Ri)，有效地址在寄存器，操作数在存储器中，执行阶段访存便于编制循环程序。  
（7）基址寻址：采用专用寄存器作基址寄存器，（也可以采用通用寄存器作为基址寄存器），EA=(BR)+A，可扩大寻址范围，便于程序搬家，执行过程中BR不变，变A。  
（8）变址寻址：EA=(IX)+A，采用专用寄存器作变址寄存器，通用寄存器也可以作为变址寄存器，IX内容可变，A不变，便于处理数组问题。
（9）相对寻址：EA=(PC)+A，A是相对当前指令的位移量（可正可负，补码），A的位数决定了操作数的寻址范围，程序浮动，广泛用于转移指令。  
（10）堆栈寻址：堆栈分为硬堆栈（多个寄存器，也称为串联堆栈）和软堆栈（指定的存储空间，也称为存储器堆栈），先进后出，栈顶地址由SP指出，进栈（SP）-1，出栈（SP）+1。  
这里SP的修改与主存编址方法有关，按字编址SP加减1，按字节编址，如果存储字长为16位则SP加减2，32位则加减4。  
7.4 指令格式举例  
设计指令格式时考虑的各种因素：1.指令系统的兼容性（向上兼容）。2.其他因素  
7.5 RISC技术  
RISC的主要特征：  
1、选用使用频率较高的一些简单指令，复杂指令的功能由简单指令来组合。  
2、指令的长度固定，指令格式种类少，寻址方式少。  
3、只有LOAD/STORE指令访存，  
4、采用流水技术，一时钟周期内完成一条指令。  
5、采用组合逻辑实现控制器。  
6、CPU中有多个通用寄存器。  
7、采用优化的编址程序。  
RISC和CISC比较  
与CISC相比RISC机的主要优点有更能充分使用VLSI芯片的面积，更能充分提高计算机运算速度，便于设计，可降低成本，提高可靠性，有效支持高级语言程序，有利于编址程序代码优化。  
相比于CISC，RISC机能提高运算速度主要反应在以下5个方面：RISC的指令数、指令格式和寻址方式的种类较少，而且指令的编码很有规律，因此RISC的指令译码比CISC的指令译码快。RISC机内通用寄存器多，减少了访存次数，可加快运行速度。RISC机采用寄存器窗口重叠技术。RISC机采用组合逻辑控制，比采用微程序控制的CISC机的延迟小，缩短了CPU的周期。RISC机选用精简指令系统，适合于流水线工作。
