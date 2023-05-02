Download Link: https://assignmentchef.com/product/solved-coa-lab-2-single-cycle-cpu
<br>
Utilizing the ALU in Lab1 to implement a simple single cycle CPU. CPU is the most important unit in computer system. Read the document carefully and do the Lab, and you will have the elementary knowledge of CPU.

2.     Requirement

<ul>

 <li>Please use Icarus Verilog and GTKWave as your HDL simulator.</li>

 <li>Please attach your names and student IDs as comment at the top of each file.</li>

 <li>Please use the Program Counter, Instruction Memory, Register File and Test Bench we provide you.</li>

 <li>Instruction set: the following instructions are to run on your CPU (60 pts.).</li>

</ul>







<table width="529">

 <tbody>

  <tr>

   <td width="108"><strong>Instruction </strong></td>

   <td width="123"><strong>Example </strong></td>

   <td width="142"><strong>Meaning </strong></td>

   <td width="78"><strong>Opcode </strong></td>

   <td width="78"><strong>Function </strong></td>

  </tr>

  <tr>

   <td width="108">Add unsigned</td>

   <td width="123">addu r1, r2, r3</td>

   <td width="142">r1 = r2 + r3</td>

   <td width="78">000 000</td>

   <td width="78">100 001</td>

  </tr>

  <tr>

   <td width="108">Add immediate</td>

   <td width="123">addi r1, r2, 100</td>

   <td width="142">r1 = r2 +100</td>

   <td width="78">001 000</td>

   <td width="78">–</td>

  </tr>

  <tr>

   <td width="108">Subtract unsigned</td>

   <td width="123">subu r1, r2, r3</td>

   <td width="142">r1 = r2 – r3</td>

   <td width="78">000 000</td>

   <td width="78">100 011</td>

  </tr>

  <tr>

   <td width="108">Bitwise and</td>

   <td width="123">and r1, r2, r3</td>

   <td width="142">r1 = r2 &amp; r3</td>

   <td width="78">000 000</td>

   <td width="78">100 100</td>

  </tr>

  <tr>

   <td width="108">Bitwise or</td>

   <td width="123">or r1, r2, r3</td>

   <td width="142">r1 = r2 | r3</td>

   <td width="78">000 000</td>

   <td width="78">100 101</td>

  </tr>

  <tr>

   <td width="108">Set on less than</td>

   <td width="123">slt r1, r2, r3</td>

   <td width="142">if( r2 &lt; r3 )    r1 = 1 else   r1 = 0</td>

   <td width="78">000 000</td>

   <td width="78">101 010</td>

  </tr>

  <tr>

   <td width="108">Set on  less than  immediate unsigned</td>

   <td width="123">sltiu r1, r2, 10</td>

   <td width="142">if( r2 &lt; 10 )   r1 = 1 else   r1 = 0</td>

   <td width="78">001 011</td>

   <td width="78">–</td>

  </tr>

  <tr>

   <td width="108">Branch  on equal</td>

   <td width="123">beq r1, r2, 25</td>

   <td width="142">if( r1 == r2 )PC += (25 &lt;&lt; 2)</td>

   <td width="78">000 100</td>

   <td width="78">–</td>

  </tr>

 </tbody>

</table>




<h1>3.     Architecture Diagram</h1>

<h1>4.     Advance Instructions</h1>

Modify the architecture of the basic design above.

<ul>

 <li>ALUOp should be extended to 3bits to implement I-type instructions. Original 2bits ALUOp from textbook : 00 -&gt; 000, 01 -&gt; 001, 10 -&gt; 010.</li>

 <li>Encode shift right and LUI instruction by using unused ALU_ctrl.</li>

</ul>

Ex. ALU_ctrl = 0 is AND, 1 is OR…, 0 1 2 6 7 &amp;12 are used by basic instructions.




