Download Link: https://assignmentchef.com/product/solved-cda5155-project-1-mips-simulator
<br>
5/5 - (1 vote)

<table>

 <tbody>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

<table>

 <tbody>

  <tr>

   <td></td>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

In this project you will create a simple MIPS simulator which will perform the following two tasks. Please develop your project in one (C, C++, Java or Python) source file to avoid the stress of combining multiple files before submission and making sure it still works correctly.

<ul>

 <li>Load a specified MIPS text file1 and generate the assembly code equivalent to the input file (disassembler). Please see the sample input file and disassembly output from the webpage.</li>

 <li>Generate the instruction-by-instruction simulation of the MIPS code (simulator). It should also produce/print the contents of registers and data memories after execution of each instruction. Please see the sample simulation output file from the course assignments webpage.You do not have to implement any exception/interrupt handling for this project. InstructionsFor reference, please use the MIPS Instruction Set Architecture PDF (available from class project1 webpage) to see the format for each instruction and pay attention to the following changes.Your disassembler/simulator need to support the two categories of MIPS instructions shown inFigure 1.Figure 1: Two categories of instructionsThe format of Category-1 instructions is described in Figure 2. If the instruction belongs to Category-1, the first two bits (leftmost bits) are always “01” followed by 4 bits Opcode. Please note that instead of using 6 bits Opcode in MIPS, we use 4 bits Opcode as described in Figure 3. The remaining part of the instruction binary is exactly the same as the original MIPS instruction set.Figure 2: Format of Instructions in Category-1</li>

</ul>

Category-1

Category-2

* J, JR, BEQ, BLTZ, BGTZ * BREAK* SW, LW* SLL, SRL, SRA

* NOP

* ADD, SUB, MUL, AND * OR, XOR, NOR* SLT* ADDI

* ANDI, ORI, XORI

01

Opcode (4 bits)

Same as MIPS instruction

1 This is a text file consisting of 0/1’s (not a binary file). See the sample input file sample.txt in the Project1 webpage.

<table>

 <tbody>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

<table>

 <tbody>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

Instruction

Identification bits

J

0000

JR

0001

BEQ

0010

BLTZ

0011

BGTZ

0100

BREAK

0101

SW

0110

LW

0111

SLL

1000

SRL

1001

SRA

1010

NOP

1011

Figure 3: Opcode for Category-1 instructions

Please pay attention to the exact description of instruction formats and its interpretation in MIPS instruction set manual. For example, in case of J instruction, the 26 bit instruction_index is shifted left by two bits (padded with 00 at LSB side) and then the leftmost (MSB side) four bits of the delay slot instruction are used to form the four bits (MSB side) of the target address. Similarly, for BEQ, BLTZ and BGTZ instructions, the 16 bit offset is shifted left by two bits to form 18 bit signed offset that is added with the address of the next instruction to form the target address. Please note that we do not consider delay slot for this project. In other words, an instruction following the branch instruction should be treated as a regular instruction (see sample_simulation.txt).

If the instruction belongs to Category-2, the first two bits (leftmost two bits) are always “11”. Then the following 4 bits serve as identification bits which are specified in Figure 4.

Instruction

Identification bits

ADD

0000

SUB

0001

MUL

0010

AND

0011

OR

0100

XOR

0101

NOR

0110

SLT

0111

ADDI

1000

ANDI

1001

ORI

1010

XORI

1011

Figure 4: Identification bits for Category-2 instructions

<table>

 <tbody>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

<table>

 <tbody>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

Instructions in Category-2 can be further divided into two sub-sets according to whether source2 is register or immediate. When the source2 is register, (“rd ← rs op rt”), the format is shown in Figure 5.

Figure 5: Format of Category-2 instructions with source2 as registerWhen source 2 is an immediate (“rt ← rs op immediate_value”), the format is shown in Figure 6.

Figure 6: Format of Category-2 instructions with source2 as register

Once you look at the sample_disassembly.txt in the assignments (Project1) webpage, it may be confusing for you to see that the last 16 bits of the following binary (offset) has the value of 17 but the assembly shows it as 68. This is a convention issue with MIPS. The binary always shows the actual offset (17 in this case) value. However, the assembly always shows the value shifted by 2 bits to the left (i.e., multiplied by 4).

