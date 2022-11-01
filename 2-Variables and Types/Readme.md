# Java Variables and Types
## Disceeting Hello World
public class HelloWorld {

  public static void main(String []args){  
  
          System.out.println("Hello World"); 
          }  
  }  
### What is public static void main ?  
* public ---> Accessible to everyone  
* static ---> Not associated with an instance ( The thing becomes the property of class itself)  
* void   ---> Method does not return anything  
* main   ---> Special method name that indicates in a java program that it can start the execution of a program  

## VARIABLE DECLARATION
int age;  // Declaration  
double price = 10.5; //  Declaration and assignment  
int count,sum; // Multiple declaration  

var age = 25; // Compiler figures out the type on it's own, it is gonna make this int  
var price = 10.5; // It's gonna make this double  
The right side is needed because java compiler must know the right side to figure out the type of the var.

## VARIABLE ASSIGNMENT
age = 25;  
price = 75.50;

## DECLARATION AND ASSIGNMENT
var salary = 500; // Compiler figures out that the var is int

## TYPES  
### WHAT ARE THE PRIMITIVE TYPES IN JAVA?
* byte
* short                  
* int
* long
* float     
* double(longer float)
* char
* boolean

#### int
32 bit signed two's compliment(1 sign bit and 31 value bits)  
max --> 0.2^31  
min --> 1.2^31  
#### float
32 bit floating point
#### long
64 bit two's complement
#### double
64 bit floating point

## LITERALS
It is a way to specify value inline.  

**int literals**  
int age = 25 ; value is literally in the code. This is a literal  
int count = 0b101010; // You can also specify a binary format.You can specify the 2's complement binary value.  
0 is the sign, b is the byte, the rest is the value 42.  
int price = 25_000; // You can do integer literals like this.To make it easier to read  

**double literals**

double price = 25.75;  
double coeff = 23_456.70_01;  
double val = 5.012E15; // We can specify it using the exponent. This exponent value can be positive and negative.  

double price = 25D; // Price here happens to be a whole number, we are forcing it to be a double.  
But imagine if this double was var, and the compiler had to infer what the right answer was for the number.  
By specifying the D here we are telling hey compiler this looks like a whole number but i want this to be a double.  
So take this D. But here because we specified the double , D is redundant.

**boolean literals**

boolean isCourseAwesome = true;  

boolean amConfused = false;  

**char literals**  

char x = 