<table width="529">

 <tbody>

  <tr>

   <td width="108"><strong>Instruction </strong></td>

   <td width="123"><strong>Example </strong></td>

   <td width="142"><strong>Meaning </strong></td>

   <td width="78"><strong>Opcode </strong></td>

   <td width="78"><strong>Function </strong></td>

  </tr>

  <tr>

   <td width="108">Shift         rightarithmetic</td>

   <td width="123">sra r1, r2, 10</td>

   <td width="142">r1 = r2 &gt;&gt; 10</td>

   <td width="78">000 000</td>

   <td width="78">000 011</td>

  </tr>

  <tr>

   <td width="108">Shift    right arithmetic variable</td>

   <td width="123">srav r1, r2, r3</td>

   <td width="142">r1 = r2 &gt;&gt; r3</td>

   <td width="78">000 000</td>

   <td width="78">000 111</td>

  </tr>

  <tr>

   <td width="108">Load    upper immediate</td>

   <td width="123">lui r1, 10</td>

   <td width="142">r1 = 10 &lt;&lt; 16</td>

   <td width="78">001 111</td>

   <td width="78">–</td>

  </tr>

  <tr>

   <td width="108">Or immediate</td>

   <td width="123">ori r1, r2, 100</td>

   <td width="142">r1 = r2 | 100</td>

   <td width="78">001 101</td>

   <td width="78">–</td>

  </tr>

  <tr>

   <td width="108">Branch on not equal</td>

   <td width="123">bne r1, r2, 30</td>

   <td width="142">if( r1 != r2 )PC += (30 &lt;&lt; 2)</td>

   <td width="78">000 101</td>

   <td width="78">–</td>

  </tr>

 </tbody>

</table>







To implement those advanced instructions, please note about the following formats.

<h1>SRA Rd, Rt, shamt</h1>

<table width="505">

 <tbody>

  <tr>

   <td width="83">0</td>

   <td width="83">–</td>

   <td width="84">Rt</td>

   <td width="84">Rd</td>

   <td width="87">shamt</td>

   <td width="83">3</td>

  </tr>

 </tbody>

</table>

6                   5                   5                   5                   5   6

Shift register Rt right arithmetically by the distance indicated by immediate shamt. Rs is ignored for sra.

<h1>SRAV Rd, Rt, Rs</h1>

<table width="505">

 <tbody>

  <tr>

   <td width="83">0</td>

   <td width="84">Rs</td>

   <td width="84">Rt</td>

   <td width="84">Rd</td>

   <td width="87">0</td>

   <td width="83">7</td>

  </tr>

 </tbody>

</table>

6                   5                   5                   5                   5   6

Shift register Rt right arithmetically by the distance indicated by the register Rs. Hint: Be careful of using Verilog operator &gt;&gt;&gt; directly in your code. To use this operator, you have to declare the variable as signed.

<h1>LUI Rt, Imm</h1>

<table width="505">

 <tbody>

  <tr>

   <td width="83">0xf</td>

   <td width="84">0</td>

   <td width="84">Rt</td>

   <td width="254">Imm</td>

  </tr>

 </tbody>

</table>

6                   5                   5                                       16

Load the lower halfword of the immediate imm into the upper halfword of register Rt. The lower bits of the register are set to 0.

<h1>ORI Rt, Rs, Imm</h1>

<table width="505">

 <tbody>

  <tr>

   <td width="83">0xd</td>

   <td width="84">Rs</td>

   <td width="84">Rt</td>

   <td width="254">Imm</td>

  </tr>

 </tbody>

</table>

6                   5                   5                                       16

Put the logical OR of register Rs and the zero-extended immediate into register Rt.




<h1>5.     Test</h1>

There are 3 test patterns, CO_P2_test_data1.txt ~ CO_P2_test_data3.txt. The default pattern is the first one. Please change the column 39 in the file “Instr_Memory.v” if you want to test the other cases.

column 39 : $readmemb(“CO_P2_test_data1.txt”, Instr_Mem)

The following are the assembly code for the test patterns.




<table width="529">

 <tbody>

  <tr>

   <td width="178"><strong>1 </strong></td>

   <td width="175"><strong>2 </strong></td>

   <td width="177"><strong>3 </strong></td>

  </tr>

  <tr>

   <td width="178">addi r1,r0,13 addi r2,r0,7 sltiu r3,r1,0xFFFF beq r3,r0,1 slt r4,r2,r1 and r5,r1,r4 subu r4,r1,r5</td>

   <td width="175">addi r6,r0,-2 addi r7,r0,5 or r8,r6,r7 addi r9,r0,-1 addi r6,r6,2 addu r9,r9,r6 beq r6,r0,-3</td>

   <td width="177">ori r10,r0,3 lui r11,-10 sra r11,r11,8 srav r11,r11,r10 addi r10,r10,-1 bne r10,r0,-3</td>

  </tr>

  <tr>

   <td width="178"><strong>final result </strong></td>

   <td width="175"><strong>final result </strong></td>

   <td width="177"><strong>final result </strong></td>

  </tr>

  <tr>

   <td width="178">r1 = 13, r2 = 7, r3 = 1, r4 = 12, r5 = 1</td>

   <td width="175">r6 = 2, r7 = 5, r8 = -1, r9 = 1</td>

   <td width="177">r10 = 0, r11 = -40</td>

  </tr>

 </tbody>

</table>




The file “CO_P2_Result.txt” will be generated after executing the Testbench. Check your answer with it.