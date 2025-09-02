---
share: true
---



### 2-to-1 Mux
in a **2-to-1 MUX**:
- Inputs: I0​, I1​ → each can be 0 or 1.
- Select line: S → decides which input goes to the output, it will the `log base 2 (inputs)`
- Output: Y → copies whichever input is selected.
* `Number of Inputs = 2^n number of selector ` and `Number of selectors = log2(number of inputs)`


![Screenshot_20250902_025313.png](/OSSU/core_system/Build-a-Modern-Computer-from-First-Principles-From-Nand-to-Tetris-Project-Centered-Course-Tets/enveloppe/pictures_folder/Screenshot_20250902_025313.png)

* Equation:
`Y=(S′ ⋅ I0)+(S . I1) ---> (Not S and I0) or (S and I1)`

Break it down:
1. **S′** means "NOT S" →
    - If switch = 0 → S′=1 (true).
    - If switch = 1 → S′=0 (false).
2. **(S′ ⋅ I0)** means:
    - Only when the switch is 0, take I0.
    - Otherwise, ignore I0.
3. **(S ⋅ I1)** means:
    - Only when the switch is 1, take I1.
    - Otherwise, ignore I1.
4. Finally, the **+ (OR)** says:
    - Combine them → you only get whichever one the switch points to.
        

---



### 1-to-2 Demultiplexer

* Instead of choosing one input from multiple one using the selector, here we have 1 input and the selector chooses which output the input will go to .
* `Number of output = 2^n number of selector ` and `Number of selectors = log2(number of output)`


* ![Screenshot_20250902_025149.png](/OSSU/core_system/Build-a-Modern-Computer-from-First-Principles-From-Nand-to-Tetris-Project-Centered-Course-Tets/enveloppe/pictures_folder/Screenshot_20250902_025149.png)
* So:
	* Say: `Input, output1,output2, S (selector)`
		* If S == 0:
			* then: output1 = input
		* else:
			* output2 =input
* Equations:
	`output1 ​= Input ⋅ NotS`  
	`output2​=Input ⋅ S`

---

### 4-to-1 MUX

* ![Screenshot_20250901_231944.png](/OSSU/core_system/Build-a-Modern-Computer-from-First-Principles-From-Nand-to-Tetris-Project-Centered-Course-Tets/enveloppe/pictures_folder/Screenshot_20250901_231944.png)
*  Logic equation:
	* `Y=(S1′⋅S0′⋅I0)+(S1′⋅S0⋅I1)+(S1⋅S0′⋅I2)+(S1⋅S0⋅I3)`
* If u notice from the table that sel2 is 0,1,0,1 , so you can do the first two together and last two together, then you can combine the result with the sel1 .
 ```C
 CHIP Mux4Way16 {

IN a[16], b[16], c[16], d[16], sel[2];

OUT out[16];

PARTS:

//// Replace this comment with your code.

Mux16(a=a, b=b, sel=sel[0], out=ab);

Mux16(a=c, b=d, sel=sel[0], out=cd);

Mux16(a=ab, b=cd, sel=sel[1], out=out);

}
 ```


### DMUX4Way

![Screenshot_20250902_024257.png](/OSSU/core_system/Build-a-Modern-Computer-from-First-Principles-From-Nand-to-Tetris-Project-Centered-Course-Tets/enveloppe/pictures_folder/Screenshot_20250902_024257.png)


### DMUX8Way
![Screenshot_20250902_024650.png](/OSSU/core_system/Build-a-Modern-Computer-from-First-Principles-From-Nand-to-Tetris-Project-Centered-Course-Tets/enveloppe/pictures_folder/Screenshot_20250902_024650.png)![Screenshot_20250902_025055.png](/OSSU/core_system/Build-a-Modern-Computer-from-First-Principles-From-Nand-to-Tetris-Project-Centered-Course-Tets/enveloppe/pictures_folder/Screenshot_20250902_025055.png)
