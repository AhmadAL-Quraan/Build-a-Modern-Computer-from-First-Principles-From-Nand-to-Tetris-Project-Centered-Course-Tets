We will start with a brief introduction of Boolean algebra, and learn how Boolean functions can be physically implemented using logic gates. We will then learn how to specify gates and chips using a Hardware Description Language (HDL), and how to simulate the behaviour of the resulting chip specifications using a hardware simulator. This background will set the stage for Project 1, in which you will build, simulate, and test 15 elementary logic gates. The chipset that you will build this module will be later used to construct the computer's Arithmetic Logic Unit (ALU) and memory system. This will be done in modules 2 and 3, respectively.

* This unit have 8 chapters and ends with a project:
	1) [[#Unit 1.1 Boolean Logic]] 
	2) [[#Unit 1.2 Boolean Functions Synthesis]]
	3) [[#Unit 1.3 Logic Gates]]
	4) [[Unit 1.4]]
	5) [[Unit 1.5]]
	6)  [[Unit 1.6]]
	7) [[Unit 1.7]]
	8) [[Unit 1.8]]



---
### Unit 1.1 Boolean Logic

* I have been introduced to Boolean Identities, which are some laws that applied when you have some expressions in boolean algebra.
 ![[screenshot-20250729-182907.png]]
 * So if we have this boolean algebra, this will the solution (boolean identities) for it .
   ![[screenshot-20250729-184835.png]]
 ---



### Unit 1.2 Boolean Functions Synthesis
* It's the **process of creating or constructing a Boolean function or logic circuit** that produces a desired output for all possible inputs.
* It's the **process of creating or constructing a Boolean function or logic circuit** that produces a desired output for all possible inputs.
* You will be given a truth table.
* **Goal:**  Find the **simplest** or **most efficient** Boolean expression (minimal number of gates, variables, or cost).
* **Input:** Usually, you’re given a **truth table**, **verbal description**, or **set of requirements** that define how outputs depend on inputs.
* Ex:

* ![[screenshot-20250729-212455.png]]
* Now for each 1 in (f) column we will generate a boolean expression for it:
     - For the row 0 it will be --> (NOT(x) AND NOT(y) AND NOT(z))
     - For the row 2 it will be ---> (NOT(x)) AND y AND NOT(z))
     - For the row 4 it will be --> (x AND NOT(y) AND NOT(z))
 - NOTICE THAT EACH ONE OF THESE EXPRESSIONS IS UNIQUE TO ITSELF, MEANS THE FUNCTION WILL NEVER GENERATE 1 IF IT APPLIED TO ANY OTHER ROW.
 - Now how do we combine them ?? we will use **OR** .
 - ![[screenshot-20250730-194901.png]]
 - ![[screenshot-20250730-205810.png]]

---
* Any Boolean function can be represented using an expression containing AND and NOT operation.
* proof: (x OR y) = NOT(NOT(x) AND NOT(y))


* There is 1 operation that can be used to express and compute any function by itself, it's called **NAND**
* NAND: NOT, AND ==> **NOT(x AND y)**
* ![[screenshot-20250730-213813.png]]
* ![[screenshot-20250730-214132.png]]
* We will use **NAND** gates to compute everything and build the complex system just by using it.
---



### Unit 1.3 Logic Gates
* A technique for implementing Boolean functions using logic gates.
* Logic gates:
	* **Elementary** (Nand, And, Or, Not, ...)
	* **Composite** (Mux, Adder, ...)



#### Elementary logic gates

* **NAND**
![[screenshot-20250730-215237.png]]
* **AND**
![[screenshot-20250730-215405.png]]
* **OR**
![[screenshot-20250730-215408.png]]
* **NOT**
![[screenshot-20250730-215412.png]]

* We can use these elementary gates to create composite ones.



#### Composite logic gate - Gate Interface/ Gate Implementation
* For example we can make this **three AND logic gate**, the first picture describes the **gate interface**, the second one describes the **details/ implementation** of it.
![[screenshot-20250730-215922.png]]



#### Circuit implementations 
![[screenshot-20250730-220520.png]]
* *This is very important*: this course will not discuss the physical manners but instead it will focus more on something like the right bottom of the screen (Theories and Implementation).