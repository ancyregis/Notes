# Notes
Daily update about classes

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
