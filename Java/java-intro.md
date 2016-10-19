## Java

> Objectives
> ### What's Java?
> ### Characteristics of Java
> ### Java Development Kit (JDK)
> ### Java program anatomy
> ### Programming Style and Documentation
> ### Programming Errors
> ### Java Arch  

### What's Java?
- A general purpose programming language.
- The Internet programming language.

### Characteristics of Java
- Simple  
    Partially modeled on C++,but simplified and improved
- Object-oriented  
    Providing flexibility,modularity,clarity,and reusablity through encapsulation,inheritance,and polymorphism.
- Distributed  
    Java is designed to make distributed computing easy. Since networking capability is inherently integrated into Java, writing network programs is like sending and receiving data to and from a file.
- Interpreted  
    Java programs are compiled into the Java Virtual Machine code called bytecode. The bytecode is machine-independent and can run on any machine that has a Java interpreter, which is part of the Java Virtual Machine (JVM).
- Robust  
    Java has eliminated certain types of error- prone programming constructs found in other languages
    a runtime exception-handling feature
- Secure  
    Several security mechanisms implemented to protect your system against harm caused by stray programs.
- Architecture-Neutral Portable  
    Run on JVM on any platform
- Multithreaded
- Dynamic  
    New code can be loaded on the fly without recompilation.New features can be incorporated transparently as needed.

### Java Development Kit (JDK)
- Java Standard Edition (J2SE)  
    Develop client-side standalone applications or applets(Java programs that work on web pages)
- Java Enterprise Edition (J2EE)  
    Develop server-side applications
- Java Micro Edition (J2ME)  

### Java program anatomy
- Class name  
    At least one class,each has a name.Class names start with an uppercase letter.
- Main method  
    A class must contain a method named main to executed from.
- Statement  
    Representing actions.
- Statement Terminator  
    A semicolon following every statements.
- Reserved words  
- Blocks  
    A pair of braces.

### Programming Style and Documentation
- Appropriate Comments  
    Key features,supporting data structures,class section,etc.
- Naming Conventions  
    Choose Meaningful and descriptive names.
    Capitalize the first letter of each word in the name.
- Proper Indentation and Spacing Lines  
    Block line to separate segments of the code.
- Block Styles  
    Use end-of-line style for spaces instead of next-line style.

### Programming Errors
- Syntax Errors  
    Detected by the compiler
- Runtime Errors  
    Cause the program to abort
- Logic Errors  
    Produces incorrect result

### Java Arch  
1. Created the source code(the java files);
2. Compiled into Byte code(the class files) with Java Compiler;The compile-time ends;
3. Class Loader get the Byte code;With information from Java Class Libraries,Byte code Verifier sends the Byte code into Java Interpreter or Just-In-Time Compiler of the JVM(Java Virtual Machine);
4. Byte code is interpreted or compiled into machine code and sent to Runtime System of the JVM;
5. The JVM perform the operations of the code on Hardware by controlling the Operating System.  

![see the java-arch](https://github.com/TheSummerX/Notes/tree/master/Java/java_arch.png.jpg/ java-arch)

### The End

