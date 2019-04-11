# 一、计算机基础知识

## 1.1 计算机的基本常识

### 1.1.1 计算机的产生与发展

  计算机的产生是20世纪最重要的科学技术大事件之一。世界上的第一台计算机（ENIAC）于1946年诞生在美国宾夕法尼亚大学，到目前为止，计算机的发展大致经历了四代：

1. 第一代电子管计算机，始于1946年，结构上以CPU为中心，使用计算机语言，速度慢，存储量小，主要用于数值计算；
2. 第二代晶体管计算机，始于1958年，结构上以存储器为中心，使用高级语言，应用范围扩大到数据处理和工业控制；
3. 第三代中小规模集成电路计算机，始于1964年，结构上仍以存储器为中心，增加了多种外部设备，软件得到了一定的发展，文字图象处理功能加强；
4. 第四代大规模和超大规模集成电路计算机，始于1971年，应用更广泛，很多核心部件可集成在一个或多个芯片上，从而出现了微型计算机。

  我国从1956年开始电子计算机的科研和教学工作，1983年研制成功1亿/秒运算速度的“银河”巨型计算机，1992年11月研制成功10亿/秒运算速度的“银河II”巨型计算机，1997年研制了每秒130亿运算速度的“银河III”巨型计算机。目前计算机的发展向微型化和巨型化、多媒体化和网络化方向发展。计算机的通信产业已经成为新型的高科技产业。计算机网络的出现，改变了人们的工作方式、学习方式、思维方式和生活方式。

### 1.1.2 计算机系统组成

计算机系统由软件和硬件两部分组成。硬件即构成计算机的电子元器件；软件即程序和有关文档资料。

![img](./assets/computer-architecture.png)

到目前为止,电子计算机的工作原理均采用冯·诺依曼的存储程序方式,即把程序存储在计算机内,由计算机自动存取指令（计算机可执行的命令=操作码+操作数）并执行它。它包括：**控制器、运算器、存储器、输入设备、输出设备**五个部分。工作原理图如下：

![1554896746173](./assets/1554896746173.png)

**(1)  计算机的主要硬件**

- **输入设备**：键盘、鼠标、扫描仪等。

- **输出设备**：显示器、打印机、绘图仪等。

- **中央处理器**（CPU）：包括**控制器**和**运算器**，可以进行算术运算和逻辑运算；控制器是计算机的指挥系统，它的操作过程是取指令——分析指令——执行指令。

- **存储器**：具有记忆功能的物理器件，用于存储信息。存储器分为内存和外存。存储器的两个重要技术指标：存取速度和存储容量。内存的存取速度最快(与CPU速 度相匹配)，软盘存取速度最慢。存储容量是指存储的信息量，它用字节(Byte)作为基本单位，1字节用8位二进制数表示，1KB=1024B，1MB=1024KB，lGB=1024MB。

  ①内存是半导体存储器(主存）：它分为只读存储器(ROM)和随机存储器(RAM)和高速缓冲存储器（Cache)

  * ROM:只能读，不能用普通方法写入，通常由厂家生产时写入，写入后数据不容易丢失，也可以用特殊方法（如紫外线擦除（EPROM)或电擦除(EEPROM_)存储器)；

  * RAM:可读可写，断电后内容全部丢失；

  * Cache:因为CPU读写RAM的时间需要等待，为了减少等待时间，在RAM和CPU间需要设置高速缓存Cache,断电后其内容丢失。

  ②外存：磁性存储器——软盘和硬盘；光电存储器——光盘，它们可以作为永久存器。

**(2)计算机的软件**

  计算机的软件主要分为系统软件和应用软件两类：

  ①系统软件：为了使用和管理计算机的软件，主要有操作系统软件如，WINDOWS 95／98／ 2000／NT4.0、DOS 6.0、UNIX等；WINDOWS 95／98／2000／NT4.0是多任务可视化图形界面，而DOS是字符命令形式的单任务的操作系统。

  ②应用软件：为了某个应用目的而编写的软件，主要有辅助教学软件(CAI)、辅助设计软件(CAD)、文 字处理软件、工具软件以及其他的应用软件。

### 1.1.3 计算机中有关数及编码的知识

1. **计算机是智能化的电器设备**

     计算机就其本身来说是一个电器设备，为了能够快速存储、处理、传递信息，其内部采用了大量的电子元件，在这些电子元件中，电路的通和断、电压高低，这两种状态最容易实现，也最稳定、也最容易实现对电路本身的控制。我们将计算机所能表示这样的状态，用0，1来表示、即用二进制数表示计算机内部的所有运算和操作。

