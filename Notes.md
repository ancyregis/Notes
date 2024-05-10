# Notes
Daily update about classes

14/02/2024

RAM -> primary storage memory, two types of Ram SRAM(Static Ram) and DRAM(Dynamic RAM), both SRam and DRam are volatile memory, SRam is made up of capacitors,SRam is faster than DRam.
CPU knows only addition, and other operations are performed by architecture.
Secondary memory is non volatile, and it includes storage devices like hard drives and SSDs
Cortex M is a Microprocessor -> it contains only the processor.
microcontroller -> it contais the complete computer system (CpU, I/O, RAM, ROM etc..)
The system bus is the median that connects  pheripherals to the processor. It has 8 buses.
GPIO -> General Purpose Input/Output
PHERIPHERALS -> GPIO -> to communicate the outside environment, Pheeripherals are send by SYSTEM BUS.
APB2 speed is twice to APB1

GPIO generally used for:
1. Reading digital signals
2. issung interrupts
3. generating triggers for external components

GPIO PIN :
         value consists of ine of two voltage settings, we can program each PIN.
GPIO PORT :
         many PIN join together is called port

MULTIPLEXING -> PIN -> GPIO
                     ->UART
            we can act pin  as GPIO, UART etc is called multiplexing.

The instruction bus is used for sending commands to the pheripherals, while the data bus is used for transferring data.
A UART (Universal Asynchronous Receiver/Transmitter)Pheriperal can be implemented using GPIO pins to provide serial communication.
Each GPIO pin can be configured as either an input or output buffer, depending on the state of the enable line(1 for output , 0 for input).
In input mode,  the GPIO pin can be configured to have a pull up or pull down register to stabilize the input.
In output mode, the  GPIO pin can be configured in open-drain state ,which means when the transistor is ON , the pin is pulled to ground.
To access the  GPIO pin direction mode you can use the MODER register.
To access the GPIO A port you have to activate the clock. This can be done by setting the corresponding  bit in the RCC (Reset and Clock Control) AHB1ENR(Advanced high performance bus)register.
Using one bit you cvan produce two values eg: 2^1(0,1); 2^2(4) values; 2^10(1024)values; 2^32(4 gega ) values.
The function mode of the GPIO pin can be configured using the first 6 bits of the MODER register(a16).
You can enable or disable the pull up or pull down register by setting or clearing the ccorresponding bits in the MODER register.

MODER
to configure the I/O direction mode
1. 00 : input (reset state)
2. 01 : General purpose output mode
3. 10 : Alternate function mode
4. 11 : Analog mode

15/02/2024

GPIO have 7 memory space and address, that memory space is called Registers.

REGISTERS
1. MODER
2. OTYPER
3. OSPEEDER
4. PUPDR
5. IDR
6. ODR
7. BSRR
8. LCKR
9. AFRL
10. AFRH

GPIOA base address will be -> 0x40020000
When we know the base address of GPIOA and we know the offset 0x00 then we can know the place.

MODER register
base address + offset : 0x00

OTYPER register
base address + offset : 0x04

pheripheral base 40020000
                 offset 20000
base address    40000000
                pheripheral base (pheriph base + AHBIperiph_offset)
         (GPIO_OFFSET = 0x0000UL)

16/2/24

__IO -> volatile
GPIO typedef*GPIO_BASE
here GPIO typedef is one structure for different address GPIOA BASE, GPIOB BASE,.....
AHB1ENR , The registers above the ABH1ENR  should be used for that we will create a dummy , The registers below the ABH1ENR  is no need to use.
DELAY -> used to blink
RR_TYPEDEF* -> using structure you cahnge all the values to address.

GPIO_BASE (AHB1PERIPH_BASE + GPIO_OFFSET)
When we use the (volatile unsigned int *)then we call as address
integer poiter typecaste (RCC_BASE + AHB1EN_R_OFFSET)will be changes as address.
(*(volatile unsigned int *)(RCC_BASE + AHB1EN_R_OFFSET))

21/02/2024

