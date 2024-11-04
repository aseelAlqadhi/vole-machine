The program simulates a simple machine simulation, that is able to execute basic operations defined by hexadecimal instructions .consisting of :

CPU: Executes instructions.
Memory: Stores data and instructions.
ALU (Arithmetic Logic Unit): Performs arithmetic operations.
Control Unit (CU): Manages instruction flow and execution.
Screen: Displays output to the user.
User Interface (UI): Manages the user for input and output.

 Memory Class :
The Memory class simulates the computer's memory.
An array of strings (mem[256]) initialized to "00", representing 256 memory cells.
It contains setter fuction  that sets the value to specific memory address  with a bound (0-255),and a getter function that returns the value at the memory address .

Register Class :
The Register class simulates a single register.
It is also an array of integers (reg [16]) initialized to 0. 
It also has setter and a getter function that sets the value of the register and returns it .
The class also has one more function (set_val_to_mem(Memory &m, int address)) ,which stores the value of the register in to the memory address .

ALU class :
The ALU class inherits from the  Register class  to include arithmetic capabilities.
The class has six functions ,the first function (valid(string &s)) ,validates weither the string is hexadecimal number or not .
The second function (add(int idx1, int idx2, int idx3, Register &reg)) basically add values  from two registers and stores the result in a third one .
Then the (dec_to_hex(string &s)) and the (hex_to_dec(string &s)) functions the with be used for converting from hexadecimal to decimal so the operations with be done on them a stored in memory and for converting the floating numbers .
Function (add_floats(int idx1, int idx2, int idx3, Register &reg)) and (string float_to_hex(int idx1, int idx2, int idx3, Register &reg) ) are responsible for adding the floating points and then convert the to hexadecimal.

Control Unit (CU) Class :
The CU class is responsible for Manding the instructions .
loadFromMemory(int idxReg, int idxMem, Register &reg, Memory &memory): Loads a value from memory into a register.
-loadImmediate(int idxReg, int val, Register &reg): Loads a specific value into a register.
-store(int idxReg, int idxMem, Register &reg, Memory &memory): Stores a register value into memory.
-move(int idxReg1, int idxReg2, Register &reg): Copies a value from one register to another.
-jumpIfEqual(int idxReg, int address, Register &reg, int &programCounter): This function checks if the value in a specified register is zero. If it is, the program counter is changed to jump to a different instruction in memory.
-halt(): Stops the program execution.
decode(const string &instr): Converts the  instruction string into a vector of integers ,so the cpu can deal with it .

 CPU Class :
The CPU class manages the execution of instructions. It’s  is the main part of the machine simulation that handles running instructions and  tracking the  the  state of the processor . It includes a Register to store data, an ALU for doing math and logic operations, and a Control Unit (CU) to control how instructions are processed. The CPU keeps track of the program counter, which shows which instruction will run next. It has methods to fetch the next instruction from memory, execute it based on what it means after decoding the instruction , and display the current state of the CPU, including the values in the registers and the program counter.
The class functions:
-fetchNextInstruction(Memory &memory): Fetches the next instruction from memory based on the program counter.
-executeInstruction(Machine &machine): Executes the instruction currently held in the instruction register, using the CU and ALU.
-displayState(): Displays the current state of the CPU, including the program counter and register values.

 Machine Class :
The Machine class acts as the  main controller of the simulation, bringing together important parts like the CPU, memory, and screen. Its job is to load a program from a file into memory, which holds the instructions for the CPU to follow. The Machine class has methods to show the current state of the CPU and memory, letting users see what's happening in the simulation.it also  checks the program counter, and views the machine's status. To sum up , the Machine class connects all the pieces of the simulation together.
The class functions: 
-Function loadProgramFile(const string &filePath): Loads instructions from a file into memory.
-outputState(): Displays the state of the CPU and memory.
-startSimulation() function : Starts the simulation allowing user to enter the input .

 User Interface (MainUI) Class  :
The MainUI class is responsible for interacting with the user during the simulation. It prints out a menu that shows the options, like checking the program counter, viewing the memory and register state, or entering new instructions. The class includes methods to display this menu (DisplayMenu())  and (inputChoice()) to take user input for choices and instructions. By handling user requests and showing the results, the MainUI class makes it easy for users to understand and control the simulation, allowing them to see what's happening and input commands as needed.


 
