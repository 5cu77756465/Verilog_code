ѧϰ�ʼ�
(����ѧϰ��վ��https://hdlbits.01xz.net/wiki/Main_Page)
wire ���������������ͣ�verilog�﷨�е�һ����Ҫ�������ͣ����ڱ�ʾ�������źţ���ʵ�ʵ�·�е��ź��������Ӧ��wire��verilog�е�Ĭ���������ͣ������е���������ź�û��ָ���������ͣ���Ĭ��Ϊwire�͡���wire�⣬����һ����Ҫ��������Ϊreg����ʾ�Ĵ����������ݡ�

z ������̬��verilog�У��źŹ���4��״̬"0��1��x��z"���ֱ��ʾ�͵�ƽ���ߵ�ƽ����ȷ��̬�͸���̬������û�н��г�ʼ�����źţ�һ�㴦�ڲ�ȷ��̬��x��������̬��ʾ���ź�û�б������ź����������������ж������Դ�������������ϡ�

4'bz :���ݸ�ʽ����ʾ���ź�Ϊ4bitλ��

ʱ���߼� ����·���м��书�ܣ���·״̬�����뵱ǰ�����йأ�����ǰһʱ�̵�״̬�йء�

ͬ���߼� ����ͬһ��ʱ���źż����¹��������ֻ��ʱ�ӵ������أ������½��أ������仯��

reg ����wire�����⣬����һ�ֳ��õ��������ͣ�һ���ʾ�Ĵ����������ݣ������������ԣ���סһ��ԭ����always���ڱ���ֵ���ź�Ӧ�����reg�ͣ���assign��丳ֵ���ź�Ӧ�����wire�͡�

always ����assign�⣬����һ��ʵ�ָ�ֵ�����Ĺؼ��֣����߶�����Ƕ�ף��������ڣ�assign���ֻ��ʵ������߼���ֵ����һ��assign������ֻ�ܸ�һ����ֵ���ʽ����always����ʵ������߼���ֵ������ʵ��ʱ���߼���ֵ�������ҿ��԰���������ֵ���ʽ��������ֵ���ʽ����Ӧλ��begin/end���м䡣

posedge ��verilog�ؼ��֣���ʾ�����ص���˼��Always@(posedge clk)��ʾ��clk�źŵ������ص�ʱ�̣�ִ��always���ڲ�����䣬������Ӧ�ģ��Ǳ�ʾ�½��صĹؼ���negedge�����Ǵ���posedge��negedge��always�飬���ᱻ�ۺϳ�ʱ���߼���·��

����/��������ֵ������"\<="���и�ֵ����䣬��Ϊ"��������ֵ"������"="���и�ֵ����䣬��Ϊ"������ֵ"����always���У�����ʽ��ֵ��ʽ���ִ�����Ⱥ�˳�򣬶���������ֵ�������ͬʱִ�С���ˣ���ʱ���߼���·�У����ָ�ֵ��ʽ���ܻ��ۺϳ���ͬ�ĵ�·�ṹ��

����ֻ���ס���¹���

i��������߼���·�У�ʹ������ʽ��ֵ��ʽ"="��

ii: ��ʱ���߼���·�У�ʹ�÷�����ʽ��ֵ��ʽ"\<="

iii����ͬһ��always���ڣ�ֻ�ܴ���һ�ָ�ֵ��ʽ��

iv��һ���źţ�ֻ����һ��always��һ��assign����¸�ֵ��

v��ԭ������˵��һ��always����ֻ����һ����һ���źţ���ͬ���źſ��ڲ�ͬ��always���ڴ���

vi: always����ֻ�ܶ�reg���źŽ��д������ܶ�wire�����ݸ�ֵ��Ҳ����ʵ����ģ��

ͬ����λ ����λֻ�ܷ�������clk�źŵ������أ���clk�źų������⣬���޷����и�λ��

If/else :always���г��õ������ж���䣬����Ƕ�ף������ȼ���һ����˵��Ӧ����λ�����߼����ڵ�һ��if����£�ʹ�������ߵ����ȼ��������ֻ����always����ʹ�á�����һ�ֱȽϳ��õ������ж������case����if/else��䲻ͬ��case��䲻�����ȼ�

�첽��λ ����always�����б����б��У�������posedge clk��clk�ź������أ� ��posedge reset��reset�ź��½��أ�����������ֻҪ��һ���������������ִ��always���ڵ��߼�����λ�����߼�Ӧ������ߵ����ȼ���

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

�����ҵ�һ�δ���
assign out[31:0] = {{24{in[7]}},in[7:0]};
�����assign out[31:0] = {24{in[7]},in[7:0]};���Ǵ���ģ����ԶԱ�һ�¡�

���ַ���
mod_a instance1 ( wa, wb, wc );
mod_a instance2 ( .out(wc), .in1(wa), .in2(wb) );

ȫ�����ı�λ�ͽ�λ���㷽��
Full adder equations:
sum = a ^ b ^ cin
cout = a&b | a&cin | b&cin

һλ��nλ����operateʱ����Ҫÿλ������
���ӣ�assign w = b^{32{sub}};
����32λb��һλsub���

