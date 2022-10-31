# UNIT 1 - THE JAVA LANGUAGE
Java is initiated by
* James Gosling (Father of the Java)
* Patrichk Naughton
* Chris Warth
* Ed Frank
* Mike Sheridan

## PRIMARY GOAL OF JAVA
* Platform Independence (Back in the days this was not common)
* Write Once, Run Anywhere !

THE JAVA MODEL

.java --> Source files

.class --> bytecode (runs everywhere because jvm turns it into .java)

In Java we are not creating machine level code to run directly on a machine, we are
creating a byte code(.class) to run on a virtual machine.This virtual machine is runtime.

## What is the difference between JDK,JRE and JVM ? 

### JAVA DEVELOPMENT KIT(JDK)

#### Java SDK

Contains compiler and other tools to build Java applications. Not necessary to run Java programs, necessary for developers. JDK comes with runtime.

### JAVA RUNTIME ENVIRONMENT(JRE)

* Required to run Java applications. Runs bytecode on the machine that is on(Different for every machine:windows,mac,linux..)
* Language agnostic(It does not matter what the language code was written in)
* Contains standalona JVM.
* JVM is a program that runs bytecode.

### JAVA VIRTUAL MACHINE(JVM)

* Runs on a computer any program thats compiled to bytecode.
* It acts like an abstract "virtual" computer.
* Has byte code loader, verifier and interpreter.
* Can convert bytecode to machine specific code at the last minute.

#### WHAT IS JAVA BYTE CODE ? 

Instruction set meant for execution by the JVM (Optimized for JVM)

##### ADVANTAGES OF JAVA BYTE CODE
* Write once run anywhere
* Security - JVM acts as a sandbox ( Your code can not harm the actual machine)

##### DOES'NT IT MAKE THINGS SLOW ?

Thanks to the jit compiler, it does not make things slow.

##### THE JUST IN TIME COMPILER

It can potentially convert from byte code to machine code.Before the execution, Just In Time compiler converts the byte code to machine code at the last moment. So, if there are 100 executions of that bytecode, jit converts bytecode to machine code, and then the executions start. Machine code is super fast.

Selective optimization that jvm does to convert byte code into direct machine level
code that runs on the barebone machine.

##### THREE WAYS TO RUN JAVA BYTECODE
* Interpret the intermadiate byte code directly
* Just before executing, compile to native code (JIT)

Why not compile it to native code for the all application, then run it natively?
* Convert intermediate code fully to native code before execution ( Ahead of Time Compilation)Ahead of execution is possible with Java 9.

## FIVE MAIN GOALS OF JAVA
1. It must be simple, object-oriented and familiar.
2. It must be robust and secure.
3. It must be architecture-neutral and portable. (Developer should not have to care in what system the code will be run).
4. It must execute with high performance. JVM today has been optimized to such an 
extent that it almost runs equally or in many cases even runst faster than the c,c++ was compiled down to.
5. It must be interpreted, threaded and dynamic.

JSHELL ---> Is a prototype code place. Kinda like matlab.




