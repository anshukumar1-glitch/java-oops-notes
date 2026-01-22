# Functional Interface
Interface having exactly single abstract method but can have any number of defaults and static methods.We can invoke lambda expression by using functional interface.
Before 1.8 in functional interface only public abstract method is allowed.

Advantage of @FunctionalInterface:-
   - It restrict the interface to be a Functional Interface.
   - So if people have already used some lambda expression and some new team member added another abstract method in that interface then all lambda expression will have errors.

## Inheritance in Functional Interface
 ```java
    @FunctionalInterface
   public interface Parent {
    public void sayHello();
}
public interface Child extends Parent{
  **but if we put a abstract method inside this then it will create problem     when we put @FunctionalInterface annonation or it will not be called as     functional interface.
  in this interface we can put n number of default and static methods it will be Functional interface.**
}
```
  - Since Parent is a functional interface so child extend Parent so Child will be functional interface.

## Default Methods Inside Interface
   - Default methods are those methods which have their body.
   Until 1.7 only public abstract methods were allowed whether we declare by writing or not.
   Similarily public static final variable were allowed.
   Since java 8 we can have concrete methods as well inside interface.

  ```java
     public interface Parent {
    default void sayHello("Hello");
}
class Child implements Parent{

}
public class MyClass{
public static void main(String[]args){
Child c=new Child();
c.sayHello();//Hello
}
}
```
   - We can directly use the implementation of the Parent interface default method.
   - But if we want to override it then we can do it also in child class and we can run that.

### Interview Question🔔
  ```java
    interface A {
    default  void sayHello(){
        System.out.println("Hello A");
    }
    }
       
}
 interface B{
    default void sayHello() {
        System.out.println("Hello B");
    }
}
 class MyClass implements A,B{
    public static void main(String[] args) {
        MyClass c=new MyClass();
        c.sayHello();
    }
}
```
So basically in this code it will create a ambiguity problem and complilier or jvm will not able to decide that which interface default method should be called.
Solution is to parameterized the one of the default method in any one interface.
OR OTHERWISE you can call it by implementing the default methods in the main class and call like it 

```java
  @Override
     public void sayHello() {
         A.super.sayHello();
     }
```
- Remember one thing that while overriding the default methods of interface we have to change the access modifier to public from  default.
- Because it is invalid.
 ```java
    @Override
default void sayHello() {
    A.super.sayHello();
}
```
REASON
❌ default methods are allowed ONLY in interfaces, NOT in classes.
MyClass is a class, so it cannot have a default method.

### ❓ Can a class have a default method?
❌ No. Default methods are allowed only in interfaces.

### ❓ Why must a class override conflicting default methods?
To resolve ambiguity when multiple interfaces provide the same default method.

### 🧠Why public Is Mandatory Here
 - Interface methods are implicitly public
  - While overriding:
    1. You cannot reduce access level
     2. So public is required

## Static methods in Interface(Have Body) 
  - Static methods in interface are those methods which are defined in the interface with the keyword static.
  - Static methods containd the complete definition of the function.
  - It cannot be overridden or changed in the implementation class.
```java
   interface A {
    static void sayHello()
    {
        System.out.println("Heelo from A");
    }
}
 class MyClass implements A{
    public static void main(String[] args) {
        MyClass c=new MyClass();
        c.sayHello();❌
        MyClass.sayHello();❌
        A.sayHello();✅
    }
 }
```
- We can not call the static methods of interface with the help of implementation class object.
- we can also not call the static method of interface with the help of implementation class name like MyClass.sayHello(); wrong
- We can call it by the interface name.like A.sayHello()-CORRECT
- We can call default method of interface with the help of implementation class object..

-Like WE CAN NOT OVERRIDE THE STATIC METHODS OF INTERFACE IN THE IMPLEMENTATION CLASS
  ```java
   interface A {
    static void sayHello()
    {
        System.out.println("Heelo from A");
    }
}
class MyClass implements A{
static void sayHello(){
  System.out.println("Heelo from Implementation");
}
    public static void main(String[] args) {
        MyClass c=new MyClass();
        
    }
 }
```
 - Jo class interface ko implement krti h yani ki implementation class usko static method dikhta hi nhi h toh wo override kaise kr sakta hai.
 - Since i have created a method in implementation class so i will not say that it is overridden method because java treats it as simple static method of the class.

### Something which is Innovative
   - Like we have a simple class and in that class we have a main method and in that we can directly print anything.
  ```java
  public class MyClass{
    public static void main(String[] args) {
        System.out.println("Hello");
    }
 }
O/p-Hello
```
- But can we put this main method inside the interface. 
   Ans is Yes From java 8 onwards we can put it there is no problem.
  ```java
   public interface MyInterface{
    public static void main(String[] args) {
        System.out.println("Hello");
    }✅
  ```
 }
