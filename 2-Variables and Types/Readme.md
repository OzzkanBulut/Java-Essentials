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

**Boolean Literals**

boolean isCourseAwesome = true;  

boolean amConfused = false;  

**Char Literals**  

char x = 'x';  

**String Literals**  

String name = "Özkan";  

**JAVA IS A STRONGLY TYPED LANGUAGE**  

## STRONGLY TYPED  

int number = "three"; --> You can not do that. Java is type safe.  

Every variable has a type(Static typing --> Types decided at compile time)  

**What is static typing ?**  
You get to choose the type of the variable only when you are writing code and you don't get to change it.

## STRONGLY TYPED  

type varName = value --> Type and value must be compatible  

## TYPE CONVERSIONS  

double number = 12;  

**CONVERSION IN NUMBER TYPES**  
**PRIMITIVE TYPE CONVERSION**  

int a = 10;  
double b = a; --> This works. Double is 64 bit, int is 32 bit. So double can hold a int itself.  

double a = 10.5;  
int b = a;  
This will not work. You can not assign a 64 bit variable into a 32 bit variable. In this case b is not as capable as holding all the values of a. Every it can be held in a double but doubles can not be held in an int.  

**TYPE CONVERSION WORKS WHEN**  
- Compatible types  
- Destination is larger than the source  

**SOME TYPE CONVERSION EXAMPLES**  
- short to int
- byte to int (smaller to higher)  
- float to double  

## CASTING  

Compiler will not do it automatically but you can force the compiler to do the conversion. Do casting when you **KNOW** conversion is okay.  

**TYPE CASTING**  

double a = 10;  

int b = a ; --> Does not Work !  

int b = (int) a; --> Force convert double a to int. That Works !(Provided that runtime can safely convert it. Destination is larger than or equal to source)  

**CASTING WITH LOSSY CONVERSION**  

double a = 10.5;  

int b = a ; --> Does not Work!  

int b = (int)a; --> It works! But since we took the integer value of a, value of b will be 10.This is called lossy conversion. We just lost the fractional value!  

**CASTING OBJECT REFERENCES**  

**What is casting?**  
A way for us to force conversion from one type to another.  

## PRECISION LOSS

int a = 4/2; --> a is 2  

int b = 3/2; --> b is 1, precision loss!  

double c = 3/2;  
**Java always read the right end side values first.** So, java first calculates the integer value of 3/2 because both of the values are int, the result will be 1. Only after calculation the result is assigned to the left side. So double will be 1.0 . Not the result we need!  

double d = 3.0/2; --> This Works! double/int is double. D is 1.5.  

## AUTOMATIC TYPE PROMOTION  

double a = 10;  

int b = 5;  

var c = a * b;  

**What is the type of c ?**  
What java does is it assumes the result is double. It finds the max capacity type. Because when there is an operation of different kinds of numbers, java takes the small bit number and converts it to the bigger bit number. So here b will be converted to double and the multiplication will be double*double, hence the result, the var is double. **This is automatic type promotion**  

## ARRAYS  

int slNos[]; --> Declare slNos as an int array.  
Does not allocate memory to it. This is different from declaring an int.  

slNos = new int[5];  
This is where you create the array. When you do this java runtime allocates the memory and assign the array to slNos. Size is important too.  

**Array Examples**  

int slNos[] = new int[10]; --> Declaration and Assignment  

double slNos[]; --> Just Declaring

double slNos[] = new int[10]; --> **This will not work!** There is no automatic type casting in arrays.  

**ACCESS BY INDEX**  

int slNos[] = new int[10];  

slNos[0] = 2;  
slNos[3] = 1000;  

int val = slNos[0]; --> Retrieve value  

**ARRAY BOUNDS**  

int slNos[] = new int[10];  

slNos[11] = 2; --> **Will not Work!**  
int val = slNos[20]; --> **Will not Work!**    

**ARRAY INITIALIZER**  

int slNos[] = {1,2,3,4,5,6};  

It is gonna inform the runtime about how many spaces needed for the array by looking at how many elements there are. It is a shorthand for creating arrays when you know the elements of the array.  

**MULTIDIMENSIONAL ARRAYS**  
Array of Arrays  

int matrix[][] = new int[3][5];  
First dimension has 3 elements, second dimension has 5 elements.  

int matrix[][] = new int[3][];  
You can skip the secon dimenson but **you can not skip both of them**  

int matrix[0] = new int[5];  
int matrix[1] = new int[6];  
int matrix[2] = new int[7];  
Here, second dimension is not consistent! This is a jagged array.  

**Multidimensional Array Initializer**  
int matrix[][] = {  
{21,22,23,24},  
{21,22,23,24},  
{21,22,23,24}  
};  

## OPERATORS  

Additive + -  
Multiplicative * / %  

**ASSIGNMENT OPERATORS**  
=  
+= -= *= /= %= &= ^= |= <<= >>= >>>=  
int a += 5 --> int a = a + 5;  

**POSTFIX AND PREFIX OPERATORS**  

Postfix --> expr++ expr--  
Prefix --> ++epr --expr  
This difference only applies when you take the value and assign it to something.  

foo = count++; --> ASSIGN First, then INCREMENT!    
foo = ++count; --> INCREMENT First, then ASSIGN!  

count++ --> count = count + 1;  

boolean isCentury = value == 100; --> If value is 100, returns true  

boolean isClearance = discount != 0; --> If discount is not 0, returns true  

**RELATIONAL OPERATORS**  

< > <= >=  

boolean isPastCentury = value>=100; --> If value is equal or bigger than 100, returns true  

boolean isSubZero = value < 0; --> If value is smaller than 0, returns true  

**LOGICAL OPERATORS**  

&& ||  

boolean shouldTakeUmbrella = isGoingOut && isRaining; --> If both is true, return true  

boolean a = b || c; --> If a or b is true, return true ; If they are both false, return false  

**TERNARY OPERATORS**  

? :  

boolean bagContents = isRaining ? umbrella:hat ; --> If isRaining is true, return hat; If isRaining is false, return hat  

**OPERATOR PRECEDENCE**  
![image](https://user-images.githubusercontent.com/67637654/199279236-5da8ba87-50c2-4b18-af3a-e37bd5ef945f.png)  

**CURLY BRACES FORMS A BLOCK**  

## VARIABLE SCOPING  

int count = 5;  
Count has a "life".  
A beginning --> When it is declared  
An end --> When scope ends  

{ --> Scope of count starts here    
int count = 10;  
count = count + 1;  
} --> Scope of count ends here!  

{  
count++;  --> **Can not reach!** Count is out of scope
}  

This is called variable scoping.  
This is why this kind of variables are called **Local Variables!**  
**"Local" to scope. Scope of those variables end when that block ends**














