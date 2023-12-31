This Repository Guides you to complete the ASIC flow from scratch (Faculty: Mahesh Awati, Guide: Kunal Ghosh)

# Lab Classes 
# Week 1
<details>
  <summary> Day 1 - Introduction to RISCV ISA and GNU Compiler Toolchain </summary>
  <br>



## C program That calculates sum from 1 to N
____Compiling it using C compiler____
```
gcc sum1ton.c 
./a.out
```

![sum1ton](https://github.com/ramdev604/pes_asic_class/assets/43489027/e8bd87eb-8e11-4623-a420-0eefff9888cc)

____Compiling using RISCV compiler____
```
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
spike pk sum1ton.o
riscv64-unknown-elf-objdump -d 1_to_N.o | less (in new tab)
```
## Spike Simulation

![spike1](https://github.com/ramdev604/pes_asic_class/assets/43489027/ae1e51b5-80fd-4633-8f3b-6884fbaf1316)

## Write a C program for Signed And Unsigned Numbers 
![unsigned](https://github.com/ramdev604/pes_asic_class/assets/43489027/474784ca-5318-4a01-abd9-995b25a5eaff)



```
vim unsignedHighest.c
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o unsignedHighest.o unsignedHighest.c
spike pk unsignedHighest.o
```
![WhatsApp Image 2023-08-21 at 22 56 11](https://github.com/ramdev604/pes_asic_class/assets/43489027/55e39c44-6d41-405c-b23c-ce8dd7204f6d)





## For the signed number 

  ![3](https://github.com/ramdev604/pes_asic_class/assets/43489027/dcecc5ae-fe61-4a96-bab9-8889851ad0fe)



```
vim signedHighest.c
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o signedHighest.o signedHighest.c
spike pk signedHighest.o
```

![4](https://github.com/ramdev604/pes_asic_class/assets/43489027/5e15b6ff-edb2-43c4-acce-e382fc390a72)
</details>

<details>
  <summary> Day 2 - Introduction to ABI and Basic Verification Flow </summary>
  <br>

# Introduction to ABI and basic verification flow

### Download the load.S , 1to9_count.c files from 
https://github.com/kunalg123/riscv_workshop_collaterals/tree/master/labs




```
cat 1to9_custom.c
cat load.S
```



![ss1](https://github.com/ramdev604/pes_asic_class/assets/43489027/087362a5-5c13-4923-a2a2-a0ffbd3c02a0)


![3](https://github.com/ramdev604/pes_asic_class/assets/43489027/832a281f-0b6f-4d96-bfed-a3d324d1a56e)

```
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o 1to9_custom.o 1to9_custom.c load.S
spike pk 1to9_custom.o
riscv64-unknown-elf-objdump -d 1to9_custom.o | less
```

## Spike Simulation

![Screenshot from 2023-08-21 09-10-32](https://github.com/ramdev604/pes_asic_class/assets/43489027/64e49c93-a6e6-42f4-a187-1c789809ce21)
</details>

#  RTL design using Verilog with SKY130 Technology 

<details>
  <summary> Day 1 - Introduction to Verilog RTL design and Synthesis</summary>
  <br>

## Task 1
## Loading a mux and it's testbench into iverilog 
  ```
    sudo -i
    cd /home
    cd ramdev
    cd VLSI
    cd sky130RTLDesignAndSynthesisWorkshop
    cd verilog_files
  ```
![gtk](https://github.com/ramdev604/pes_asic_class/assets/43489027/66d33e8d-f382-48ed-8b72-9988a1de738d)

![GTK1](https://github.com/ramdev604/pes_asic_class/assets/43489027/58800e3e-ea20-47cb-b6ff-57cca7781373)

## Task 2
## Labs using Yosys and Sky130 PDKs

```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog good_mux.v
synth -top good_mux 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```
![yosys](https://github.com/ramdev604/pes_asic_class/assets/43489027/785a7786-3069-49f5-ae7a-bec890e9bb14)

![yosys1](https://github.com/ramdev604/pes_asic_class/assets/43489027/48dbaf4a-f863-45fb-8caa-d5ed151e9749)

## Writing a netlist for the verilog code
![yosys2](https://github.com/ramdev604/pes_asic_class/assets/43489027/a7349e48-c321-4551-b50d-5d1ebb223bc4)
![yosys3](https://github.com/ramdev604/pes_asic_class/assets/43489027/422411fc-9ac3-48c3-a4b2-c47e569d439d)
![yosys4](https://github.com/ramdev604/pes_asic_class/assets/43489027/09531182-0212-463e-a6c1-2d60823eaa8f)
![yosys5](https://github.com/ramdev604/pes_asic_class/assets/43489027/217e8779-951f-4b4f-832f-e910dcea8f61)
</details>

<details>
  <summary> Day 2 - Timing libs, hierarchical vs flat synthesis and efficient flop coding styles </summary>
  <br>

## Introduction to .lib

## Task 1
### Command to invoke sky130_fd_sc_hd__tt_025C_1v80.lib file 

```
 vim ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

![T1_1](https://github.com/ramdev604/pes_asic_class/assets/43489027/f4dad528-775e-4d81-ade2-478881e7b74e)
![T1_2](https://github.com/ramdev604/pes_asic_class/assets/43489027/f2381deb-d0ee-4333-aee2-0daded1f5bad)
![T1_3](https://github.com/ramdev604/pes_asic_class/assets/43489027/8ffd0c36-f3d2-4f4f-b0e6-02088b677bfe)
![T1_4](https://github.com/ramdev604/pes_asic_class/assets/43489027/d596dcda-df77-4493-b899-dd9a2c7fbad1)

## Task 2
## Hier synthesis flat synthesis 

```
yosys
read_liberty -lib ../lib//sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog multiple_modules.v
synth -top multiple_modules
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show multiple_modules
```
![yosys1](https://github.com/ramdev604/pes_asic_class/assets/43489027/35b51b32-b8a7-460d-be27-fdb1c72e84a7)
![yosys2](https://github.com/ramdev604/pes_asic_class/assets/43489027/621d0260-b681-4541-9c50-2ab36208be5c)

```
write_verilog multiple_modules_hier.v
!vim multiple_modules_hier.v 
```
![T2_1](https://github.com/ramdev604/pes_asic_class/assets/43489027/be2f74ac-9e20-4bc1-8333-59d82eb4cc1d)
![T2_2](https://github.com/ramdev604/pes_asic_class/assets/43489027/1861bbee-4e6b-4597-a85f-b71e601c6453)

## Task 3

## Various Flop Coding Styles and optimization

### For asynchronous reset
```
iverilog dff_asyncres.v tb_dff_asyncres.v
./a.out
gtkwave tb_dff_asyncres.vcd 
```
![GTK1](https://github.com/ramdev604/pes_asic_class/assets/43489027/3e7479ed-f378-44b5-ad33-ac575d35e8c0)

![GTK2](https://github.com/ramdev604/pes_asic_class/assets/43489027/3f973171-b9a8-48a9-aa19-6c613fbd8547)

### For asynchronous set
```
iverilog dff_async_set.v tb_dff_async_set.v
./a.out
gtkwave tb_dff_async_set.vcd
```
![GTK3](https://github.com/ramdev604/pes_asic_class/assets/43489027/39762c4c-4222-419d-a803-e71cf9120539)

### For Synchronous reset
```
iverilog dff_syncres.v tb_dff_syncres.v
./a.out
gtkwave tb_dff_syncres.vcd 
```
![GTK4](https://github.com/ramdev604/pes_asic_class/assets/43489027/c18cf3c9-ac8a-48c2-bc30-ca150a926f06)

## Task 4
### Synthesizing all 3 codes using yosys

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_asyncres.v
synth -top dff_asyncres
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib//sky130_fd_sc_hd__tt_025C_1v80.lib
show
```
![yosys3](https://github.com/ramdev604/pes_asic_class/assets/43489027/20574c1f-0f00-470b-bc64-0c113fb19d9a)
![yosys4](https://github.com/ramdev604/pes_asic_class/assets/43489027/fc768d3e-11df-4167-b955-fb25e1ca9ebc)

```
read_verilog dff_async_set.v
synth -top dff_async_set
dfflibmap -liberty ../lib//sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```
![yosys5](https://github.com/ramdev604/pes_asic_class/assets/43489027/6da8c888-5126-4150-967b-02fd0eb09321)

```
read_verilog dff_syncres.v
synth -top dff_syncres
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```
![yosys6](https://github.com/ramdev604/pes_asic_class/assets/43489027/36ffdba6-d323-4b7c-b35a-2d1335590fc0)
</details>

<details>
  <summary> Day 3 - Combinational and Sequential Optimizations </summary>
  <br>

# Introduction to optimizations
## Combinational logic optimizations
**opt_check1.v**
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
read_verilog opt_check.v
synth -top opt_check
opt_clean -purge
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```
![d3_1](https://github.com/ramdev604/pes_asic_class/assets/43489027/720c5d35-658d-44ce-b783-d5a0bbe86c43)

**opt_check2.v**
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
read_verilog opt_check2.v
synth -top opt_check2
opt_clean -purge
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```
![d3_2](https://github.com/ramdev604/pes_asic_class/assets/43489027/dfef47fa-e098-4169-ba53-3e8a6496eaa5)


**opt_check3.v**

```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
read_verilog opt_check3.v
synth -top opt_check3
opt_clean -purge
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```
![d3_3](https://github.com/ramdev604/pes_asic_class/assets/43489027/b73fb517-2326-4d47-a84e-9150dac46db1)

**multiple_module_opt.v**
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
read_verilog multiple_module_opt.v
synth -top multiple_module_opt
flatten
opt_clean -purge
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```
![d3_4](https://github.com/ramdev604/pes_asic_class/assets/43489027/b23df09a-3e79-4a4c-8a6e-76aae68ba1f0)

# Sequential logic optimizations
**dff_const1.v**

```
iverilog dff_const1.v tb_dff_const1.v
./a.out
gtkwave tb_dff_const1.vcd
```
![diff_term](https://github.com/ramdev604/pes_asic_class/assets/43489027/80f2ea14-7c70-482a-8f8e-2b8b76e66b8b)
![diff1_gtk](https://github.com/ramdev604/pes_asic_class/assets/43489027/cd615e5b-9e2d-4250-8b67-b1dfb5fc416c)


**Synthesis**
```
  read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
  read_verilog dff_const1.v
  synth -top dff_const1
  dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
  abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
  show
```
![diff1_yosys](https://github.com/ramdev604/pes_asic_class/assets/43489027/0e5fac57-121a-4341-a4de-99ba74871b1c)

**dff_const2.v**
``` v
module dff_const2(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b1;
	else
		q <= 1'b1;
end

endmodule
```
**Simulate**
```
iverilog dff_const1.v tb_dff_const2.v
./a.out
gtkwave tb_dff_const2.vcd
```
![diff2_gtk](https://github.com/ramdev604/pes_asic_class/assets/43489027/a4feb46c-82bb-4919-b5a8-e156d92a85fe)


**Synthesis**
```
  read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
  read_verilog dff_const2.v
  synth -top dff_const2
  dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
  abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
  show
```
![diff2_yosys](https://github.com/ramdev604/pes_asic_class/assets/43489027/50871366-9725-4080-a99a-f8aa9f3934fe)

**dff_const3.v**
``` v
module dff_const3(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b1;
		q1 <= 1'b0;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end

endmodule
```

**Simulate**
```
iverilog dff_const3.v tb_dff_const2.v
./a.out
gtkwave tb_dff_const3.vcd
```
![diff3_term](https://github.com/ramdev604/pes_asic_class/assets/43489027/1fbd83d9-44cb-40c4-9709-20245fcbde73)
![diff3_gtk](https://github.com/ramdev604/pes_asic_class/assets/43489027/fe97d6f2-4ceb-414c-9d64-209dcc73b88b)


**Synthesis**
```
  read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
  read_verilog dff_const3.v
  synth -top dff_const3
  dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
  abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
  show
```
![diff3_yosys](https://github.com/ramdev604/pes_asic_class/assets/43489027/c8aa6825-ccee-447d-b900-5e042bc7de6e)

# Sequential optimzations for unused outputs
**counter_opt.v**
``` v
module counter_opt (input clk , input reset , output q);
reg [2:0] count;
assign q = count[0];

always @(posedge clk ,posedge reset)
begin
	if(reset)
		count <= 3'b000;
	else
		count <= count + 1;
end

endmodule
```
**Synthesis**
```
  read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
  read_verilog counter_opt.v
  synth -top counter_opt
  dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
  abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
  show
```

![counter1](https://github.com/ramdev604/pes_asic_class/assets/43489027/9ca788d8-df6c-42ec-8c38-7e7365847835)

**counter_opt2.v**
``` v
module counter_opt (input clk , input reset , output q);
reg [2:0] count;
assign q = (count[2:0] == 3'b100);

always @(posedge clk ,posedge reset)
begin
	if(reset)
		count <= 3'b000;
	else
		count <= count + 1;
end

endmodule
```
**Synthesis**
```
  read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
  read_verilog counter_opt2.v
  synth -top counter_opt
  dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
  abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
  show
```
![counter2](https://github.com/ramdev604/pes_asic_class/assets/43489027/24099692-4d86-4a73-b2de-0c1b91746b4a)
</details>

<details>
  <summary> Day 4 - GLS and Synthesis-Simulation Mismatch </summary>
  <br>
	
**ternary_operator_mux.v**
	
**Simulation**
```
iverilog ternary_operator_mux.v tb_ternary_operator_mux.v
./a.out
gtkwave tb_ternary_operator_mux.vcd
```
![ter1_term](https://github.com/ramdev604/pes_asic_class/assets/43489027/900a9cb5-85e2-4797-a165-c27af974e889)
![ter1_gtk](https://github.com/ramdev604/pes_asic_class/assets/43489027/9e39892c-8035-4dc9-b1d4-d8c132062e73)


**Synthesis**
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog ternary_operator_mux.v
synth -top ternary_operator_mux
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
write_verilog -noattr ternary_operator_mux_netlist.v
show
```
![ter1_yosys](https://github.com/ramdev604/pes_asic_class/assets/43489027/9ecade19-4573-47bd-a784-b95b41c5d007)

**GLS**
To to Gate level simulation, Invoke iverilog with verilog modules
```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_netlist.v tb_ternary_operator_mux.v
./a.out
gtkwave tb_ternary_operator_mux.vcd
```
![gls_gtk](https://github.com/ramdev604/pes_asic_class/assets/43489027/ee6d00a6-a190-4175-8610-a64ba8d04e76)


** bad_mux.v**
``` v
module bad_mux (input i0 , input i1 , input sel , output reg y);
always @ (sel)
begin
	if(sel)
		y <= i1;
	else 
		y <= i0;
end
endmodule
```
**RTL Simulation**
```
iverilog bad_mux.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
```
![badmux_gtk](https://github.com/ramdev604/pes_asic_class/assets/43489027/7e64326e-938b-4583-83bd-260292e9b3c6)


**Synthesis**
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog bad_mux.v
synth -top bad_mux
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
write_verilog -noattr bad_mux_netlist.v
show
```
![badmux_yosys](https://github.com/ramdev604/pes_asic_class/assets/43489027/ae127ec8-bd43-4a55-9083-e6e302576271)

**GLS**
To to Gate level simulation, Invoke iverilog with verilog modules
```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v bad_mux_netlist.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
```

![gls2_gtk](https://github.com/ramdev604/pes_asic_class/assets/43489027/fe4107c6-f85f-4c5c-bbd9-082a19b3b459)

# Labs on synth-sim mismatch for blocking statement
**blocking_caveat.v**
``` v
module blocking_caveat (input a , input b , input  c, output reg d); 
reg x;
always @ (*)
begin
	d = x & c;
	x = a | b;
end
endmodule
```
**RTL Simulation**
```
iverilog blocking_caveat.v tb_blocking_caveat.v
./a.out
gtkwave tb_blocking_caveat.vcd
```
![rtl2_gtk](https://github.com/ramdev604/pes_asic_class/assets/43489027/ec56e77f-bc8a-4c5d-be56-db092c227c9f)


**Synthesis**
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog blocking_caveat.v
synth -top blocking_caveat
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
write_verilog -noattr blocking_caveat_netlist.v
show
```
![rtl2_yosys](https://github.com/ramdev604/pes_asic_class/assets/43489027/747247e3-8cde-4b4e-879e-1eb12f024f0d)

**GLS**
To to Gate level simulation, Invoke iverilog with verilog modules
```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v blocking_caveat_netlist.v tb_blocking_caveat.v
./a.out
gtkwave tb_blocking_caveat.vcd
```

![gls3_gtk](https://github.com/ramdev604/pes_asic_class/assets/43489027/2fc51442-4c1a-4441-b32d-75f02c820278)
</details>