0100100000100010 0000000000010001 264 BEQ R1, R2, #68

Please note there are also convention related confusion for other instructions. For example, in many binary format, the destination is the middle operand, whereas the destination always shows up as the leftmost operand in assembly instructions &lt;opcode, dest, src1, src2&gt;.

Sample Input/Output Fils

Your program will be given a binary (text) input file. This file will contain a sequence of 32-bit instruction words which begin at address “256”. The final instruction in the sequence of instructions is always BREAK. Following the BREAK instruction (immediately after BREAK), there is a sequence of 32-bit 2’s complement signed integers for the program data up to the end of the file. The NEWLINE character can be either “
” (linux) or “r
” (windows). Your code should work for both cases. Please download the sample input/output files using “Save As” instead of using copy/paste of the content.

Your MIPS simulator (with executable name as MIPSsim) should accept an input file (inputfilename.txt) in the following command format and produce two output files in the same directory: disassembly.txt (contains disassembled output) and simulation.txt (contains the simulation trace). Please hardcode the names of the output files. Please do not hardcode the input filename. It will be specified when running your program. It can be “sample.txt” or “test.txt”.

MIPSsim inputfilename.txt

Correct handling of the sample input file (with possible different data values) will be used to determine 60% of the credit. The remaining 40% will be determined from other valid test cases that you will not have access prior to grading. It is recommended that you construct your own sample input files with which to further test your disassembler/simulator.

11

identification bits (4 bits)

rs (5 bits)

rt (5 bits)

rd (5 bits)

00000000000

11

identification bits (4 bits)

rs (5 bits)

rt (5 bits)

immediate_value (16 bits)

The disassembler output file should contain 3 columns of data with each column separated by one tab character (‘t’ or char(9)). See the sample disassembly file in the class Project1 webpage.

<ol>

 <li>The text (e.g., 0’s and 1’s) string representing the 32-bit data word at that location.</li>

 <li>The address (in decimal) of that location</li>

 <li>The disassembled instruction.</li>

</ol>

Note, if you are displaying an instruction, the third column should contain every part of the instruction, with each argument separated by a comma and then a space (“, ”).

The simulation output file should have the following format.

* 20 hyphens and a new line* Cycle &lt;cycleNumber&gt;: &lt;tab&gt;&lt;instr_Address&gt;&lt;tab&gt;&lt;instr_string&gt;* &lt; blank_line &gt;* Registers* R00:&lt;tab&gt;&lt;int(R0)&gt;&lt;tab&gt;&lt;int(R1)&gt;…&lt;tab&gt;&lt;int(R7)&gt;* R08:&lt;tab&gt;&lt;int(R8)&gt;&lt;tab&gt;&lt;int(R9)&gt;…&lt;tab&gt;&lt;int(R15)&gt;* R16:&lt;tab&gt;&lt;int(R16)&gt;&lt;tab&gt;&lt;int(R17)&gt;…&lt;tab&gt;&lt;int(R23)&gt;* R24:&lt;tab&gt;&lt;int(R24 &gt;&lt;tab&gt;&lt;int(R25)&gt;…&lt;tab&gt;&lt;int(R31)&gt;* &lt; blank_line &gt;* Data* &lt;firstDataAddress&gt;:&lt;tab&gt;&lt;display 8 data words as integers with tabs in between&gt; * ….. &lt;continue until the last data word&gt;

The instructions and instruction arguments should be in capital letters. Display all integer values in decimal. Immediate values should be preceded by a “#” symbol. Note that some instructions take signed immediate values while others take unsigned immediate values. You will have to make sure you properly display a signed or unsigned value depending on the context.

Because we will be using “diff –w -B” to check your output versus ours, please follow the output formatting. TA may not be able to debug in case of any mismatch. In other words, mismatches can be treated as wrong output.

The course project webpage contains the following sample programs/files to test your disassembler/simulator.

<ul>

 <li>sample.txt : This is the input to your program.</li>

 <li>sample_disassembly.txt : This is what your program should produce as disassembled output.</li>

 <li>sample_simulation.txt : This is what your program should output as simulation trace.</li>