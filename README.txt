学习笔记
(代码学习网站：https://hdlbits.01xz.net/wiki/Main_Page)
wire ：线网型数据类型，verilog语法中的一种主要数据类型，用于表示线网型信号，与实际电路中的信号连线相对应。wire是verilog中的默认数据类型，此例中的输入输出信号没有指定数据类型，则默认为wire型。除wire外，另外一种主要数据类型为reg，表示寄存器类型数据。

z ：高阻态，verilog中，信号共有4种状态"0、1、x、z"，分别表示低电平、高电平、不确定态和高阻态。对于没有进行初始化的信号，一般处于不确定态（x），高阻态表示该信号没有被其他信号驱动，经常用于有多个驱动源的总线型数据上。

4'bz :数据格式，表示该信号为4bit位宽

时序逻辑 ：电路具有记忆功能，电路状态不但与当前输入有关，还与前一时刻的状态有关。

同步逻辑 ：在同一的时钟信号激励下工作，输出只在时钟的上升沿（或者下降沿）发生变化。

reg ：除wire类型外，另外一种常用的数据类型，一般表示寄存器类型数据，不过并不绝对，记住一条原则：在always块内被赋值的信号应定义成reg型，用assign语句赋值的信号应定义成wire型。

always ：除assign外，另外一种实现赋值操作的关键字，两者都不可嵌套，区别在于，assign语句只能实现组合逻辑赋值，且一个assign语句后面只能跟一条赋值表达式。而always即能实现组合逻辑赋值，又能实现时序逻辑赋值操作，且可以包含多条赋值表达式，多条赋值表达式，则应位于begin/end对中间。

posedge ：verilog关键字，表示上升沿的意思。Always@(posedge clk)表示在clk信号的上升沿的时刻，执行always块内部的语句，与此相对应的，是表示下降沿的关键字negedge。凡是带有posedge或negedge的always块，都会被综合成时序逻辑电路。

阻塞/非阻塞赋值：采用"\<="进行赋值的语句，称为"非阻塞赋值"，采用"="进行赋值的语句，称为"阻塞赋值"。在always块中，阻塞式赋值方式语句执行有先后顺序，而非阻塞赋值语句则是同时执行。因此，在时序逻辑电路中，两种赋值方式可能或综合出不同的电路结构。

我们只需记住以下规则：

i：在组合逻辑电路中，使用阻塞式赋值方式"="；

ii: 在时序逻辑电路中，使用非阻塞式赋值方式"\<="

iii：在同一个always块内，只能存在一种赋值方式。

iv：一个信号，只能在一个always或一个assign语句下赋值。

v：原则上来说，一个always块内只处理一个或一类信号，不同的信号可在不同的always块内处理。

vi: always块内只能对reg型信号进行处理，不能对wire型数据赋值，也不能实例化模块

同步复位 ：复位只能发生在在clk信号的上升沿，若clk信号出现问题，则无法进行复位。

If/else :always块中常用的条件判断语句，可以嵌套，有优先级，一般来说，应将复位处理逻辑放在第一个if语句下，使其具有最高的优先级，该语句只能在always块内使用。另外一种比较常用的条件判断语句是case。与if/else语句不同，case语句不带优先级

异步复位 ：在always的敏感变量列表中，包含了posedge clk（clk信号上升沿） 和posedge reset（reset信号下降沿）两个条件，只要有一个条件发生，便会执行always块内的逻辑。复位处理逻辑应具有最高的优先级。

wire [2:0] a, c;   // Two vectors
assign a = 3'b101;  // a = 101
assign b = a;       // b =   1  implicitly-created wire
assign c = b;       // c = 001  <-- bug
my_module i1 (d,e); // d and e are implicitly one-bit wide if not declared.
                    // This could be a bug if the port was intended to be a vector.

{3'b111, 3'b000} => 6'b111000
{1'b1, 1'b0, 3'b101} => 5'b10101
{4'ha, 4'd10} => 8'b10101010     // 4'ha and 4'd10 are both 4'b1010 in binary

input [15:0] in;
output [23:0] out;
assign {out[7:0], out[15:8]} = in;         // Swap two bytes. Right side and left side are both 16-bit vectors.
assign out[15:0] = {in[7:0], in[15:8]};    // This is the same thing.
assign out = {in[7:0], in[15:8]};       // This is different. The 16-bit vector on the right is extended to
                                        // match the 24-bit vector on the left, so out[23:16] are zero.
                               // In the first two examples, out[23:16] are not assigned.


{5{1'b1}}           // 5'b11111 (or 5'd31 or 5'h1f)
{2{a,b,c}}          // The same as {a,b,c,a,b,c}
{3'd5, {2{3'd6}}}   // 9'b101_110_110. It's a concatenation of 101 with
                    // the second vector, which is two copies of 3'b110.

这是我的一段代码
assign out[31:0] = {{24{in[7]}},in[7:0]};
如果是assign out[31:0] = {24{in[7]},in[7:0]};则是错误的，可以对比一下。

两种方法
mod_a instance1 ( wa, wb, wc );
mod_a instance2 ( .out(wc), .in1(wa), .in2(wb) );

全加器的本位和进位计算方法
Full adder equations:
sum = a ^ b ^ cin
cout = a&b | a&cin | b&cin

一位和n位进行operate时，需要每位都进行
例子：assign w = b^{32{sub}};
这是32位b和一位sub异或

