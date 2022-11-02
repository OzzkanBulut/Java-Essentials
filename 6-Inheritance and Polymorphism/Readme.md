# INHERITANCE AND POLYMORPHISM

Hiearchy of Templates f.e

                              Animal Class
    Wild Animal Class			         Pet Class
					                 Dog Class
					                 Cat Class
					                 Rabbit Class
This kind of thing is possible in java because of inheritance.

## INHERITANCE
Allows generic classes to define traits common to a set of related classes.

    class A {		  class B extends A {
    
    }             }			    
     

B has the members defined in A, but A does not have defined in B.
A is the super class, B is the subclass.

class C extends B {
}

class B super class of the C, subclass of the A.
C also is subclass of A.

Can only extend one class!



ACCESS MODIFIERS WITH INHERITANCE

    class A {			        class B extends A {
	    public int m;		        public int q;
	   private int n;		    }
	   protected int o;
	   int p;
    }
 
B myObj = new B();  
B can access m and o, cannot access n because it is private and can access p if
they are in the same package.A can not access q .

----------------------------------------------------------------------------------
    class A{			      class B extends A {
    public String m;		    public int m;
    }				   
				                    public void printValue(){
					                  this.m = 10;
					                  System.out.println(m);
					                  }

				                  public void printSuperClassValue(){
					                super.m = "Hello";
					                System.out.println(super.m);
				   	              }
				               }					
				    
this.m refers to the int value that is in the subclass.
super.m refers to the copy of string value from superclass that is in the subclass.

**INTERVIEW QUESTION**
**What does super refer to ?**
It refers to the super class. The parent class  

## METHOD OVERRIDING  

We can overwrite a method by declaring a method with the same name in the subclass:

    class A {                                   class B extends A {
        public String findName(){                    public String findName(){
                                                      
        }                                             }
    }                                           }  
Method must be exactly the same. If you make the return type int in the subclass, it will not work!  
Also, you can not change the access method! You can not make it private. You can take a public method and make it protected, but you can not take a public method and make it prive.  

**The Override Annoation**   

Whoever is reading the code will understand that you are overriding a method.
    class B extends A {
      
           @Override
           public int findName() {
           
           }
    }  