2. **二进制数的运算法则**

   由于二进制数运算非常简单，电器元件容易实现，所以计算机内部都用二进制编码进行数据的传送和计算。其主要法则是：

   `0+0=0 0+1=1 1+0=1 1+1=0   0*0=0 0*1=0 1*0=0 1*1=1`

3. **十进制与二进制、八进制、十六进制数之间的相互转换**

   (1)数的进制与基数

   计数的进制不同，则它们的基数也不相同，如下表所示：

   | 进制     | 基数                    | 特点       |
   | -------- | ----------------------- | ---------- |
   | 二进制   | 0 ,1                    | 逢二进一   |
   | 八进制   | 0,1,2,3,4,5,6,7         | 逢八进一   |
   | 十六进制 | 0,1,2,...,9,A,B,C,D,E,F | 逢十六进一 |
   | 十进制   | 0,1,2,3,4,5,6,7,8,9     | 逢十进一   |

   （2）数的权

   不同进制的数，基数不同，每位上代表的值的大小（权）也不相同。如：

   $$
   \begin{align}
   （219)10 &= 2*10^2 + 1*10^1 + 9*10^0\\
   （11010)2 &= 1*2^4+1*2^3+0*2^2+1*2^1+1*2^0\\
   （273)8 &= 2*8^2+7*8^1+3*8^0\\
   （27AF)16 &= 2*16^3+7*16^2+10*16^1+15*16^0\\
   \end{align}
   $$

   (3)十进制数转换任意进制

   - **整数转换**：将十进制整数除以所定的进制数,取余逆序。
      ` （39)10=(100111)2      (245)10=(365)8 `

   - **小数转换**：将十进制小数的小数部分乘以进制数取整,作为转换后的小数部分,直到为零或精确到小数点后几位。如：

     `（0.35)10=(0.01011)2        (0.125)10=(0.001)2`

     (4)任意进制的数转换十进制
     按权值展开, 如:
   $$
   \begin{align}
      （219)10 &= 2*10^2+1*10^1+9*10^0 \\
      （11010)2 &= 1*2^4+1*2^3+0*2^2+1*2^1+1*2^0 = 26 \\
      （273)8 &= 2*8^2+7*8^1+3*8^0 = 187 \\
       (7AF)16 &= 7*16^2+10*16^1+15*16^0 = 1867 \\
     \end{align}
   $$

