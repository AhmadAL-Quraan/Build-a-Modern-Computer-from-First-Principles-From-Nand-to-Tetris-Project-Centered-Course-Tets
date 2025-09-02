---
share: true
published:
---


We will start with a brief introduction of Boolean algebra, and learn how Boolean functions can be physically implemented using logic gates. We will then learn how to specify gates and chips using a Hardware Description Language (HDL), and how to simulate the behavior of the resulting chip specifications using a hardware simulator. This background will set the stage for Project 1, in which you will build, simulate, and test 15 elementary logic gates. The chipset that you will build this module will be later used to construct the computer's Arithmetic Logic Unit (ALU) and memory system. This will be done in modules 2 and 3, respectively.

* This unit have eight chapters and ends with a project:
	1) [[#Unit 1.1 Boolean Logic]] 
	2) [[#Unit 1.2 Boolean Functions Synthesis]]
	3) [[#Unit 1.3 Logic Gates]]
	4) [[#Unit 1.4: Hardware Description Language]]
	5) [[#Unit 1.5: Hardware Simulation]]
	6) [[#Unit 1.6: Multi-Bit Buses]]



---
# Unit 1.1 Boolean Logic

* I have been introduced to Boolean Identities, which are some laws that applied when you have some expressions in boolean algebra.
![screenshot-20250729-182907.png](screenshot-20250729-182907.png)
 * So if we have this boolean algebra, this will the solution (boolean identities) for it .
 
 ![screenshot-20250729-184835.png](screenshot-20250729-184835.png)


### Boolean symbols 

| Meaning | Symbol 1 | Symbol 2      | Symbol 3      | Example      |
| ------- | -------- | ------------- | ------------- | ------------ |
| **AND** | `·`      | `∧`           | sometimes `^` | A⋅B=A∧B      |
| **OR**  | `+`      | `∨`           |               | A+B=A∨B      |
| **NOT** | `′`      | `¬`           | `!` (in code) | A′ = ¬A = !A |
| **XOR** | ⊕        | `^` (in code) |               | A ⊕ B        |
 
 
 👉 In Boolean algebra:

- `A · B` or `A ∧ B` → **AND**
- `A + B` or `A ∨ B` → **OR**
- `A′` or `¬A` or `!A` → **NOT**
 
 
 
 ---



# Unit 1.2 Boolean Functions Synthesis
* It's the **process of creating or constructing a Boolean function or logic circuit** that produces a desired output for all possible inputs.
* It's the **process of creating or constructing a Boolean function or logic circuit** that produces a desired output for all possible inputs.
* You will be given a truth table.
* **Goal:**  Find the **simplest** or **most efficient** Boolean expression (minimal number of gates, variables, or cost).
* **Input:** Usually, you’re given a **truth table**, **verbal description**, or **set of requirements** that define how outputs depend on inputs.
* Ex:
![screenshot-20250729-212455.png](screenshot-20250729-212455.png)
* 
* Now for each 1 in (f) column we will generate a boolean expression for it:
     - For the row 0 it will be --> (NOT(x) AND NOT(y) AND NOT(z))
     - For the row 2 it will be ---> (NOT(x)) AND y AND NOT(z))
     - For the row 4 it will be --> (x AND NOT(y) AND NOT(z))
 - NOTICE THAT EACH ONE OF THESE EXPRESSIONS IS UNIQUE TO ITSELF, MEANS THE FUNCTION WILL NEVER GENERATE 1 IF IT APPLIED TO ANY OTHER ROW.
 - Now how do we combine them ?? we will use **OR** .
 - ![screenshot-20250730-194901.png](screenshot-20250730-194901.png)
 - ![screenshot-20250730-205810.png](screenshot-20250730-205810.png)

### Expressing boolean functions
* Any Boolean function can be represented using an expression containing AND and NOT operation.
* proof: (x OR y) = NOT(NOT(x) AND NOT(y))


* There is 1 operation that can be used to express and compute any function by itself, it's called **NAND**
* NAND: NOT, AND ==> **NOT(x AND y)**
* ![screenshot-20250730-213813.png](screenshot-20250730-213813.png)
* ![screenshot-20250730-214132.png](screenshot-20250730-214132.png)
* We will use **NAND** gates to compute everything and build the complex system just by using it.



---



# Unit 1.3 Logic Gates
* A technique for implementing Boolean functions using logic gates.
* Logic gates:
	* **Elementary** (Nand, And, Or, Not, ...)
	* **Composite** (Mux, Adder, ...)

* *Note:* 
	* There is inputs pins, output pins, internal ones.![Screenshot_20250902_031010.png](Screenshot_20250902_031010.png)

#### Elementary logic gates

* **NAND**
![screenshot-20250730-215237.png](screenshot-20250730-215237.png)
### How is Nand primitive while it's using And ?

That’s a really sharp observation 👌 and it touches the heart of **logic design**.

When we say **NAND is a primitive gate**, we don’t mean it’s literally built out of an AND + NOT inside. It means:

- **In theory:** NAND is _functionally complete_. That means you can build _any other logic gate_ (AND, OR, NOT, XOR, etc.) just by wiring NANDs together. So we treat it as a _primitive building block_.
    
- **In practice (electronics):** A NAND gate is usually built directly from **transistors** (MOSFETs or BJTs), not by first making an AND gate and then adding a NOT.



* **AND**
![screenshot-20250730-215405.png](screenshot-20250730-215405.png)
* **OR**
![screenshot-20250730-215408.png](screenshot-20250730-215408.png)
* **NOT**
![screenshot-20250730-215412.png](screenshot-20250730-215412.png)

* We can use these elementary gates to create composite ones.



#### Composite logic gate - Gate Interface/ Gate Implementation
* For example we can make this **three AND logic gate**, the first picture describes the **gate interface**, the second one describes the **details/ implementation** of it.
![screenshot-20250730-215922.png](screenshot-20250730-215922.png)



#### Circuit implementations 
![screenshot-20250730-220520.png](screenshot-20250730-220520.png)
* *This is very important*: this course will not discuss the physical manners but instead it will focus more on something like the right bottom of the screen (Theories and Implementation).


---




# Unit 1.4: Hardware Description Language

* We will use HDL to build and implement the logic gates.
* HDL is a functional language which means we can start writing our gate logic from anywhere, but for readability --> start from right to left .
* Common HDL languages:
	1) Varilog.
	2) VHDL
* HDL must have 2 things:
	1) Good documentation.
	2) Good names.
### Design: from requirements to gate diagram
* ![Screenshot_20250810_114710.png](Screenshot_20250810_114710.png)
* ![Screenshot_20250810_115540 1.png](Screenshot_20250810_115540%201.png)

* HDL for this will be:
```vhdl
CHIP Xor {

IN a, b;

OUT out;

  

PARTS:

Not(in=a, out=nota);

Not(in=b, out=notb);

And(a=a, b=notb, out=aAndNotb);

And(a=nota,b=b,out=notaAndb);

Or(a=aAndNotb,b=notaAndb,out=out);


}
```


* Note that `in` is input name, `out` is the output variable name, `Not, And, Or, ...` they are like interfaces.

# Unit 1.5: Hardware Simulation

* So it explains how to make an HDL file and test it, --- > pretty much easy, just check re-test the web-based IDE and you will figure it out.


# Unit 1.6: Multi-Bit Buses

* We will work here with the buses which is basically an array of bits, `a[4]` 4-bit bus.

* How would you xor the first and last bits of a 16-bit bus named ‘bus’?

	Xor(a=bus[0], b=bus[15], out=out)  <---

	Xor(a=bus[0], b=bus[16], out=out)

	Xor(a=bus[1], b=bus[15], out=out)

	Xor(a=bus[1], b=bus[16], out=out)


* How summation happened using logic gates:
	1) sum = a xor b xor carry_current
	2) carry_next = a & b + (carry_current & (a xor b))



