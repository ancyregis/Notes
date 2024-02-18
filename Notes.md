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
