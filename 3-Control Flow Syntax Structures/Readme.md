# FLOW STATEMENTS / CONTROL STATEMENTS  

```
if(a>b) b = 0;  

if(a>b){  
System.out.println("a is greater");  
b = 0;  
}    
else if (a < b) {  
System.out.println("a is lesser");  
} else {  
System.out.println("a and be are equal");  
} 
```
This is referred to as if-else ladder.  

**Nested If**  

```
if(a>b) {
	System.out.println("a is greater");
	if(isTooBig(a)) System.out.println("a is too big");
} else if(a<b) {
	System.out.println("a is lesser");
} else {
	System.out.println(" a and b are equal");
} 
```

**DO NOT MAKE LADDERS OF IF ELSES!**  

**USE SWITCH CASE**  
```
switch(a) {
	
	case 0:
	   System.out.println("a is 0");
	   break;
	case 1:
	   System.out.println("a is 1");
	   break;
	case 2:
	   System.out.println("a is 2");
	   break;
	default:
	   System.out.println("a is >=3");
}  
```
The reason why a break is needed in switch case is because of the  

**Switch Fall-Through Pattern:**  
```
switch(a) {
	case 0:  
	case 2:  
	case 4:  
	case 6:  
	case 8:  
	case 10:  
	    System.out.println(" a is an even number less than 10");  
	    break;  
	case 1:  
	case 3:  
	case 5:  
	case 7:  
	case 9:  
	    System.out.println("a is an odd number less than 10");  
	    break;  
	default:  
	    System.out.println(" a is greater than 10");  
}  
```

**SWITCH VALUE**  

switch(value){  

}  

**What are the types that are allowed in here ?**    
**What are the best types that switch statement supports ?**  

They can be among this primitives:  
- byte
- short
- char
- int
- STRING
- Enum  


**JAVA 14 FEATURE**  

**Switch Expression**    
```
int numletters = switch(day) {--> day is an enum value   

case MONDAY, FRIDAY, SUNDAY -> 6;  
case TUESDAY -> 7;--> If day is tuesday, return 7  
case THURSDAY, SATURDAY -> 8; --> **THERE IS NO BREAKS!**    
case WEDNESDAY -> 9; --> If day is wednesday, return 9    

};  
```

**SWITCH EXPRESSION** 
- No breaks required --> No fall through  
- Switch Expression --> Returns value  
- Possible to declare same variable in multiple 'blocks'  

## ITERATION STATEMENTS  

**"Classic" For Loop**  
```
for(int i = 0; i<10;i++)(initialization;condition;action per iteration) {  
    System.out.println(i);  
} This curly bracket ends the scope! No more int i from this.  
```
**COMMAS IN FOR LOOP**  
```
int i,j;  

for(i=0, j=10; 1<10; i++, j--) {  
   System.out.println(i+j);  
}  
```
**For-each Loop**  
```
for (type iterationVariable : collection) { // collectioans are like arrays,lists or sets. Works for all types of collections    
    block-statement  
}  
You only read the value from the collection.There are no changes made in the collection  

int someNumbers[] = {25,42,36,75,93};  
int total = 0;  

for(int element: someNumbers) {  
total = total + element;  
}  

We can also use var  
for(var element : someNumbers)  
Compiler looks the someNumbers collection type and assumes the type.  
```
**NESTED LOOPS**  
```
int matrix[][] = new int[10][20];  

for (int i=0; i<10; i++) {  
for(int j=0; j<20; j++) {  
matri[i][j] = i * j;  
}  
}  
```
**NESTED LOOPS WITH FOR-EACH**  
```
for( int[] subArray : matrix){   
  for(int element: subArray){  
    System.out.println("Element is " + element);  
  }  
}  
```
Not a lot of people use this, but it can be used.  

**When the index is needed use CLASSIC FOR**  
**When you want just the element use FOR-EACH**  
**For-each is really handy with Collections API's**  

**WHILE LOOP**  
while (condition) {  
  
}  

**DO-WHILE LOOP**   
  
do{  
  
} while(condition)  


**DIFFERENCE BETWEEN WHILE AND DO-WHILE**  

In the while loop, you have the statement executed only if this condition evaluates to true. If the condition is false, the statement is skipped.  
On the other hand, in the do-while loop, it executes the statement at first no matter what the condition is. Only after the first execution it checks the condition.  
Only difference between the while loop and do-while loop, is if that condition was false at the beginning. While will not execute, but do-while will execute for once.  
**BREAK and CONTINUE (ALTERING THE FLAW OF THE LOOP)**  

Break --> Ends the loop  
Continue --> Skip to the next iteration  

**BREAK**  
```
for (int i = 0 ; i<10;i++) {  
	if(i %% 5) break;  
	System.out.println(i); // Prints till 4  
}  
```
**CONTINUE**  
```
for (int i = 0 ; i<10;i++) {  
	if(i %% 5) continue;  
	System.out.println(i); // Prints 0 to 9 but skips 5  
}  
```
**REVISITING SCOPING**  

**Example**  
```
if (i > 5) { // Scope of foo starts here  
	int foo = 20 ;  
	// Statements  
} // Scope of foo ends here  

if (i > 5){ // Scope of foo starts here  
	int foo = 20; // We declared foo here, so scope of foo will end in this if  
} else { // Scope of foo ends here  
	foo = 30; // Foo is not declared here, so compiler wont recognize it  
}  
```
**NESTED LOOPS EXAMPLE**  
```
int matrix[][] = new int[10][20];  

for(int i = 0 ; i< 10 ; i++) { // Scope of i starts here  
	for(int j = 0 ; j< 20 ; j++) { // Scope of j starts here  
	martix[i][j] = i*j; // Both are in the scope, so you can do this.  
	} // Scope of j ends here  
} // Scope of i ends here  
```














