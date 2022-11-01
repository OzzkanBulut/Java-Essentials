# Object Oriented Programming

## A Java Class  

**Class**

Models "things" in the real or business world.  

Java Class Provides State and Behavior  

**Example Classes (Entities)**  

* Employee
* Account
* Car
* Message


**Class vs Object**

Class --> New Data Type
Object --> Value of that type

Class is a template for object
Object is the instance of that class

OBJECTS
Referred to as instances or class instances


CLASS SYNTAX

class ClassName{

Member variables --> State
Methods--> Behavior --> Behavior
}


class ClassName {
	type memberVariable;
	type memberVariable; // Also called instance variables

	type methodName(parameters){
		// method body
	}

	type methodName(parameters) {
		// method body
	}
}


EXAMPLE CLASS DEFINITION
	
class Car { // Pascal Case
	int seats;
	int wheels;
	double weight;
	double topSpeed; // Camel Case
}

When we created class Car, we actually created a data type.

Car myNewCar; // This is a new variable of type Car.

myNewCar = new Car(); // We created a new instance of a class

Therewill be a new instance of this class, which means its goınna get a copy of 
the variables in that class.

neighborCar = new Car() ; // Gets ANOTHER copy of these variables.
 
neighborCar and myNewCar are two instances.

myNewCar.seats = 4 ;
neighborCar.seats = 2 ;
System.out.println(myNewCar.seats); // Prints 4
System.out.println(neighborCar.seats) // Prints 2 

HOW DOES THIS WORK ? 

It works by Usıng Object References

When you create a new variable of a class type, java runtime is gonna allocatate that
variable.
Car myNewCar; // This does not allocate ! Only declares // This is the object reference, points to the instance address. Creating a reference variable here
myNewCar = new Car(); // This is creating a new instance and allocates memory.THIS IS THE INSTANCE

Car neighbor; // it creates another variable but allocates a memory yet.
neighborCar = new Car(); // Another instance of Car created. ** new ALLOCATES MEMORY SPACE**

References can be assigned to other references

myNewCar = neighborCar; // Kinda like in the strings, those 2 references refer to the same object

neighborCar = null ; // This reference is erased. Does not point to anywhere.Does not have an arrow anymore
myNewCar still exists to that same object.
** Get an ss of 603.04.30**

THINGS TO REMEMBER
* Classes are blueprints and Objects are instances
* Classes contain instance variables (or member variables) and methods
* A class definition forms a new type. Objects instances of the class are values of the type.
* You create new instance using the new keyword.
* The new keyword is what allocates memory for the object instance.
* The memory allocation happens at runtime(just  when its needed).
* Object variables are really reference variables. // Pointing
* References can be changed by having them point to other instances.


**VARIABLE SHADOWING** COMMON INTERVIEW QUESTION

class Car {
	int seats;
	int whells;
	double weight;
	double mileage;
	
	boolean canSeat ( int seats) {
		return seats >= seats; // This is instance variable shadowing. This is happens when we have save variable names between the method variable and instance variable.
	}
}
We can solve this problem with : 
The THIS reference
Refers to the instance the metwod will be run on


class Car {
	int seats;
	int whells;
	double weight;
	double mileage;
	
	boolean canSeat ( int seats) {
		return this.seats >= seats;
	}
}


CONSTRUCTORS

class Car {
	int seats;
	int wheels;
	double weight;
	double mileage;
	
	Car(){
		mileage = 0 ; // When instances of  car is created, mileage of those instances will be 0.IT HELPS CONSTRUCT THE OBJECT.
	}

	boolean isTwoSeater(){
		return seats == 2;
	}

	boolean isFourSeater(){
		return seats == 4;
	}
}



JAVA CONSTRUCTORS

- Must be same name as class
- No return type
- Can use access modifiers // public,private,protected
- Can have multiple constructors (Constructor overloading)

How ‎will the runtime know which constructor to use ? 
Like This:

