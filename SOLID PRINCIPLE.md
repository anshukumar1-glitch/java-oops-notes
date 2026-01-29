# SOLID PRINCIPLES
  SOLID is a set of 5 object-oriented design principles introduced by Robert C. Martin.
### Purpose of SOLID:-
- Make code easy to maintain
- Reduce tight coupling
- Make systems flexible, testable, and extensible
- Prevent breaking existing code when requirements change
As applications grow, bad design increases complexity. SOLID helps control that complexity.

### SOLID stands for:
S – Single Responsibility Principle (SRP)
O – Open/Closed Principle (OCP)
L – Liskov Substitution Principle (LSP)
I – Interface Segregation Principle (ISP)
D – Dependency Inversion Principle (DIP)

### 1.Single Responsibility Principle
   It says that class should have only one reason to change.
   It means that one class have only one responsibility and a class should do one job only.
   Its few benefits are :-
       1. Testing -A class with one responsibility will have far fewer test cases.
       2. Lower Coupling- Less functionality in a single class will have fewer dependencies.
       3. Organization – Smaller, well-organized classes are easier to search than monolithic ones.and have better readability.
   Without SRP:-
      Classes become god classess.
      Small change breaks many things.
      Hard to test and debug.
Example:- A Book class that:
Stores book data ❌
Manipulates text ❌
Prints text ❌
Printing is not the responsibility of a Book.

But th correct logic is :-
  Book class → holds data & book-related logic.
BookPrinter class → handles printing/output

- Key Idea: If a class is doing more than one thing, split it.

### 2.OPEN/CLOSED PRINCIPLE(OCP)
  - It says Classes should be open for extension but closed for modification. In doing so, we stop ourselves from modifying existing code and causing potential new bugs.
  - It says add new behaviour without changing the existing code.

- It can be Achieved by :-
     Inheritance
     Interfaces
     Abstract classes
      Polymorphism

Example:- Like we have a class called Guitar.
```java
  public class Guitar {

    private String make;
    private String model;
    private int volume;
    private String flameColor; // added later ❌

}
```
 - At this point, it might be tempting to just open up the Guitar class and add a flame pattern — but who knows what errors that might throw up in our application.
 - So we can not modify the existing class code rather than we can just make another class extends Guitar and can add a ` flameColor `.
```java
  public class Guitar {

    private String make;
    private String model;
    private int volume;

    public Guitar(String make, String model, int volume) {
        this.make = make;
        this.model = model;
        this.volume = volume;
    }
}
public class SuperCoolGuitarWithFlames extends Guitar {

    private String flameColor;

    public SuperCoolGuitarWithFlames(
            String make,
            String model,
            int volume,
            String flameColor) {
        super(make, model, volume);
        this.flameColor = flameColor;
    }
}
```
Why this is good:-
Original class untouched
New feature added safely
✅ OCP satisfied

### 3.Liskov Substitution    
  Subclass must be usable wherever parent class is expected.
  Child should not break parent behavior.
  ❌Wrong Code (LSP Violation):-
  ```java
        public interface Car {
    void turnOnEngine();
    void accelerate();
}
public class MotorCar implements Car {

    private Engine engine;

    public MotorCar(Engine engine) {
        this.engine = engine;
    }

    public void turnOnEngine() {
        engine.on();
    }

    public void accelerate() {
        engine.powerOn(1000);
    }
}
public class ElectricCar implements Car {

    public void turnOnEngine() {
        throw new AssertionError("I don't have an engine!");
    }

    public void accelerate() {
        System.out.println("Accelerating fast!");
    }
}
```
❓ Why this breaks LSP
  Car promises turnOnEngine()
  ElectricCar breaks the promise
  Client code crashes
So we can write the correct code by Splitting behaviour properly.
  like 
  ```java
    public interface Vehicle {
    void accelerate();
}
public interface EnginePoweredVehicle {
    void turnOnEngine();
}
public class MotorCar implements Vehicle, EnginePoweredVehicle {

    private Engine engine;

    public MotorCar(Engine engine) {
        this.engine = engine;
    }

    public void turnOnEngine() {
        engine.on();
    }

    public void accelerate() {
        engine.powerOn(1000);
    }
}
public class ElectricCar implements Vehicle {

    public void accelerate() {
        System.out.println("Silent but fast!");
    }
}
```
-- Why this is good
No broken expectations
Substitution works perfectly
✅ LSP satisfied

