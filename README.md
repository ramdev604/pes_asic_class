This Repository Guides you to complete the ASIC flow from scratch (Faculty: Mahesh Awati, Guide: Kunal Ghosh)

# Lab Classes 

<details>
  <summary> Week 1 : Day 1: Introduction to RISCV ISA and GNU Compiler Toolchain </summary>
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
  <summary> Week 1 : Day 2 - Introduction to ABI and Basic Verification Flow </summary>
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

<details>
  <summary> Week 2 : Day 1 - Introduction to Verilog RTL design and Synthesis</summary>
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
  <summary> Week 2 : Day 2  Timing libs, hierarchical vs flat synthesis and efficient flop coding styles </summary>
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