#### Implementation of Add for 16 bit

* Think of **HDL (Hardware Description Language)** differently from programming:

	- In **software**, you call a function and it _returns_ a value.
	- In **hardware**, you **connect wires**.
    
So when you write:

```h
FullAdder(a=a[0], b=b[0], c=false, sum=out[0], carry=c1);
```
- `sum=out[0]` means: _the `sum` output wire of this FullAdder is physically connected to the wire `out[0]`_.
- The FullAdder internally computes `(a ⊕ b ⊕ c)` and drives that onto its `sum` pin.
- Since `sum` is connected to `out[0]`, now `out[0]` has that value.
That’s why you don’t need to “return” — hardware doesn’t return values, it **propagates signals** through connections.

So later when you say `out[15]`, it already has a value because your chain of FullAdders is driving it.

👉 In short:
- `sum` is just the output pin of the FullAdder.
- `out[bit]` is the wire you connect that pin to.
- Once connected, the value flows automatically.


```hdl
CHIP Add16 {
    IN a[16], b[16];
    OUT out[16];

    PARTS:
    // 16-bit adder built from FullAdder
    FullAdder(a=a[0], b=b[0], c=false, sum=out[0], carry=c1);
    FullAdder(a=a[1], b=b[1], c=c1,    sum=out[1], carry=c2);
    FullAdder(a=a[2], b=b[2], c=c2,    sum=out[2], carry=c3);
    FullAdder(a=a[3], b=b[3], c=c3,    sum=out[3], carry=c4);
    // ...
    FullAdder(a=a[14], b=b[14], c=c14, sum=out[14], carry=c15);
    FullAdder(a=a[15], b=b[15], c=c15, sum=out[15], carry=carry16);
}

```