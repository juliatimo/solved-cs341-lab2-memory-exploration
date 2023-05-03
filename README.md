Download Link: https://assignmentchef.com/product/solved-cs341-lab2-memory-exploration
<br>
The goal in this lab will be to explore the Harvard architecture and its memory spaces. The starter code can be found on GitHub under Lab 2. The code is mostly written for you already, you should uncomment it bit by bit and observe what happens.

<h1>Part 1</h1>

The processor used in the Arduino UNO (the ATMEGA328) is built along the lines of the Harvard architecture.  In this architecture, the processor stores program code and program data/stack in separate memory spaces.




There are three memory spaces in the Arduino UNO processor architecture.  See the Figure above. Note that addresses for each of the three memory spaces start with 0x0000 and go to a symbolic constant as the end address – FLASHEND, RAMEND, or E2END. These constants are defined in the IDE compiler and you will determine their hex values below.




The Flash (program code) and EEPROM (configuration data) are non-volatile meaning that their contents are preserved across power cycles.  The RAM is volatile so its contents are lost when the power is turned off.  The contents of RAM are initialized during the power on sequence in the program code.

Note that the 32 general purpose registers and the I/O device registers are

“memory mapped” into the data memory address space from 0x0000 to 0x00ff.  The program memory is organized as 16 bit words while the data memory and EEPROM are organized as bytes.




<ol>

 <li>Setup an Arduino in the simulator (no components necessary)</li>

 <li>Find the section in the <a href="https://github.com/jack17davis/cs341/blob/master/Lab%202/Lab%202%20Starter.ino">code</a> labeled “Part 1” and uncomment it</li>

 <li>Click run, and open the serial monitor</li>

 <li><strong>Record the 3 constants in the results section of your lab report </strong></li>

</ol>

<strong> </strong>

<h1>Part 2</h1>

Now that we know the size of our memory spaces, lets create some arrays and see where they end up.

<ol>

 <li>I have already created 6 arrays, 3 as global variables and 3 in setup</li>

 <li>Take a careful look at the arrays, and how they are initialized</li>

 <li>Uncomment the section in the code labeled “Part 2”</li>

 <li>Clear the serial monitor, and click run</li>

 <li>Look at the locations of the arrays and try to piece together how the compiler allocates memory. Where does the heap, stack, and initialized data end up?</li>

</ol>




<h1>Part 3</h1>

After seeing where our arrays ended up, we’re going to print out sections of the RAM to confirm our guesses at the end of part 2. Tinkercad limits the buffer size of the serial monitor, so this means that we cannot look at the entire RAM at one time easily.




<ol>

 <li>I have already created the functions displayRAM and displayAllRAM to help you out. Call them like this:</li>

</ol>

displayRAM((char *) 0x100, (char *) 0x200, false); displayAllRAM(2000, false); //displays memory in 0x100 blocks with delays  The output will look something like this.




The first row corresponds to memory addresses 0x200 through 0x20F. Thus, the memory address 0x2A0 is currently storing the integer 4.

<ol start="2">

 <li><strong>In your lab report answer the following question: </strong></li>

</ol>

<strong>What memory addresses were used by the stack, heap, and initialized data? </strong>Give rough estimates such as “the stack starts around 0x300 and extends towards 0x00.”