class Car {
	int seats;
	int wheels;
	double weight;
	double mileage;
	
	Car() {					Car c1 = new Car();  // This one uses the empty constructor. Referred as no-arg constructor
		mileage = 0 ;             	Car c2 = new Car(5); // This one uses the construct with an int parameter
	}
	
	Car(int seats) {
		this.seats = numberOfSeats; // use this when shadowing
	}
}

Java has a default constructor for classes that you dont write but it is already there.
When you dont write a constructor yourself, something is happening behind the scenes to make sure that you get a new object and that is object is being constructed somehow.


CALLING A CONSTRUCTOR FROM CONSTRUCTOR

class Car {
	int seats;
	int wheels;
	double weight;
	double mileage;
	
	Car() {
		mileage = 0; 		Car c1 = new Car();
	}				Car c2 = new Car(4);

	Car (int seats) {
		this(); // This calles the no-arg constructor.So when you call this constructor, you actually call both constructors.
		this.seats =seats; // So no matter which constructor you call, mileage of those 2 car c1 and c2 will always be 0.
	}
}


OBJECT INSTANCE VARIABLES

class Car {
	String name; // String is an object
	String make;
	int seats;
	int wheels;
	double weight;
	double topSpeed;
	Tire[] tires; // Tire is a class.This is a tire array that collects tire objects.
}

OBJECT ARGUMENTS

boolean isHeavierThan(Car c) { // This method takes a Car object as an argument !
	return this.weight > c.weight;
}



CONSTRUCTOR OBJECT ARGUMENTS

COPY CONSTRUCTOR PATTERN

class Car{ // Create a car object by copying an another car object
	int seats;
	int wheels;
	double weight;
	double mileage;
	
	Car(Car other){
	this.seats = other.seats;	
	this.wheels = other.wheels;
	this.weight = other.weight;
	this.mileage = other.mileage;
	}
}

** WHAT IS A COPY CONSTRUCTOR ? ** Interview Question
It is used when you want to clone an object or take instances of that object.
Takes the object you want to be copied as a constructor argument.


PASSING OBJECTS AS METHOD ARGUMENTS

Call BY VALUE or CALL BY REFERENCE

In java, it is called by value all the time.

class Car{ 
	int seats;
	int wheels;
	double weight;
	double mileage;
	
	boolean canSeat(int numberOfPeople) { // Takes primitive type, int
		return seats >= numberOfPeople;
		numberOfPeople = 100;
	}

	boolean isHeavierThan(Car c) { // Takes object type,car
		return this.weight > c.weight;
	}
}



Car car = new Car();
int capacity = 3 ;
car.canSeat(capacity); 

when we change the value of numberOfPeople to 100, the capacity variable will
not change.Because in java, we call the methods by value, not by reference.
so when we type car.canSeat(capacity), we are not giving the canSeat method
the reference of capacity, we are only giving the value of capacity which is 3.
So, original capacity will not be affected.This is why Java is a CALL BY METHOD LANGUAGE.




OBJECT REFERENCES AS ARGUMENTS ( SS 607.5.40)

Car car = new Car();
Car anotherCar = new Car();
car.canSeat(3);
car.isHeaviewThan(anotherCar);


boolean isHeavierThan(Car c) {
	return this.weight > c.weight ;
}

When we pass an object reference to the method, they will be the same references.
In this example, anotherCar and c references are same because they are pointing
to the same object instance that is created in the heap.So when there is a change
in the c reference, anotherCar reference also changes.

If we say c.weight = 100, anotherCar.weight will be 100 too.
When you take an object reference as argument in a method, be careful to not 
to change the reference!

Interview Question ---> Call by value and Call by Reference!


THINGS TO REMEMBER

- Java implements call by value
- Any value passed as parameters is "copied" to the method arguments
- If the argument is an object reference , the reference is copied // Reference is also passed by value!
- The reference copy points to the same instance as the source object reference








  

