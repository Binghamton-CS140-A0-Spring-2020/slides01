# slides01

-----------------------------
**CS 140 Programming with Objects and Data Structures**

-----------------------------

**Introduction**

**Main Course Resources**
- Start at http://bingweb.binghamton.edu/~lander
- That page has a link to “Programming with Objects and Data Structures”
- TO DO: Download and install a Java JDK
 - You can use Corretto, which we have in the labs: 
 <a href="https://docs.aws.amazon.com/corretto/latest/corretto-11-ug/downloads-list.html" target="blank">Amazon Corretto 11</a>. 
 Since it is free and supported by Amazon, our labs will have have this one.
 - You might use Java 13 (openJDK) Development Kit (Java SDK): https://jdk.java.net/13/
 - You could choose the commercial version from Oracle: it is free when you use it for 
 personal use: https://www.oracle.com/technetwork/java/javase/downloads/index.html
- IMPORTANT: On Windows (if you do not use Corretto, which kindly does it for you) you need to get the path to the java `bin` directory into your path. 
 (on Mac and Linux it is either automatic or needs a different procedure)
 - For Windows with openJDK or Oracle, right click on `This PC` and select `Properties`, then on the left side of the System Window, click 
on `Advanced Systems Settings`.
 - In the `System Properties` dialog, click on `Environment Variables...` near the bottom.
 - Click on `Path` in the *LOWER* window (System variables) and click the `Edit` button near the bottom.
 - If you chose Amazon Corretto, you should find that the Path was modified during the install: 
 `C:\Program Files\Amazon Corretto\jdk11.0.3_7\bin` (or maybe a later version number). If it is there just use Cancel to exit this whole process.
 - If you chose the OpenJDK, you need to click the `New` button and paste in the path to `javac`, probably 
 `C:\Program Files\jdk-13\bin`--but you need to check in the file explorer. Then click `OK` on each window and close the System window.
 - If you chose the Oracle, you need to click the `New` button and paste in the path to `javac`, probably 
 `C:\Program Files\Java\jdk-13.0.1\bin`--but you need to check in the file explorer.. Then click `OK` on each window and close the System window.
 - Any problems, bring your computer to Lab or office hours.