4. **定点数与浮点数**
      定点数是指数据中的小数点位置固定不变。由于它受到字长范围的限制，所能表示的数的范围有限，计算结果容易溢出。浮点数的形式可写成：

   $$
   N = M*2^E
   $$

    (其中M代表尾数,E代表阶码）其形式如下：

   ![1554945273894](./assets/1554945273894.png)

   

5. **ASCII编码**
       由于计算机是电器设备，计算机内部用二进制数，这样对于从外部输入给计算机的所有信息必须用二进制数表示,并且对于各种命令、字符等都需要转换二进制数，这样就牵涉到信息符号转换成二进制数所采用的编码的问题，国际上统一用美国标准信息编码（ASCII）它可用7位二进制数表示，存储时用一个字节，它的最高位为0。因此基本的ASCII字符集有128个如:

   | 字符 | ASCII值 | 二进制编码   |
   | ---- | ------- | ------------ |
   | 0-9  | 48-57   | 00110000-... |
   | A-Z  | 65-90   | 01000001-... |
   | a-z  | 97-122  | 01100000-... |

   **ASCII编码如下：（ASCII中的0~31为控制字符；32~126为可显示字符；127为Delete(删除)命令）**

   | **ASCII值** | **控制字符** | **ASCII值** | **控制字符** | **ASCII值** | **控制字符** | **ASCII值** | **控制字符** |
   | ----------- | ------------ | ----------- | ------------ | ----------- | ------------ | ----------- | ------------ |
   | 0           | NUL          | 32          | (space)      | 64          | @            | 96          | 、           |
   | 1           | SOH          | 33          | ！           | 65          | A            | 97          | a            |
   | 2           | STX          | 34          | ”            | 66          | B            | 98          | b            |
   | 3           | ETX          | 35          | #            | 67          | C            | 99          | c            |
   | 4           | EOT          | 36          | $            | 68          | D            | 100         | d            |
   | 5           | ENQ          | 37          | %            | 69          | E            | 101         | e            |
   | 6           | ACK          | 38          | &            | 70          | F            | 102         | f            |
   | 7           | BEL          | 39          | '            | 71          | G            | 103         | g            |
   | 8           | BS           | 40          | (            | 72          | H            | 104         | h            |
   | 9           | HT           | 41          | )            | 73          | I            | 105         | i            |
   | 10          | LF           | 42          | *            | 74          | J            | 106         | j            |
   | 11          | VT           | 43          | +            | 75          | K            | 107         | k            |
   | 12          | FF           | 44          | ,            | 76          | L            | 108         | l            |
   | 13          | CR           | 45          | -            | 77          | M            | 109         | m            |
   | 14          | SO           | 46          | .            | 78          | N            | 110         | n            |
   | 15          | SI           | 47          | /            | 79          | O            | 111         | o            |
   | 16          | DLE          | 48          | 0            | 80          | P            | 112         | p            |
   | 17          | DCI          | 49          | 1            | 81          | Q            | 113         | q            |
   | 18          | DC2          | 50          | 2            | 82          | R            | 114         | r            |
   | 19          | DC3          | 51          | 3            | 83          | X            | 115         | s            |
   | 20          | DC4          | 52          | 4            | 84          | T            | 116         | t            |
   | 21          | NAK          | 53          | 5            | 85          | U            | 117         | u            |
   | 22          | SYN          | 54          | 6            | 86          | V            | 118         | v            |
   | 23          | TB           | 55          | 7            | 87          | W            | 119         | w            |
   | 24          | CAN          | 56          | 8            | 88          | X            | 120         | x            |
   | 25          | EM           | 57          | 9            | 89          | Y            | 121         | y            |
   | 26          | SUB          | 58          | :            | 90          | Z            | 122         | z            |
   | 27          | ESC          | 59          | ;            | 91          | [            | 123         | {            |
   | 28          | FS           | 60          | <            | 92          | \            | 124         | \|           |
   | 29          | GS           | 61          | =            | 93          | ]            | 125         | }            |
   | 30          | RS           | 62          | >            | 94          | ^            | 126         | ~            |
   | 31          | US           | 63          | ?            | 95          | —            | 127         | DEL          |

**下表为控制字符释义。**

| **十进制** | **十六进制** | **字符意义**  | **十进制** | **十六进制** | **字符**意义 |
| ---------- | ------------ | ------------- | ---------- | ------------ | ------------ |
| 0          | 00           | 空            | 16         | 10           | 数据链路转意 |
| 1          | 01           | 头标开始      | 17         | 11           | 设备控制 1   |
| 2          | 02           | 正文开始      | 18         | 12           | 设备控制 2   |
| 3          | 03           | 正文结束      | 19         | 13           | 设备控制 3   |
| 4          | 04           | 传输结束      | 20         | 14           | 设备控制 4   |
| 5          | 05           | 查询          | 21         | 15           | 反确认       |
| 6          | 06           | 确认          | 22         | 16           | 同步空闲     |
| 7          | 07           | 震铃          | 23         | 17           | 传输块结束   |
| 8          | 08           | backspace     | 24         | 18           | 取消         |
| 9          | 09           | 水平制表符    | 25         | 19           | 媒体结束     |
| 10         | 0A           | **换行/新行** | 26         | 1A           | 替换         |
| 11         | 0B           | 竖直制表符    | 27         | 1B           | 转意         |
| 12         | 0C           | 换页/新页     | 28         | 1C           | 文件分隔符   |
| 13         | 0D           | **回车**      | 29         | 1D           | 组分隔符     |
| 14         | 0E           | 移出          | 30         | 1E           | 记录分隔符   |
| 15         | 0F           | 移入          | 31         | 1F           | 单元分隔符   |

6. 汉字编码与汉字输入法

   （1）机内码
       ASCII码不能表示汉字，因此要有汉字信息交换码，我国国家标准是GB2312，它也被称作国际码。它由两个字节组成，两个字节的最高位都为1。GB2312共收纳6763个汉字，其中，一级汉字（常用字）3755个按汉字拼音字母顺序排列，二级汉字3008个按部首笔画次序排列。
   （2）汉字输入码（外码）
       目前，汉字输入法主要有键盘输入、文字识别和语音识别。键盘输入法是当前汉字输入的主要方法。它大体可以分为：

   - 流水码：如区位码、电报码、通信密码，优点重码律少，缺点难于记忆；

   - 音码：以汉语拼音为基准输入汉字，优点是容易掌握，但重码律高；

   - 形码：根据汉字的字型进行编码，优点重码少，但不容易掌握；

   - 音形码：将音码和形码结合起来，能减少重码律同时提高汉字输入速度。

   （3）汉字字模
       供计算机输出汉字（显示和打印）用的二进制信息叫汉字字形信息也称字模。通用汉字字模点阵规格有16×16，24×24，32×32，48×48，64×64，每个点在存储器中用一个二进制位(bit)存储，如一个16×16点阵汉字需要32个字节的存储空间。

### 1.1.4 原码、反码与补码

   
