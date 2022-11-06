## THE FINAL MODIFIER
```
final int i = 10 ; // i can not change. It will be always 10 in that scope

i = 20 ; // Can not assign a value to final variable 'i'

final int i ; // Works too , but the first assignment you make will be final.

final Car c = new Car();

Car neighborCar = new Car();

c = neighborCar; // Does not work! Gives the same error. The c reference is final!

c.seats = 6 ; // You can do this. You can not change the value of c , but you can change the instance variables of c .This is a different variable.It is not final

In order for c.seats=6 to not work , we have to make instance variable seats final as well.
```

**The Final Modifier**  

- Used to declare a variable as a "constant"
- Affects the variable/reference only
- Object references can be final - but does not affect instance variables
- Collections can be final - but does not affect containing elements
- Benefit --> Runtime optimization
- Benefit --> Programming best practice

final String COMPANY_NAME = "Acme Inc"; // Tells the developer this is important.I dont want my company name changed!.  
It is recommended to write the name like this, all caps and a underscore.


**MAGIC VALUES**  
```
if(numberOfItems > 6){
	//Show Error
}
Magic values are values that have no explanation in the code or the documentary
that why that value is in there. In this example , 6 is the magic value.
You can use final modifier in here to avoid magic values :

final int MAX_ITEMS_IN_CART = 6;

if(numberOfItems > MAX_ITEMS_IN_CART){
	// Show Error
}

```
**LOCAL CLASSES AND VARIABLE SCOPE  INTERVIEW QUESTION**  
```
public static void main(String [] args) {
	int i = 10;
	
	clas Foo {
		int x = i; // This works! java allows you to use all the variables inside this class.  
	}

	i = 20 ; // If you change value i , you cannot use it in the Foo!.Very important!
} 
```
Any variable that is changing inside the scope, cannot be used in a local inner class!!  
Why ?  
When u create a local class, java takes copies of the variables in the main.So java copies the value of i which is 10,
but when you change i to 20 , java can no longer update the copy, so it will be 10.Which causes problems  

When you have local classes, you can reference the variable which is in the scope of that same block that 
the class is in, as long as the variable is not modified!.  

**You can do this !**  
```
public static void main(String[] args){
	final int i = 10; // Hey dont change this, it will be used in a local class!
	
	class Foo {
		int x = i ;  // Has to be final or effectively final
	}
}

```
**Interview Question **
WHAT NEEDS TO HAPPEN FOR AN OUTER VARIABLE TO BE ACCESSED IN A LOCAL CLASS ? 
The variable must be final!.

**DOES JAVA SUPPORT SCOPE CLOSURES?**
Java kind of supports closures, whith the idea that the thing thats containing the closure
happens to be local class,and what its closing over is all the variables that are
in scope in the same block has way that local class is being declared.

**PACKAGES**
```
class Car {
	int seats;
	int wheels;
	double weight;
	double mileage;
}
```
A package can contain multiple classes.You just basically group the related 
classes in the packages.  

package io.javabrains; // packages are in this format  

You can refer to the classes in a package like this :   

io.javabrains.Car // packagename.car  

You can seperate classes with same name if they are in different packages :  

com.google.Car  
com.facebook.Car  --> Classes have the same name but because they are in different packages,
			IDE can seperate them.  

- Used for grouping classes and interfaces
- Can contain sub-packages //Service --> Abstract-Concrete
- Provides namespacing for class names
Namespace(Also called as name scope) : is an abstract container or environment created to hold a logical
grouping of unique identifier or symbols(i.e. names).
- Provides encapsulation - access control for code in classes
- No hierarchy!!! --> VERY IMPORTANT
Each package with the uniqeu name is a unique package but there is no hiearchy in them!  

**DEFAULT PACKAGE**

Classes in the source folder belong to the default package.  
If you dont specify a package in the class, class belongs to the default package.  

Dont do this! --> When you are working in a real application , always specify a 
package name.  

**IMPORTING CLASSES**  

- Import required to use a class from a different package:  
```
package io.javabrains.vehicles;			package io.javabrains;
					
class Car {				class App {
}						public static void main(String[]args){
							Car c = new Car();
						}
					}
```
Since they are in the same package, we can use package io.javabrains;

import io.javabrains.vehicles.*;  
- You can import * for a package. // // * means import everything from that class  


**ACCESS MODIFIERS**  

Encapsulate and restrict access to member variables and methods
This certain things inside of my class , i dont want people to access them.
I dont want somebody outside of this class to access them.

- public --> Accessible to everyone
- private --> Not accessible outside the class
- protected --> Accessible by inheritance (subclasses)

```
class Car {
	private int seats; // seats is accessible only in class Car
	private int wheels;
	private double weight;
	private double mileage;
	
	public boolean isTwoSeater() { // This methods are accessible outside the class
		return seats == 2;
	}

	public boolean isFourSeater() { // This is accessible outside the class too
		return seats == 4;
	}
}
```
If you dont specify any access modifier, it is gonna be a default access modifier.  

**Default Access Modifier**  

- Default is package private
- Acts like public if in the same package // if accessing code is in the same package
- Acts like private to other packages // if accessing code is anothar package
(SS 610exp-5.40)
 
**INTERVIEW QUESTION**  
What are the access modifiers in Java ?   


**RECOMMENDED PRACTICE**  

- All state is private // All data is private
- Methods can be mixed - depends on whether the method is internal-only or 
  meant to be called outside
- Use getters and setters to access internal state
- Package-private is very rarely used // Be careful with that!
- Protected based on inheritance access needs 


**THE STATIC KEYWORD**  

The static keyword is where the java kind of breaks the strict object oriented design rule.  

When you need to define a class member as independent from any object instance.  

Static is also essential for starting the application. In java, everythign is object.  

In order to start the application, you need an object to be created first. So whose
gonna create the object is every object is created by another object ?  

It is kinda like the chicken and egg problem.  

new keyword --> can be called from method --> Should be called on an instance, but who
gets that instance ?  

This is where the main() method comes  

main() method is not associated with an instance. This is what kicks of the app
This is how java solves the chicken egg problem.  

**Object References for Non-Static Members**  
```
class Car {
	int seats;
	int wheels;
	double weight;
	double topSpeed;
}

Car myNewCar;
myNewCar = new Car();

Car neighborCar;
neighborCar = new Car;
```

**Object References for Static Members**  
```
class Car {
	static int seats;
	int wheels;
	double weight;
	double topSpeed;

	static void staticMethodName() {
	
	}

}				Car ---> seats
				
Car myNewCar;			myNewCar ---> wheels,weight,topspeed
myNewCar = new Car();

Car neighborCar;
neighborCar = new Car(); 	neighborCar ---> wheels,weight,topSpeed
```  

Because seats is static, it will be associated with the Car class, not with an instance.  

Static is a global variable for that class.  
Usage of static are with the class name , not with the instance name :  

Car.seats = 5; // All seats in every Car object will be 5  

if you try to get neighborCar.seats, it will be 5 because we globally declared that
it is 5.  

Car.staticMethodName(); // Calling a static method is also from the class, not the instance  

**Static Keyword**  

- Makes a class member associate with the class, not instance
- Can be accessed before any instances are created
- No instance assumptions - example: no this, no non-static access
- All instances of a class share the same static variable
- Used by the method that starts every Java Program.


**NESTED CLASSES**  

You can define a class inside another class

Multiple Types of Nesting

- Static nested class
- Static Inner Class
```
	class Car {
	
		static class Wheel {

		}
	}
				
Car myCar = new Car();
Car.Wheel someCarWheel = new Car.Wheel(); // You instantiated a wheel object
We associated the wheel class with the car class.
```

- Inner Class (Non-static nested class)
```
	class Car {			
	
	class Wheel{// There is no static here!
	
		}
	}

Car myCar = new Car();
Car.Wheel myCarWheel = myCar.new Wheel();
// Not just any wheel! This is associated with the Car instance // 
```

Difference between static inner class and non-static inner class are 
static inner class are associated with the class, but non-static inner classes
are associated with the object(instance) itself.  

- Local Classes
```
	public static void main(String[] args){
	
		class Foo {
		
			int x ;
		}
		Foo f = new Foo();
		f.x = 1 ;
	}
```

It is not commonly used.

- Anonymous Classes

Anonymous Inner Class
```
class Car {
	private int seats;
	private int wheel;
	private double weight;
	private double mileage;				Car c = new Car() { // No semicolon , open a curly bracket to override the blueprint)
							// ....
	public boolean isTwoSeater(){ 
		
		return seats == 2 ; 			public boolean isTwoSeater(){  // This method is overwritten. But only for this instance!
	}					
							return seats >= 2; 	Only the object c will return seats greater or equal than 2, Rest of the car object
	public boolean isFourSeater(){				}		Will always return 2!
							}
		return seats == 4 ; 
	}
```