**INHERITANCE EXAMPLE**  

    public class Animal {                   public class Fish extends Animal {
      public int age;
      public String species;
                                              @Override
      public void move() {                    public void move(){
                                                // When you type Fish.move it will prind fish swimming
        System.out.println("Animal moving);     System.out.println("Fish Swimming"); 
      }                                       }
    }                                       }  
    

    public class Bird extends Animal {
      
       public void move() {
        System.out.println("Bird flying"); // When you type bird.move it will print bird flying
       }
    }

**ENCAPSULATION REVISITED**  

    public class Car {                  public class SportsCar extends Car {
        private int seats;                  public void run(){
                                                //Seats can access here
        public void run(){
          // Seats Can access here
        }
    }
As long as its inheriting from the parent, the access rules of the parent applies.  
However, if you override the method run, you can no longer access seats.  

**This is why you have getter and setter in java. TO ACCESS PRIVATE STATEMENTS**  

    public class Car {                    public class SportsCar extends Car {
        private int seats;
                                              @Override
        public int getSeats(){                public void run(){
            return seats;                         // Can not access seats here
        }                                         // But can access getters and setters
        
        public void setSeats(int seats){      }
            this.seats= seats;
        }
        
        public void run(){
          // Can access seats here
        }

## CONSTRUCTORS WITH INHERITANCE  

    class A {
    
        public A(){
            System.out.println("A's constructor is called);
        }
    }
     
     class B extends A {
          
          public B extends A {
              
                public B() {
                    System.out.println("B's constructor is called");
                }
          }
 **Which constuctor is called ?**  
 When a new instance of B is created, **Both** of these constructors are called.  
 A's constructor is called first, then B's constructor is called.  
 
 **SUPER'S NO-ARG CONSTRUCTOR IS AUTOMATICALLY CALLED**  
 
 ![image](https://user-images.githubusercontent.com/67637654/199469346-fc1f9667-0fa8-4325-9379-2a136e604cb0.png)  
A's constructor is called first, then B's constructor is called, and C's constructor is called.  
  
**Arg Constructor with no-arg super**  

    class A{ 
        public A(){  
            System.out.println("A's constructor is called");
        }
    }
    
    class B extends A {
        public B (int i) {
            System.out.println("B's constructor is called "+ i);
        }
    }
When this happens, then a no-arg constructor thats inherited from A is called first.  
Then B's constructor with the argument i is called.  

**Calling Constructors with Args**  

    class A {
        public A(int i) {
            System.out.println("A's constructor is called" + i);
        }
    }
    
    class B extends A {
        public B(int i) {
            System.out.println("B's constructor is called "+i);
        }
    }
When both the subclass and superclass have arguments in their constructor, only the subclass' constructor will be called.  
Because only superclass constructors with no arguments called automatically. Since this superclass has arguments in it's constructor,
it will not be called automatically. To call the superconstructor manually, you can do this :

    class B extends A{
        public B(int i){
            super(i); --> Called the super class constructor with argument i
            System.out.println("B's constructor is called");
        }
    }
**INTERVIEW QUESTION**
**When do you use super in java?**  

**2 uses of super :**   
- When you referreing to a member of super that you have inherited but hidden, you use super. to get to that.
- For calling the super's constructor when super's constructor requires arguments.If it is a no-args constructor, it will automatically be called.
  But if not, we have to use super to call the constructor with argument



  ------------------------------------------------------------------------------------
 
## Abstract Classes  

**Defining a suber class without intending to create instances**  
**You can not create instances**  

    abstract class Animal {
      
        // Implementation common to all animals 
    }
Animal a = new Animal() --> **You can not do that in abstract classes!**  

**Abstract classes can not be instantiated, but can be inherited**  

    abstract class Animal {
    
        // Implementation generic to all animals 
    }
    
    abstract class Pet extends Animal {
    
        // Implementation common to all pets
    }
    
    class Rabbit extends Pet {
        // Inherits what's in Animal and Pet
    }
**You can not instantiate Animal and Pet, but you can create a Rabbit object since it is not abstract**  


## Abstract Methods

    abstract class Animal {
        
        // Define the "contract" of the method
        abstract public void move();
    }
    
    abstract class Pet extends Animal {
        // Can choose to implement move()
    }
    
    class Rabbit extends Pet {
    
        // Must implement move!
        public void move(){
        
        }
    }  
If a method is abstract, you dont have to write a body for it.  
Because of Pet and Animal classes are abstract, they will not be instantiated.  
And because we can not create objects of those classes, we do not need to implement abstract methods in them.  
But, if a non-abstract class like Rabbit extends an abstract class, the abstract methods must be implemented.  
Because Rabbit can be instantiated and we need those abstract methods for that to happen.  

**Abstract Keyword**  
- Can be applied to classes that you don't want instantiated.  
- Can be a hierarchy of abstract classes.(An abstract class can extend to another abstract class)
- Abstract methods indicate the method signature without implementation.
- Anything that is abstract cannot be instantiated!
- A non-abstract class extending an abstract class must implement all abstract members
- Method overriding rules apply --> method signature, no weaker privilege (same rules with method overriding)


**FINAL KEYWORD WITH INHERITANCE**  

**You can use final in the classes that you don't want to be extended or inherited.**  

    final class A { --> This class is final, you can not inherit from A
    
    }
    
    class B extends A {  --> Will throw an error!
    
    }

**You can also use final in methods that you don't want to be overriden**  

    class Rabbit extends Pet {
    
        final public void move() { --> This method is final, it can not be changed! This is the final version
        
        }
    }
    
    class WildRabbit extends Rabbit {
        
        public void move(){ --> move() can not override move() in Rabbit; overriden method is final!
        
        }
    }

## INTERFACES  

**Define a class' interface seperate from implementation**  

    public interface Car {
        
        public void drive();
        public void refuel(Fuel f);
    }
    
    class SportCar implements Car {
        
        @Override
        public void drive(){
        
        }
        
        @Override
        public void refuel(Fuel f){
        
        }
Anything that implements this interface will have these 2 methods.  
**You can implement more than 1 interfaces to a class!**  

    public interface Drivable {
        public void drive();
    }
    
    public interface FuelVehicle {
        public void refuel(Fuel f);
    }
    
    class SportCar implements Drivable,FuelVehicle {
        
        @Override
        public void drive(){
        
        }
        
        @Override
        public void refuel(Fuel f){
        
        }  
Class has to implement all the methods of all interfaces.  
**Interfaces can extend eachother**
**You can extend one interface two another, and then you can only implement the super interface to your class**  

    public interface FuelVehicle extends Drivable {
        public void refuel(Fuel f);
    }
    
    class SportCar implements FuelVehicle { --> We only implemented FuelVehicle interface
    
        @Override
        public void drive() {
        
        }
        
        @Override
        public void refuel(Fuel f) {
        
        }
    }

**INTERFACES TO IMPORT CONSTANTS**

    interface MyConstants {
        int GLOBAL_VALUE = 42;
    }
    
    class MyClass implements MyConstants {
        int i = GLOBAL_VALUE; --> Will be 42
    }
One uses of interface is to have your constant variables stored. Any class that implements that interface can access those constant variables.    

## INTERFACES VS ABSTRACT CLASSES  

An interface is used when you want to defina a contract of your class. Somebody external to your class would like to know.  
Kinda like a user manual. What the user needs to use that gadget for.  

An abstract class is basically a template or starting point for a bunch of classes. When you want to create a lot of classes and they all have common things  
you can create an abstract class and have those classes inherit from that abstract class.  

In both of them, you can not create instances of their own. 
**You can not create an interface and abstract instance!**  

**DEFAULT METHODS**  

    interface Drivable {                         class SportCar implements FuelVehicle {
                    
        public default void drive() {                 @Override  
            System.out.println("Driving");            public void refuel(Fuel f){
        }                                             
    }                                                 }   
                                                 }
    interace FuelVehicle extends Drivable {
    
        public void refuel(Fuel f);
      
    }

**SportCar has to implement refuel method, but does not have to implement drive method.  
Because drive method is default, which is like an inheritance.It gets the default implementation of that method automatically**  

    interface Drivable {
      
        public default void drive(){
            System.out.println("Driving");
        }                                                           class SportCar implements Drivable,FuelVehicle{
    }                                                   
    
    interface FuelVehicle{                                          }
    
        public default void drive(){
            System.out.println("Driving with fuel");
        }
    }
**If you were to implement 2 interfaces with same default methods and type SportCar.drive, which of the drive method will work ?  
If there are no extra implementations in the SportCar class, there is no way that compiler will know what drive method you are referring to.  
Good thing is, java will not let you do this. It will give you this error:  
"SportCar" inherits unrelated defaults for drive() from types Drivable and FuelVehicle**  

**INTERFACES RECAP**  
- Used to define the "interface" of a class
- A class can implement multiple interface
- Interfaces can extend other interfaces
- Interfaces can contain default methods
- Class implementation overrides default methods
- When there are conflicts, class has to have implementation
- Interfaces can define "constants" that are available in implementing classes
- Interface can define static methods just like classes
- Interfaces can have private methods. These are called by other methods in the interface. (Use case: common to default methods)  


## POLYMORPHISM
Many forms  
Ability of java objects to be able to change forms.  

**SuperClass reference = subClassInstance;**  
**Animal lion = new Lion()**
**While doing like this, you can only use animal related methods.You can not use lion specific methods! Because animal does not have those methods.**  
Superclass can be immediate parent or further up!  

![image](https://user-images.githubusercontent.com/67637654/199512459-4eb6600e-28fc-40cb-9927-093e5129740d.png)  
**You can't acces the methodName() method because it is a lion specific method. Because we created the lion as an Animal object, it cant acccess!**  

![image](https://user-images.githubusercontent.com/67637654/199512738-fedc62a0-98b1-480d-a0f3-1d69c6db49a5.png)  
**THIS WORKS!**  

![image](https://user-images.githubusercontent.com/67637654/199512874-53cac98f-9620-4b7b-aaa8-9314c13a55cd.png)  
**Method in lion will work!**

**POLYMORPHISM WITH INTERFACES**  

    public interface Drivable {
        public void drive();
    }
                                              Drivable car = new SportCar();
    public interface FuelVehicle {            car.drive();
        public void refuel (Fuel f);
    }


**CASTING WITH OBJECT REFERENCES**  

    Drivable car = new SportCar();
    car.drive();
    
    FuelVehicle vehicle = (FuelVehicle)car;
    vehicle.refuel(new Fuel());
This is the same with casting primitive parameters. You are telling compiler to do the conversion by force.  
You ask for compiler's trust and say that I know what I'm doing.  


**IS-A RELATIONSHIP**  

**Idea of is-a relationship is : Subclass is-a Superclass**  
Is fish an animal ? Is dog a Pet ?  
This informs what can be assigned to something  
Drivable car = new SportCar(); --> Is sportCar drivable? yes  


**THE OBJECT CLASS**  

![image](https://user-images.githubusercontent.com/67637654/199516270-6f9edcec-6226-42f6-b414-371a6e8dcc61.png)  
When you type super() in c, you refer to class B.And when you type super() in class B, you refer to class A.  
What will happen if you type super() in A ? --> You refer to the Object Class.  
![image](https://user-images.githubusercontent.com/67637654/199516842-1e4d2b39-ad3e-4d03-ae81-e5620b33c666.png)  
**All classes in java extends to the Object Class. In the object class, there are important methods that every class should have.  
Like equals(),toString().**  


**toString Method**  

    public class Car {              Car car = new Car();
                                    System.out.println(car);
    }

When you try to print a class, it will print the string value of the object. Which is something like this :  
car@437589. In order to return a meaningful string, you can override the toString method in class Car.  
  
    public class Car {
      
      @Override                                           Car car = new Car();
      public String toString(){                           System.out.println(car); // Prints "this is a car"
          return ("This is a car");                       
      }
  }
 
  
**Equals Method**  

![image](https://user-images.githubusercontent.com/67637654/199521910-071365ad-139e-4308-951b-3278d3d059bd.png)  

Let's say these two instances have the exactly same values.  
myNewCar == neighborCar will tell you it's false.  
Because even though all their values are same, they are still different instances.  
In order to check if all the values in the instances are same, we override equals method.  

    public class Car {
        private int seats;
        private String make;
        
        @Override
        public boolean equals(object O){
            // Check to see if the parameter o has the same values
        }
    }
    









        


   
  


     


        
        
        
        
        
        
        
        
        