### 4.Interface Segregation
 - Do not force classes to implement unused methods
 - It simply means that larger interfaces should be split into smaller ones. By doing so, we can ensure that implementing classes only need to be concerned about the methods that are of interest to them.
Example :-
```java
  public interface BearKeeper {
    void washTheBear();
    void feedTheBear();
    void petTheBear();
}
//❓ Problem -Everyone forced to pet bear
```
 We can split this big interfaces into smaller interfaces.
   like-
```java
 public interface BearCleaner {
    void washTheBear();
}
public interface BearFeeder {
    void feedTheBear();
}
public interface BearPetter {
    void petTheBear();
}
public class BearCarer implements BearCleaner, BearFeeder {

    public void washTheBear() {
        System.out.println("Washing bear");
    }

    public void feedTheBear() {
        System.out.println("Feeding bear");
    }
}
but who want to pet a bear then he can
public class CrazyPerson implements BearPetter {

    public void petTheBear() {
        System.out.println("Petting bear 😬");
    }
}
```
Here in this code we can clearly state that a person can love to feed a bear or wash a bear but he dont love to pet a bear so in upper we are keeping all methods in one interface so it will create a issue that person implement that interface will have to pet a bear. Which violates the priciple of ISP (forcing the person to peat a bean by overiding the unused methods).

✔ Why this is good:-
Classes implement only what they need
No dummy methods
“ISP promotes smaller, focused interfaces to reduce unnecessary dependencies.”
✅ ISP satisfied

### 5.DEPENDENCY INVERSION PRINCIPLE(DIP)
   It says that Depend on abstractions, not concrete classes
📌 Use interfaces + dependency injection.
👉High-level class ko low-level class pe directly depend nahi karna chahiye
👉 Dono ko interface (abstraction) pe depend karna chahiye
  
- 🧠Real Life Example
 Phone Charger Example
 Socho tumhara mobile phone hai.
 ❌ Agar phone bole:
 “Main sirf Samsung charger se hi charge hunga”
 Toh problem:
 Charger badla → phone useless
 Flexibility nahi
 ✅ Sahi approach:
 “Mujhe bas USB-C standard chahiye”
 Ab:
 Samsung charger chalega
 OnePlus charger chalega
 Power bank bhi chalega
 👉 USB-C = Interface (abstraction)

```java
 Code Example (Conceptually)
❌ DIP Violation
class Computer {
    private Keyboard keyboard = new StandardKeyboard();
}


Problem:
Computer tightly tied hai StandardKeyboard se
Keyboard change nahi kar sakte
Testing mushkil

✅ DIP Followed
interface Keyboard { }

class StandardKeyboard implements Keyboard { }

class Computer {
    private Keyboard keyboard;

    Computer(Keyboard keyboard) {
        this.keyboard = keyboard;
    }
}


Ab:
Keyboard change ho sakta hai
Testing easy
Code flexible

Dependency Inversion Ka Main Point ⭐
Yaad rakhne ka Formula
Concrete class pe depend ❌
Interface pe depend ✅

Kyun Zaroori Hai DIP?
✔ Loose coupling
✔ Easy testing (mock objects)
✔ Code flexible
✔ Future changes easy

Ek Line Mein (Interview Ready)

Dependency Inversion ka matlab hai ki classes ek-dusre ke implementation pe nahi, balki abstraction (interface) pe depend karein.

Short Hinglish Summary 📝

Direct new keyword se dependency banana ❌
Interface use karke dependency dena ✅
High-level class = boss
Low-level class = worker
Interface = contract
```


Real Youtube Wala Padhai.
->Problem before Solid Principles:
   - Maintainability
   - Readability
   - We intdroduces so many bugs.
This is invented by Robert C.Martin

   