SERIAL Communication
sender----->reciver
data being transffered  one by one(line by line process)
less cost
8 bit data is transferred one bit ata a time
serial communication uses two methods: 
1.SYNCHRONOUS
clock is transmitted with data
2. ASYNCHRONOUS
no clock is transmitted(baudrate)

PARALLEL communication
      ------->
sender------->reciver
      ------->

8 bit data is transferred at the same time
hight cost
faster than serial communication

Mbps - mega bits per second
LSB - Least dignificance bit
MSB - Most Significance bit
UART- universal asynchronous receiver/transmitter
UART is a serial communication.

DUPLEX
Data can be transmitted and received
               transmitter------------->receiver
               receiver<----------------transmitter
eg: phone
SIMPLEX
Data can be transmitied only an received only.
- one direction only
eg: FM
           transmitter----------------->receiver
HALFDUPLEX
Data can be transmitted in only one way at a time
FULLDUPLEX         
Data can be transmitted in both ways.
eg:UART
→In arynchronous transmission, each byte (character) is packed between start and stop bite

In UART-it (stop bit) can be a bit, 1 bit or 1/2 bit
→ Baudrate
connection speed expereused in bets per second

22/02/2024

sudo apt get install minicom
for linux everything is a file or it is a process,in linux mouse, keyboard are file

in new tab
ls /
ls /dev
ls -l /dev

SOC-system on chip ---->Name in soc 
SOM-system on module------>phycore A5D2X
SBC-single board computer----->rugged board A5D2X

Three types of boot
   1. flash memory boot
   2. sd card  booot
   3. network boot
flash memory is like a harddisk

at91.bootstrap ---->primary

boot RDm-->it works as load to the SRAM
u-boot--> it will load in .dtb RAM
.dts--->device tree source
.dtsi---->device tree source include
.dtb--->compiles both .dts and .dtsi
FInally load all and only mount thr RFS





28/2

ARM:
electronic Gadgets like phone , microcontrillert..etc
ARM:
Before ARM introduce we have CICS
cics----> ARM
load and store---> These & instructions only work in memory other instructions all work in Registers.

compile source file

• C

.i

•S assembly

elf.

Secondary memory saves the saved codes.. when the code is send from secondary memory to primary memory is called the process.
=> For one set architecture there will be many microarchitecture availabel.
Arm is not a chip manufacturing company" design
Family can have multiple architecture for that can have multiple processor.

ARM architecture specifier:

1.Instruction set
2.Register set
3.Exception model(interrupt)
4.Memory model
5.Debug, Trace and profilines



RISC- Reduced instruction set computer:
1.simple instructions
2.simple Addressing modes
3.Load store Architecture
4.Big Endian and little Endian

Mioro architecture
1.build and design of a processor
2.Number and sizes of cache
3.cycle court for individual instructions
4.which optional feature are implemented.


ARM Dowmentation:

- ARM [architecture reference manual]

- TRM [ Technical reference manual]

-CIM [Configuration and integration manual]

- Soc datasheet.



29/2/24


SHELL SCRIPT
shell- is a program
A shell script is a textfile containing a series of commands that are interpreted and executed by a shell program. shell scripts are used to automate tasks, execute commands or perform various oprations within the linux environment.

mkdir folder name
vim filename.sh
                  #!/bin/bash
                  echo "Rathinam Technical Campus"
                  exit 0
chmod 777 filename.sh
./filename.sh

Library--->system call--->kernel
           it will acess the kernel
PROCESS CREATION 
system()-->Library function
fork()-->system call
wait()-->system call          ----->its all call the clone for execution
waitpid()-->system call
exec()-->system call
clone()-->clone system call

wait and waitpid is used avoid zombie process.
to see the content inside folder we use "ls -al"
By using System library we can run the bash command.
there are 9 man pages available.

Fork creates a new process then the new process is referred to us child process, the calling is called the parent process, both child and parent process have separate memory.


1/3/24
orphan-->chils is running , the parent is terminating
zombie-->parent is running, child is terminating.
In zombie process that we have to kill the parent,killing the parent by finding the id (kill -9 ID)
To avoid zombie process we use wait system call
silver bullet -9
To kill zombie
1)kill -9 "process IDF"
2)ctrl+c
T