- TODO for Windows: Download and install Git Bash form this <a href="https://git-scm.com/downloads" target="blank">download page</a>.
Use the defaults (on Mac and Linux it should be installed). 
Typing Git Bash in the search field of Windows with open a Git terminal window, where you can 
clone the same repository you use in Lab. You can repeat the instructions from Lab.
- TODO for Windows: Download and install Gedit for Windows from the <a href="https://wiki.gnome.org/Apps/Gedit#Download" target="blank">Gedit download page (the Windows 64-bit binaries)</a>. We will be using Gedit in the labs.
- TODO If you do not have a GitHub account, go to GitHub (https://github.com/) and sign up. 
Once you have signed up for an account, fill out and submit this <a href="https://docs.google.com/forms/d/e/1FAIpQLScY7jaNu5EQBvSgBYviebTIfU-sXctDjsooiAT2joM7SzCMNQ/viewform" target="blank">Google Form</a>
so we can get you into the GitHub classroom.

**Course Information Page is important**
- Go to: <a href="http://bingweb.binghamton.edu/~lander/cs140/HomePageFiles/info.html" target="blank">Info Page</a>
- There are many important things to read there and we will review them in the next class.
- Unless otherwise noted, assignments are individual assignments. This means that all work submitted will have been done by you.

-----------------------------
**Writing Programs**

-----------------------------

**Programming**
- The kind of programming we are doing uses the following:
 - We need to work with variables
 - We need to give them values (assignment)
 - We need conditional statements
 - We need loops
 - We need functions
- This is called imperative programming

- On top of that we organize code in classes and a running program has a number of 
instances of the classes (objects) that are interconnected during execution and they call each 
other's methods—OO programming

**Classes**
- All Java code goes inside some class:

```java 
public class Example 
{
	...
}
```

- Note that when I use Eclipse, later in the course, I prefer to keep the opening brace on the previous line

```java 
public class Example {
	...
}
```

but with a plain text editor this layout is easier to type to ensure the braces balanced correctly.

- Usually we group classes into packages (not mentioned in Chapter 3 of the textbook)

```java
package lab01;
public class Example 
{
	...
}
```

- Next we need to put fields and methods in the class

**Declaring variables**
- Many imperative languages, including Java, require that variables be
 - Declared
 - Initialized

 before they may be used. These are compiled languages and the compiler checks the variables are used correctly
- Declaration and initialization can be combined.
- NOTE: we shall see that "reference variables" also need to be instantiated as part of the initialization

**Primitive Types**
- There are 8 primitive types that are similar to the variables in the C language

```java
int value =  1; // declaration and initialization
int input; // declaration 
// later
input = 5; // this could be the initial value
	// or a change of value
char letter = 'g';
char aKoreanChar = '\ud55c';    //  한 
long large = 1234567890123456789L;
boolean choice = false;
double precipAug = 3.59;
float precipJuly = 2.69F;
byte tiny = (byte)110; // values from -128 to 127
short small = (short) -25000; // from -32768 to 32767
```

- Writing (byte)110 is a *cast* or *type cast*. We cast the int 110 as the type byte and in this case a 
value stored in 32 bits is changed to one stored in 8 bits (`00000000000000000000000001101110` to `01101110`). 
The (short)-25000 *cast* changes `11111111111111111001111001011000` to `1001111001011000`


**Range of values of each Primitive Type**
- See the table of number types in Section 4.1 for all the ranges
- We have now seen all of Java's 8 primitive types, all other types are reference types

**Object Oriented Programming**

- In object-oriented programming we develop a way to break up code into classes and create run-time objects from those classes.
- A program consists of a number of interacting run-time objects. 
- The *type* of a reference variable is a key concept and there are two kinds of types associated with the variable: the *static* type and the *dynamic* type, which we explore a bit later

**Example from Chapter 3 of Big Java 7th edition Section 1**
- <a href="http://bcs.wiley.com/he-bcs/Books?action=index&itemId=1119499097&bcsId=11274" target="blank">Resources for the textbook</a>
- <a href="http://bcs.wiley.com/he-bcs/Books?action=resource&bcsId=11274&itemId=1119499097&resourceId=44689" target="blank">Link to the source code</a>
- Notice the *javadoc* comments in the code examples.
- Private fields, public methods are typical in Java programming.

```java
package ch03.sec01; 
/** 
 * This class models a tally counter. 
 */ 
public class Counter 
{ 
    private int value; 
    /** Gets the current value of this counter. 
     * @return the current value 
     */ 
    public int getValue() 
    { 
        return value; 
    } 
    /** 
     * Advances the value of this counter by 1. 
     */ 
    public void click() 
    {
        value = value + 1;
        // in future we write value++; 
    } 
    /** 
     * Resets the value of this counter to 0. 
     */ 
    public void reset() 
    { 
        value = 0; 
    } 
} 
```

- INDENTATION is extremely important for readability. I have seen students be unable to compile their code in an exam just because they did not indent it and could not figure out the matching braces.
- The code beneath any opening brace must be indented a few spaces or 1 tab. Code under a closing brace goes at the same indentation as the closing brace. The brace closing an opening brace must be vertically aligned with the matching brace.
- Driver class

```java
package ch03.sec01;
public class CounterDemo 
{
    public static void main(String[] args) 
    {
        Counter tally = new Counter();
        tally.click();
        tally.click();
        int result = tally.getValue(); // Sets result to 2  
        System.out.print("result: ");
        System.out.println(result);
        System.out.println("Expected: result: 2");
    }
}
```

- Chapter 3 also has a simple `BankAccount`
- For future clarity, the first constructor is called a *no-argument constructor*, or *no-arg constructor*.
- In CS 140, let's call the second constructor an *initialization constructor*, or *init-constructor* 
to indicate that is has parameters used to *initialize* the fields of the object.
- In CS 140, let's call a constructor that only initializes *some* of the fields of the object a 
*partial initialization constructor*, or *part-init-constructor* to indicate that is has parameters 
used to *initialize* the fields of the object but *not all* the fields. We will see examples later in the class.

```java
package ch03.sec04;
/**
 * A bank account has a balance that can be changed by 
 * deposits and withdrawals.
 */
public class BankAccount 
{
	private double balance;

	/**
	 * Constructs a bank account with a zero balance.
	 */
	public BankAccount() 
	{
		balance = 0;
	}

	/**
	 * Constructs a bank account with a given balance.
	 * @param initialBalance the initial balance
	 */
	public BankAccount(double initialBalance) 
	{ 
		balance = initialBalance;
	}

	/**
	 * Deposits money into the bank account.
	 * @param amount the amount to deposit
	 */
	public void deposit(double amount) 
	{
		balance = balance + amount;
		// in future we write balance += amount;
	}

	/**
	 * Withdraws money from the bank account.
	 * @param amount the amount to withdraw
	 */
	public void withdraw(double amount) 
	{
		balance -= amount;
		// means balance = balance - amount;
	}

	/**
	 * Gets the current balance of the bank account.
	 * @return the current balance
	 */
	public double getBalance() 
	// this is called a "getter method"
	{
		return balance;
	}
}
```

- Driver class

```java
package ch03.sec04;
/**
 * A class to test the BankAccount class.
 */
public class BankAccountTester 
{
	/**
	 * Tests the methods of the BankAccount class.
	 * @param args not used
	 */
	public static void main(String[] args) 
	{
		BankAccount harrysChecking = new BankAccount();
		harrysChecking.deposit(2000);
		harrysChecking.withdraw(500);
		System.out.println(harrysChecking.getBalance());
		System.out.println("Expected: 1500");      
	}
}
```

**Reference Types**
- We can declare reference variables from developer-defined classes or from classes in the Java library:

```java
ch03.sec01.Counter myCounter;
ch03.sec04.BankAccount myAcc;
String str; // java.lang.String
java.awt.Rectangle rectang;
java.io.PrintWriter output;
```

- Reference variables need to be instantiated:

**Instantiation – calling constructors**

```java
ch03.sec01.Counter myCounter = new ch03.sec01.Counter();
ch03.sec04.myAcc = new ch03.sec04.BankAccount(150.0);
String str = "My String";
// equivalent to String str = new String("My String");
java.awt.Rectangle rectang = new java.awt.Rectangle(10,30,25,60);
java.io.PrintWriter output = new java.io.PrintWriter("out.txt");
```

- There is never a need to mention the package `java.lang` but putting in the package 
names `ch03.sec01`, `ch03.sec04`, `java.io`, `java.awt` is a nuisance, so we *import*

**Importing packages**

- To avoid putting package names through all the code, we use import

```java
package sample;
import ch03.sec01.Counter;
import ch03.sec04.BankAccount;
import java.awt.Rectangle;
import java.io.FileOutputStream;
import java.io.PrintWriter;
public class Example 
{
	Counter myCounter = new Counter();
	BankAccount myAcc = new BankAccount(150.0);
	String str = "My String";
	Rectangle rectang = new Rectangle(10,30,25,60);
	// need to instantiate output inside a method
	// since opening a file can throw an exception
	...
}
	// Instantiate `output` in the main method because of the Exception:
```

- We have to provide a context where an `Exception` can be thrown for the instruction `new File(out.txt")`

```java
package notes;
import java.awt.Rectangle;
import java.io.FileNotFoundException;
import java.io.PrintWriter;
import ch03.sec01.Counter;
import ch03.sec04.BankAccount;

public class Example 
{
	Counter myCounter = new Counter();
	BankAccount myAcc = new BankAccount(150.0);
	String str = "My String";
	Rectangle rectang = new Rectangle(10,30,25,60);

	public static void main(String[] args) 
		throws FileNotFoundException 
	{
		PrintWriter output = new PrintWriter("out.txt");
	}
}
```

- Object oriented programming provides a way to do data encapsulation 
(putting the operations that work on data together with that data) and information hiding 
- See <a href="http://en.wikipedia.org/wiki/Information_hiding" target="blank">Wikipedia: Information Hiding</a>
- Both are intended to isolate changes in code so that as one part is developed, you do not need to keep changing the parts that are done

**Textbook Chapter 1**
- Chapter 1 describes that a computer runs by executing machine code. 
- Machine code is not readable by humans: it is just a long string of 0’s and 1’s that is read in short chunks of fixed length (e.g. 32 bits at a time)
- Sun Microsystems (later bought by Oracle) decided to use the principle of virtual machine for Java:
- The Java program (`.java` files) is converted to a class file (.class files) by running the compiler, e.g.
 - `> javac  -d  .  Counter.java`
 - `> javac  -d  .  CounterDemo.java`
 
- Note that it soon becomes easiest to type
 - `> javac  -d  .  *.java`
although this command is *not* guaranteed to compile all files. If some have errors, it may stop along the way.
 
**Class files**

- A class file went into the directory `ch03.sec01`, it contains machine code for a theoretical machine (called a virtual machine)
- There is another program called the Java Virtual Machine (the JVM) for most operating systems. Really these are JVM emulators—programs that simulate the action of the theoretical machine
- That virtual machine emulator (JVM) is started by typing `java` and the program immediately looks for the file you wish to execute, e.g. `CounterDemo.class`:

 - `> java ch03.sec01.CounterDemo`

 we do not put `.class` at the end of the file name when calling `java`.
- The `java` program can only begin by running a method called 
 `public static void main(String[] args)` in `CounterDemo.java`
- Only the name `args` can be changed to some other identifier and the bracket `[]` could move to appear after `args`.
 `public static void main(String something[])`
 
**Benefit of the virtual machine**
- Once you use the JVM concept, you can run the same class files on any computer
- In contrast, traditionally C, C++, Fortran and many other programs must be compiled separately to 
run on Solaris, Linux, Windows, Mac OS, etc.
- Microsoft's .NET platform is a similar idea to the JVM but more powerful and multi-language. 
- Microsoft now supports open source cross platform .NET: <a href="http://www.mono-project.com/" target="blank">the Mono Project</a>
- It was started independently as explained in the History section of the <a href="https://en.wikipedia.org/wiki/Mono_(software)" target="blank">Wikipedia article</a>

**Writing the code**
- The code of the file `Counter.java` is called the source code of the program. 
- It must be written with an editor that produces plain text. If no other 
editor is installed, we use Notepad on Windows, or some Java editing tool 
like Eclipse on Windows but you can install Gedit or Notepad++ on Windows. We use gedit, vi or emacs or the same tool such as Eclipse on Linux.
- Just as an experiment, try writing the file in Word and saving it as a `.docx` file. Then, change the extension to `.java` and see what the compiler does with it!--It will not like it.

**You must test your code**
- Getting the code written and compiled is only one of the earliest steps. 
- It is common for professional developers to write the tests before they write the code.
- You must test your code to see if it does what you expected. See Section 2.7 of the textbook.
- You are very strongly recommended to write the *javadoc* documentation, explaining what the code does, FIRST (Section 3.2)
- As the textbook says: "If you can't explain what a class or method does, you aren't ready to implement it" 

-----------------------------
**Syntax**

-----------------------------

**Mostly like C, not the same as Python**

**Simple statements end with semicolons**

- Arithmetic assignments

```java
z = (x + y) * z / 17;
```

- Trigonometric assignments

```java
opp = hypot * Math.sin(angle);
```

- Assignment to a reference variable

```java
title = "Mississippi".substring(0,4);
```

- Calls to methods

```java
rectang.translate(20,35);
System.out.println("Mississippi");
```

- Indentation and layout is not important to the compiler, only to YOU, the writer and ME (or a TA) the reader

```java
package notes;
import java.awt.Rectangle;
public class Notes01Ex1
{
	public static void main(String[] args) 
	{
		int x = 1;
		int y = 3;
		int z = 5;
		z = (x + y) * z / 17;
		
		System.out.println(z);
		System.out.println("Expected: 1");
		
		// compare
		
		System.out.println((1 + 3) * 5.0 / 17);
	        System.out.println("Expected: 1.1764705882352942");

	        System.out.println((1 + 3) * 5 / 17F);
	        System.out.println("Expected: 1.1764706");
		
		double hypotenuse = 5;
		double angle = Math.PI/4.0;
		double opposite;
		opposite = hypotenuse * Math.sin(angle);

		System.out.println(opposite);
	        System.out.println("Expected: 3.5355339059327373");
		
		// compare
		
		System.out.println(5/Math.sqrt(2));
	        System.out.println("Expected: 3.5355339059327373");

		String title = "Mississippi".substring(0,4);
		
		System.out.println(title);
	        System.out.println("Expected: Miss");

		Rectangle rectang = new Rectangle(12,20,15,17);
		
		System.out.println(rectang);
	        System.out.println("Expected: java.awt.Rectangle" 
				+ "[x=12,y=20,width=15,height=17]");
		
		rectang.translate(20, 35);
		
		System.out.println(rectang);
		System.out.println("Expected: java.awt.Rectangle" 
				+ "[x=32,y=55,width=15,height=17]");

		// the Java compiler does not care about the end 
		// of line or indentation (but YOU should):
		
		double z1 = (x + 
	y
	       ) 
* 
5 
             /  17
             ;

		System.out.println(z1);
		System.out.println("Expected: 1.0");

		String title1 = "Mississippi"
				.substring(4
	,6);

		String title2 = "Mississippi"
				.
				substring(6
						,9
)
						;

		System.out.println(
				title1
			);
		System.out.println("Expected: is");
		System.out.println(title2);
		System.out.println("Expected: sip");

		// The double-quotes around a String literal must begin and end
		// on the same line
		String str = "This is a long String spread over several "
				+ "lines but it must be broken down into several "
				+ "shorter Strings that are each on a single line. "
				+ "The plus sign \"+\" is used to concatenate "
				+ "these shorter String literals together. "
				+ "We use the term 'literal' for things that "
				+ "represent their own value in the source code";

		/* Java 13 will be testing block text, this will not compile 
		in Java 11 or Java 12 but will work in Java 13 with the --enable-preview
		option (example from https://dev.to/vojtechruz/java-13-text-blocks-6nb):
		String html = """
                  <html>
                    <body>
                      <p>Hello, world</p>
                    </body>
                  </html>
                  """;
		*/
		System.out.println(str);
	}
}
```
- As explained in <a href="https://dev.to/vojtechruz/java-13-text-blocks-6nb" target="blank">Text Block link</a> the current proposal is to store the indentation relative to the first line of the block.
- Look back at the code of BankAccount, which shows you can choose to have more than one constructor
- While in the code of Counter there is no constructor but one gets provided--in this case a no-argument constructor--so we can write `myCounter = new Counter();`

-----------------------------
**Control Flow** 

-----------------------------

**if statements - 1**

- Simplest: `if` without alternative branches

```java
if(myAccount.getBalance() > 1000) 
{
	System.out.println("I'm rich");
	myAccount.withdraw(100.0);
	System.out.println("Let's go out");
}
```

- For more information read the start of Chapter 5

**Python indentation turns into curly-braces**

- The C, C++, Java, PHP, Javascript, ... family do not use indentation for grouping. 
It is VERY STRONGLY recommended to make code readable

```python
# Python
if x < y:
	------	
	------	
	------	
	------
```

```java
// Java
if(x < y) 
{
	------
	------	
	------	
	------
}
```

- indentation is for readability and making sure opening and closing braces match
 
**if statements - 2**

- `if` with one alternative using `else`

```java
if(an expression that is true or false) 
{
	statement
	statement
	...
} 
else 
{
	statement
	statement
	statement
	...
}
```
 
**if statements - 3**

- `if` without multiple alternative branches using `else if`

```java
if(an expression that is true or false) 
{
	statement
	...
} 
else if(an expression that is true or false)
{
	statement
	...
}
else if(an expression that is true or false)
{
	statement
	...
}
else 
{ // this else is optional
	statement
	...
}
```
 
**while loop**

- Let's use the correct name for "...an expression that is true or false." The name is *Boolean* expression.
- We use boolean-expr to indicate "any Boolean expression can go here." See Section 5.7
- `while` syntax:

```java
while(boolean-expr) 
{
	statement
	statement
	...
}
```

**do-while loop**

- Ensures one execution of the loop body.
- Is the only compound statement that has to end with a semi-colon because
the controlling logic comes after the closing brace of the loop

```java
do 
{
	statement
	statement
	...
} while(boolean-expr);
```

- Read Chapter 6 for the syntax and examples of while loops and for loops.

**for loop**

- `for` syntax:

```java
for(initialize ; boolean-expr ; increment) 
{
	statement
	statement
	...
}
```

- where initialize is used to initialize and usually declare variables used in the loop. There could be other instructions that are executed once before the loop starts
- and increment is used to change variables at the end of every execution of the loop. Most often, it increments a counter
- the boolean expression is checked before each iteration of the statements in the body of the loop. If the expression is false, execution jumps to the next instruction after the loop. In the case that the loop is at the end of a method, then when the expressiomn is false, execution returns to the place where the method was called.

**Some items in Chapters 2 and 3**
- First, remember to put a link to the Java API on the bar of links in your Browser:
<a href="https://docs.oracle.com/en/java/javase/11/docs/api/index.html" target="blank">Java 11 API</a> or 
<a href="https://docs.oracle.com/en/java/javase/12/docs/api/index.html" target="blank">Java 12 API</a>
- If you are trying our Java 13, then 
<a href="https://docs.oracle.com/en/java/javase/13/docs/api/index.html" target="blank">Java 13 API</a>

- Get used to finding things on the API website

```java
String river = "Mississippi";
int len = river.length( );
String river2 = river.toUpperCase( );
String river3 = river.replace("issipp", "our");
System.out.println(river);
System.out.println("Expected: Mississippi");
System.out.println(len);
System.out.println("Expected: 11");
System.out.println(river2);
System.out.println("Expected: MISSISSIPPI");
System.out.println(river3);
System.out.println("Expected: Missouri");
```

- There is no method that is called on a String varaiable that changes the variable. Only assignment to a new value can change a String variable.

**Chapter 3 describes the syntax of classes**

```java
package notes;
/**
 * Example2 has 2 private instance fields, an initialization constructor
 * and an included main method for testing. When the main method is inside the 
 * class it is testing, it has access to the private fields of objects of
 * the class that are created in the main method.
 */
public class Example2 
{
	private String river;  // fields are called instance
	private int len;       // variables in the textbook

	/**
	 * Constructor takes a river name as input and
	 * initializes the two fields
	 * @param aRiver the name of the river for 
	 * this example object
	 */
	public Example2(String aRiver) 
	{
		river = aRiver;
		len = river.length( );
	}
	/**
	 * The main method for testing
	 */
	public static void main(String[] args) 
	{
		var test = new Example2("Mississippi");
		var length = test.len;
		/* Comment: before Java 9, this needs to be
			Example2 test = new Example2("Mississippi");
			int length = test.len;
		*/
	}
}
```

**The Call Stack**

- *Parameters* and *local variables* are stored in an area of memory called the *call stack*. In the main method above, `args` is a *parameter*, `test` and `length` are local variables. The string `"Mississippi"` is an *argument*. For the 
object `test`, `test.len` is an *instance field* of the object.
- In the constructor `aRiver` is the *parameter*, and the lines

```java
river = aRiver;
len = river.length( );
```
 show that the constructor has access to the *instance fields* inside the *instance* of the class that is being 
constructed (also called an *object* of the class).
- Parameters and local variables are stored in the *call stack*. Here is the call stack just before the constructor call ends.![](https://www.cs.binghamton.edu/~lander/cs140/CallStack1.JPG)

- Here is the call stack just after the call to the constructor has ended and returned to the `main` method

![](https://www.cs.binghamton.edu/~lander/cs140/CallStack2.JPG)

- Here is the call stack after executing the last instruction in `main` (just before the program ends)

![](https://www.cs.binghamton.edu/~lander/cs140/CallStack3.JPG))

- A *primitive* variable is the program's name for a location in computer memory
- *Values* of the primitive variables are stored at those memory locations.
- These variables are stored in the activation records in the call stack
 if they are *parameters* or *local variables*. They are stored in *objects* if they are instance fields.
- Reference variables are also stored in the call stack or in objects but the *values stored there are references to (the addresses of) the objects that are stored at other places in memory*
- The Textbook does show the objects and the reference arrows to the objects.
- Horstmann has decided not to complicate the diagrams with the call stack
- Page 480 is one of the few diagrams in the book, where he shows one object with references to other objects

**Reference**

- Reference variables occur in other languages. 
- C# and C++ also have "reference types."
- However C++ also has "pointer types" (as does the C language), where the value of the address itself can be directly modified (e.g. incremented to point at the following memory location).
- C++ is a substantially more complex language than Java and is used in CS 240. (You should take Math 314 or Math 330 when or before you take CS 240).
