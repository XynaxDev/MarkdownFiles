# <p align="center" style="color: #003366; font-family: Cambria; font-size: 36px; margin: 0; padding: 0;"> <strong>Java <span style="color: red; font-size: 20px;"><i>.notes</i></span></strong> </p>


### **JDK**
JDK (Java Development Kit) is a software tool used to provide an environment for developing Java programs.  
It includes:  
- JRE (Java Runtime Environment)
- JVM (Java Virtual Machine)


### **JRE**
JRE (Java Runtime Environment) provides the necessary library files for executing (running) Java programs. 
It includes:  
- JVM  
- Library Files


### **JVM**
JVM (Java Virtual Machine) is responsible for the execution of Java programs by locating and running the `main` function.


## **Classes and Object**

### **Classes:**
Classes are the fundamental building blocks of Java applications. Without defining a class, we cannot create objects or organize our code into a functional program.  

**Example**:
```java
class ClassName {
    // Attributes
    dataType attributeName;

    // Method
    returnType methodName() {
        // Method logic
    }
}
```
<br>

We can also define **packages** and **import libraries** outside of any class.

**Example**:<br>

```java
package mypackage;           // Package declaration
import java.util.ArrayList;  // Importing a library
```

### **Objects:**
In Java, an object is an instance of a class that contains attributes and methods.

**Example**:
```java
ClassName objectName = new ClassName(); // objectName is object

objectName.attributeName; // Access attribute
objectName.methodName();  // Call method
```

## **Tokens**
Tokens are the individual units of a Java program.

**Example**:

1. **Keyword:** Reserved words predefined for the compiler. These have special meanings and cannot be used as variable names or any other identifiers.
   
2. **Data Types:** Data types define the type of data a variable can hold.
   
   **Types:**

   1. **Primitive Data Types:** `int`, `char`, `boolean`, etc.
   2. **Reference Data Types:** Refer to objects and hold references to data.
    
        **Examples:**

        - **Strings:** A sequence of characters (e.g. `String str = "Hello";`).
        - **Arrays:** A collection of similar types (e.g. `int[] numbers = {1, 2, 3};`).
        - **Classes:** User-defined types to create objects.

3. **Identifiers:** User defined terms used to name variables, methods, classes, etc.
   1. Can start with `_` or `$`, but not with numbers.
   2. Keywords and whitespace cannot be included.
   3. Case-sensitive.

4. **Variables:** Variables are containers that hold values.

    Types of Variables:
   1. **Instance Variables:**
      - Declared inside the scope/body of a class.
      - Memory is allocated only after object creation (late memory allocation).
      - Each object gets a separate copy.
      - Default value is `0` if not explicitly initialized.
      - Accessible by all methods in the class.

    2. **Static Variables:**
        - Declared with the `static` keyword.
        - Cannot be declared as local variables.
        - Shared among all instances of the class (class variable).
        - Can be accessed without creating an object (early memory allocation).
        - Accessed using the class name.
  
    3. **Local Variables:**
        - Declared within a method or block.
        - Accessible only within that method or block.
        - Must be explicitly initialized before use.

## **Methods/Functions**
Methods are reusable blocks of code that perform specific tasks. They can be static (called without objects) or instance (require objects).

**Example:**
```java
public int add(int a, int b) {
    return a + b;
}
```
- `public:` An access modifier that defines visibility.
- `int:` A data type representing an integer value.
- `add:` The name of the method.
- `return:` A keyword used to return a value from a method.
- `(int a, int b):` The parameters (inputs) for the method.
  
## **Access Modifiers**
Java provides four types of access modifiers to control the visibility of classes, methods, and variables:
1. **public**
 - Can be used for both classes and methods.
 - **For methods:** Can be accessed by all classes.
 - **For classes:**
      - Only one class can be declared as public in a file.
      - If a class is public, the file name must match the class name.

2. **private**

- `private methods` and `variables` can only be accessed within the same class.

- In Java, the private access modifier can be applied to methods and member variables (fields) within a class.
  1. **Private Methods and Variables:** We can declare methods and member variables as private, meaning they can only be accessed within the same class.

        **Example:**
        ```java
        class A {
            private int a;

            private void myMethod() {
                // Implementation
            }
        }
        ```
  2. **Private Classes:** We cannot declare a top-level class as `private`. However,we can declare inner classes (nested classes) as private. A private inner class can only be accessed by its enclosing class.
   
        **Example:**
    
        ```java
        public class OuterClass {
            private class InnerClass {
                // Implementation
            }
        }
        ```

3. **protected** 
- `protected` method can be accessed in same package but for different package as a subclass only.
- `protected` can be used for methods and member variables.
- It allows access within the same package and through inheritance.
- It cannot be used for top-level classes, but can be used for inner classes.

4. **default** 

- Whenever we don't use any access modifier then by default it will act as a default modifiers. Default method can be accessed in same package.

    **Example:**
    ```java
    class MyClass {
    ```

    ```java 
        int myVariable;
        void myMethod() { 
            // Implementation
        }
    }
    ```


    >NOTE: Not accessible from subclasses in different packages.

    **Default Classes:** Like methods and variables, we can also have top-level classes with default access. Such classes are accessible only within their own package.


## **Method Overloading**
Method overloading occurs when multiple methods in the same class have the same name but different parameters.

## **Polymorphism**
Polymorphism allows methods to perform different actions based on the object they are acting upon.

There are two types of polymorphism in Java:

- **Compile-time Polymorphism:** Achieved through method overloading.
- **Run-time Polymorphism:** Achieved through method overriding in inheritance
  
### **Need for Method Overloading**
**1. Code Reusability:**

Method overloading allows you to reuse the same method name for different purposes, reducing the need for multiple methods that perform similar tasks.

For example, if we have multiple ways to calculate an area, using overloaded methods like `calculateArea` with different parameters is more suitable than naming them `calculateAreaCircle`, `calculateAreaSquare`, etc.

**Example 1:**
```java
public class AreaCalculator {
    // Overloaded methods for calculating area
    double calculateArea(double radius) {
        return Math.PI * radius * radius; 
    }

    double calculateArea(double length, double width) {
        return length * width;
    }
```
```java
    double calculateArea(double base, double height, boolean isTriangle) {
        return 0.5 * base * height;
    }
}

public class Main {
    public static void main(String[] args) {
        AreaCalculator calculator = new AreaCalculator();

        System.out.println("Area of Circle: " + calculator.calculateArea(5));               
        System.out.println("Area of Rectangle: " + calculator.calculateArea(4, 6));        
        System.out.println("Area of Triangle: " + calculator.calculateArea(4, 5, true)); 
    }
}
```

**Example 2: Method for calculating sum**
```java
public double calculateSum(int a, double b) {
    return a + b;
}
```
**Example 3: Method for calculating product**
```java
public int calculateProduct(int a, double b) {
    return a * (int)b; // Converts double to int before multiplying
}
```

**Example 4: Method for formatting output**
```java 
public String formatOutput(int a, double b) {
    return "The values are: " + a + " and " + b;
}
```

**2. Polymorphic Behavior:**

Method overloading enables us to define multiple behaviors for a method based on its parameters. This is useful when operations may vary depending on the input type or number of parameters.

**Example:**
```java
class Logger {
    void log(String message) {
```
```java
        System.out.println("Log: " + message);
    }
    void log(String message, int level) {
        System.out.println("Log Level " + level + ": " + message);
    }

    void log(String message, String user) {
        System.out.println("Log by " + user + ": " + message);
    }
}
```

Method overloading is called compile-time polymorphism (or static polymorphism) because the decision about which method to call is made at compile time, based on the method signature (the method name and parameter list).


## **Constructor**

In Java, a constructor is a special method used to initialize objects. It has the same name as the class and does not have a return type, not even `void`.

Constructors are called when an instance of a class is created.

**Key Features of Constructors:**

- **Same Name as Class:** The constructor must have the same name as the class.
- **No Return Type:** Constructors do not have a return type.
- **Called Automatically:** They are called automatically when an object is created.
- **Can Be Overloaded:** we can have multiple constructors in a class with different parameter lists (constructor overloading).

**Types of Constructors:**
1. **Default Constructor:** A constructor with no parameters. If no constructor is provided in the class, Java automatically provides a default constructor.

    > NOTE: You can also define a constructor without parameters.

2. **Parameterized Constructor:** A constructor that takes parameters to initialize an object with specific values.

**Example 1: Default Constructor**

```java
class Dog {
    String name;
    // No constructors defined, so Java provides a default constructor
    void bark() {
        System.out.println(name + " says Woof!");
    }
```
```java
}
public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();  // Default constructor is called
        dog.bark();  // Output: null says Woof!
    }
}
```

**Example 2: Parameterized Constructor**
```java
class Dog {
    String name;

    // Constructor without parameter
    public Dog() {
        name = "Unknown";
    }

    // Parameterized constructor
    public Dog(String name) {
        this.name = name;
    }

    void bark() {
        System.out.println(name + " says Woof!");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog1 = new Dog();  // Calls default constructor
        dog1.bark();  // Output: Unknown says Woof!

        Dog dog2 = new Dog("Buddy");  // Calls parameterized constructor
        dog2.bark();  // Output: Buddy says Woof!
    }
}
```


> Important Notes: Constructors in Java cannot be static, abstract, final, or synchronized, among other things.

<br><br><br><br><br>

## **Arrays**

In Java, an array is a data structure that allows us to store multiple elements of the same type in a single variable.

### **Declaration**

```java
int[] numbers;      // Declaring an array of integers
int numbers[];      // Alternative syntax
int arr[], arr1;    // Multiple declarations
int[] arr, arr1;    // Multiple declarations with preferred syntax
```

### **Initialization**

```java
int[] numbers = new int[5];     // Declares an array of 5 integers
int numbers[] = new int[5];     // Alternative syntax
int numbers[] = {10, 20, 30, 40, 50}; // Direct initialization with values
int numbers[];
numbers = new int[5];           // Delayed initialization
```

> NOTE: We can initialize an array multiple times in a single program.

**Example:**

```java
int a[];
a = new int[5];
a = new int[3];
a = new int[4];
a[0] = 10;
a[1] = 20;
a[2] = 30;
```

### **Default Values in an Array**
In all cases, the array will have a default value for its elements:

For integers: `0`<br>
For boolean: `false`<br>
For object references: `null`<br>
For char: `'\0'`<br>
For String: `null` 
<br>
<br><br>

## **Example: Inheritance and Method Access**

```java
class Main {
    public static void main(String a[]) {
        A obj = new B();
        obj.m1();
        obj.m2(); // This line causes a compile-time error
        System.out.println(obj.a);
        System.out.println(obj.b); // This line causes a compile-time error
    }
}
class A {
    int a = 10;
    void m1() {
        System.out.println("m1 A called");
    }
}
class B extends A {
    int b = 20;
    void m2() {
        System.out.println("m2 B called");
    }
}
```

### **Reference Type vs. Object Type**

- **Declaration:** `A obj = new B();`

    - The reference type (`A`) determines the accessible methods and fields at compile time.
    - The actual object type (`B`) determines the methods executed at runtime.
    - Methods defined in class `B` and overridden methods will be executed, while only fields of type `A` will be accessible.
- **Invalid Assignment:** `B obj = new A();`

    - This is not allowed in Java because you cannot assign a superclass object (`A`) to a subclass reference (`B`). It violates type safety.

### **Data Members (Fields) vs. Methods**

**Example: Data Members**
```java
class A {
    int a = 10;
    void m1() {}
}
class B extends A {
```
```java
    int a = 20;
    void m1() {}
}
```
- **Field Binding (Compile-Time):** The reference type determines which field is accessed. For `A obj = new B();`, `obj.a` will access `A`'s field, resulting in `10`.

- **Method Binding (Runtime):** The actual object type determines which method is executed. For `A obj = new B();`, `obj.m1()` calls `B`'s overridden method.

**Example: Overriding Static Members**

```java
class Main {
    public static void main(String[] args) {
        A obj = new B();
        // Accessing instance variable and method
        System.out.println("Instance variable: " + obj.a); // Outputs: 10
        obj.m1(); // Outputs: "m1 B called"
        // Accessing static variable and method
        System.out.println("Static variable: " + obj.b); // Outputs: 5
        obj.staticMethod(); // Outputs: "Static method in class A"
    }
}

class A {
    int a = 10; // Instance variable
    static int b = 5; // Static variable

    void m1() {
        System.out.println("m1 A called");
    }
    static void staticMethod() {
        System.out.println("Static method in class A");
    }
}

class B extends A {
    int a = 20; // Instance variable
    static int b = 15; // Static variable

    void m1() {
        System.out.println("m1 B called");
    }

    static void staticMethod() {
        System.out.println("Static method in class B");
    }
}
```

### **Key Points**
1. **Instance Variables:**
    - Accessed based on the reference type, resolved at compile-time.
    - **Example:** `obj.a` accesses `A`'s field, resulting in `10`.

2. **Instance Methods:**
    - Executed based on the actual object type at runtime.
    - **Example:** `obj.m1()` calls `B`'s overridden method.

3. **Static Variables and Methods:**
    - Accessed based on the reference type, resolved at compile-time.
    - **Example:** `obj.b` and `obj.staticMethod()` access members of `A`.

### **Diagram Representation**
```
    +---------+            +---------+
    |    A    | <--------  |    B    |
    |         |            |         |
    | a = 10  |            | a = 20  |
    | m1()    |            | m1()    |
    +---------+            +---------+
          ^                      ^
          |                      |
          +----------------------+
                     |
                 +-------+
                 |  obj  |
                 +-------+
                 |   A   |  <-- Reference Type
                 +-------+
```

**Reference Variable:**

`obj`: This is a reference variable of type `A`, which points to an instance of `B`.

**Arrow Indications:**

The arrow from `obj` to `B` signifies that `obj` holds a reference to an object of type `B`.

**Example:**
```java
class Main {
    public static void main(String[] args) {
        A obj = new B(); 
        // Print the "address" (hash code) of the object created
```
```java
        System.out.println("Address of object (B): " + System.identityHashCode(obj));

        // Print the reference variable of type A
        System.out.println("Reference variable (obj): " + obj);
    }
}

class A {
    int a = 10;

    void m1() {
        System.out.println("m1 A called");
    }
}

class B extends A {
    int b = 20;

    void m1() {
        System.out.println("m1 B called");
    }
}
```
In Java, when you print a reference variable like `obj`, it does not directly display the memory address. Instead, it calls the `toString()` method of the object's class, which typically returns a string representation that includes the class name and a hash code.

## **Exceptions**
In Java, exceptions are events that disrupt the normal flow of a program.

**Types of Exceptions in Java:**

1. **Unchecked Exceptions:**
These are exceptions that don't need to be explicitly handled or declared.
They usually represent programming errors, like accessing an out-of-bounds array index.

    **Examples:** `NullPointerException`, `ArrayIndexOutOfBoundsException`.

2. **Checked Exceptions:**
These are exceptions that the compiler forces you to handle explicitly.
They must either be caught or declared in the method signature using the throws keyword.

    **Examples:** `IOException`, `SQLException`.

## **Throw and Throws**
In Java, both throw and throws are used for exception handling, but they serve different purposes:

- `throw:` Used to explicitly throw an exception from a method or block of code.

- `throws:` Used in a method declaration to declare that a method may throw one or more exceptions.


### **1. `throw` Keyword**
The `throw` keyword is used to explicitly throw an exception in your program. When you use `throw`, you create an exception and pass it to the runtime for handling.

**Syntax:**
```java
throw new ExceptionType("Message");
```

**Example:**

```java
public class ThrowExample {

    // Method to check age
    public static void checkAge(int age) {
        if (age < 18) {
            // Throwing an exception when age is less than 18
            throw new IllegalArgumentException("Age must be 18 or older.");
        }
        System.out.println("Age is valid.");
    }

    public static void main(String[] args) {
        try {
            checkAge(16);  // This will throw an IllegalArgumentException
        } catch (IllegalArgumentException e) {
            // Catching the thrown exception
            System.out.println("Caught exception: " + e.getMessage());
        }
    }
}
```

### **2. Division Example with Exception Handling**
```Enter the first number (integer): 10
Enter the second number (integer): 2
Result of 10 divided by 2: 5
End of iteration 1.
Enter the first number (integer): 20
Enter the second number (integer): 4
Result of 20 divided by 4: 5
End of iteration 2.
Enter the first number (integer): 30
Enter the second number (integer): 6
Result of 30 divided by 6: 5
End of iteration 3.
End of program.
```

### **3. Example with ArrayStoreException**
```java
public class Main {
    public static void main(String[] args) {
        // Create an array of Integers
        int[] arr = new int[5];
        
        try {
            // Attempting to store a String into an Integer array
            arr[0] = "Hello"; // This will throw ArrayStoreException
        } catch (ArrayStoreException e) {
            System.out.println("Caught an ArrayStoreException: " + e.getMessage());
        }
    }
}
```

### **Primitive vs. Object Arrays**

- `int[]`: An array of primitive types (`int`), while `Integer[]` is an array of reference types (`Integer`).
- `int[]` and `Integer[]` are fundamentally different in Java.
- `Integer` is an object (a wrapper class), while `int` is a primitive type.
- Java doesn't allow you to assign an `int[]` to an `Object[]` or any other array of objects, and similarly, an `Integer[]` array cannot be assigned to an array of primitive `int`.

## **ClassCastException**

ClassCastException is a runtime exception that occurs when you try to cast an object to a class type that it is not an instance of.

**Example:**
```java
public class Main {
    public static void main(String[] args) {

        // Create an object of type Object
        Object obj = new String("Hello, World!");

        try {
            // Try casting the Object to an Integer (which will throw ClassCastException)
            Integer num = (Integer) obj;
        } catch (ClassCastException e) {
            // Catch the ClassCastException and print the message
            System.out.println("Caught ClassCastException: " + e.getMessage());
        }
    }
}
```

- We create an `Object` reference obj that holds a `String object` (`"Hello, World!"`).
- We then try to cast `obj` to an `Integer` (which is an incompatible type for a `String` object).
- Since `obj` actually refers to a `String` and not an `Integer`, Java throws a `ClassCastException`.

>NOTE: `ClassCastException` is a runtime exception that occurs when you try to cast an object to a class type that it is not an instance of. Always make sure the object being cast is of the correct type to avoid this exception.

## **Multithreading**
Multithreading in Java is a concept that allows a program to perform multiple tasks concurrently, making better use of system resources like the CPU.

### **Thread in Java:**
A thread is a lightweight process that executes a small part of a program. In Java, threads can be created using the `Thread` class or the `Runnable` interface.

### **Thread Lifecycle:**
The lifecycle of a thread involves several states:

1. **New (Thread Creation):**

    - When a thread object is created, but it hasn’t been started yet, it is in the New state.
    - In this state, the thread is just an object. The start() method needs to be called to move the thread to the Runnable state.

    **Example:**
    ```java
    Thread t = new Thread();  // New state
    ```
2. **Runnable (Ready to Run):**

    - When the `start()` method is called on the thread, it moves to the Runnable state.
    - In this state, the thread is ready to be executed by the CPU. However, it doesn't mean it's currently executing, it's just waiting for CPU time.

    **Example:**
    ```java
    t.start();  // Thread is now in the Runnable state
    ```
3. **Running (Executing):**

    - When the thread gets CPU time and starts executing its task, it is in the Running state.
    - In this state, the thread is actively running and executing the code inside its `run()` method. If multiple threads are running, the CPU decides which one gets executed based on scheduling.

    **Example:** Once `start()` is called and the thread is granted CPU time, it enters the Running state and executes its `run()` method.

4. **Blocked (Waiting for Resources):**

    - When a thread wants to access a resource (like I/O, lock, etc.), but that resource is not available, the thread moves to the Blocked state.
    - The thread is unable to continue execution because it is waiting for a resource to become available. Once the resource is available, the thread moves back to the Runnable state.

5. **Dead (Terminated):**

   - When a thread completes its execution or is terminated due to an exception, it moves to the Dead state.
   - The thread has finished its work, and it cannot be restarted. Once a thread has completed its `run()` method or is interrupted, it enters the Dead state.

    **Example:**
    ```java
    t.start();  // Thread starts
    // thread completes its task and ends
    // After run() method finishes, the thread becomes dead.
    ```

### **Summary of Thread States**
- `New:` Thread object created, but not yet started.
- `Runnable:` Thread is ready to run, waiting for CPU time.
- `Running:` Thread is actively executing.
- `Blocked:` Thread is waiting for a resource (e.g., lock, I/O).
- `Dead:` Thread has finished its execution or has been terminated.

### **Thread Creation**
1. **Using the `Thread` Class:**

    In Java, you can create a thread by extending the `Thread` class. You need to override the `run()` method, where you write the code that the thread will execute.

    **Example:**
    ```java
    class MyThread extends Thread {
        public void akash() {
            System.out.println("Thread is running");
        }
    }

    public class Main {
        public static void main(String[] args) {
    ```
    ```java
            MyThread t = new MyThread();
            t.start();  // start() method calls the run() method
        }
    }
    ```

2. **Using the `Runnable` Interface:**

    You can also create a thread by implementing the Runnable interface. In this case, you need to define the `run()` method.

    **Example:**

    ```java
    class MyRunnable implements Runnable {
        public void run() {
            System.out.println("Thread is running");
        }
    }

    public class Main {
        public static void main(String[] args) {
            MyRunnable task = new MyRunnable();
            Thread t = new Thread(task);
            t.start();
        }
    }
    ```
### **Explanation of Runnable Approach**
1. **Defining the MyRunnable Class:**
We created a class called `MyRunnable` that implements the `Runnable` interface. This means we have to define the `run()` method inside the class. The `run()` method contains the code that the thread will execute when it runs.

2. **Implementing the run() Method:**
Inside the `run()` method, we wrote a simple print statement "`Thread is running`". This is the action that will be performed by the thread when it is executed.

3. **Creating a Runnable Object:**
We created an object of the `MyRunnable` class called task. This object represents the code that the thread will run.

4. **Creating a Thread Object:**
We then created an object of the `Thread` class, called t, and passed the task object to the Thread constructor. This tells the `thread` what code to run (which is in the task object).

5. **Calling the start() Method:**
Finally, we called the `start()` method on the Thread object t. This method starts the thread, and the thread will then run the code in the `run()` method (which is the print statement "`Thread is running`").

<br>

## **Method Overriding**
Method Overriding in Java is a concept where a subclass provides its own implementation of a method that is already defined in its superclass. The method in the subclass must have the same name, return type, and parameters as the method in the superclass.

**Example:**
```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override  // @Override annotation is optional, but it helps to avoid mistakes
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal myAnimal = new Animal();
        Animal myDog = new Dog();

        myAnimal.sound();  // Output: Animal makes a sound
        myDog.sound();     // Output: Dog barks
    }
}
```

### **Explanation**
1. **Parent Class Animal:**

    - The Animal class contains a method `sound()` that by default prints "`Animal makes a sound`".

2. **Child Class Dog:**

    - The Dog class overrides the `sound()` method from the Animal class. Now, the `sound()` method in Dog prints "`Dog barks`" instead.

3. **Method Overriding in Action:**

   - When the line `myDog.sound()` is called, even though `myDog` is a reference of type `Animal`, it points to an object of type `Dog`.
   - This is where runtime polymorphism comes into play. At runtime, Java decides to call the `sound()` method of the `Dog` class, not the `Animal` class.

<br>

## **Thread Management and Synchronization**
### 1. **Thread Priorities**
Thread priorities are used to give one thread more or less importance compared to others. In Java, thread priority ranges from 1 (lowest priority) to 10 (highest priority). The default priority is 5.

**Example:**
```java
Thread t1 = new Thread();
t1.setPriority(Thread.MAX_PRIORITY);  // Priority 10 (Highest)
t1.start();

Thread t2 = new Thread();
t2.setPriority(Thread.MIN_PRIORITY);  // Priority 1 (Lowest)
t2.start();
```

In this example, `t1` is assigned the highest priority (`10`), and `t2` is assigned the lowest priority (`1`).

### 2. **Synchronization**
Synchronization is used to prevent data corruption in a multi-threaded environment. If one thread is accessing a shared resource, other threads are prevented from accessing it until the first thread completes its task.

**Example:**
```java
class Counter {
    private int count = 0;

    public synchronized void increment() {
        count++;  // Only one thread can access this method at a time
    }

    public int getCount() {
        return count;
    }
}
```

Here, the `increment()` method is synchronized, ensuring that only one thread can increment the c`ount` at a time.

### 3. **Messaging (for Intercommunication of Threads)**
Thread messaging is used when one thread communicates with another. Java provides methods like `wait()`, `notify()`, and `notifyAll()` for thread communication.
<br><br><br>

**Example:**

```java
class Message {
    private String message;
    public synchronized void setMessage(String message) {
        this.message = message;
        notify();  // Notify waiting thread
    }
    public synchronized String getMessage() throws InterruptedException {
        wait();  // Wait for message to be set
        return message;
    }
}
```
In this example, one thread sets a message using `setMessage()`, and another thread fetches the message using `getMessage()`. The second thread waits until it is notified by the first thread.

### 4. **Thread Classes**
In Java, threads can be created in two ways:

- **Extending the Thread Class:** By creating a subclass of the Thread class and overriding its `run()` method.
- **Implementing the Runnable Interface:** By implementing the Runnable interface and defining the `run()` method.

### 5. **Suspending, Resuming, and Stopping Threads**

- **Suspending a Thread:** The `suspend()` method was used to temporarily suspend a thread, but it is now deprecated due to potential deadlocks.
- **Resuming a Thread:** The `resume()` method was used to resume a suspended thread, but it is also deprecated.
- **Stopping a Thread:** The `stop()` method was used to stop a thread, but it is deprecated because it can cause resource leaks and inconsistent states.
- **Best Practice:** To safely stop a thread, the `interrupt()` method should be used.

**Example:**
```java
Thread t = new Thread(() -> {
    while (!Thread.currentThread().isInterrupted()) {
        // Thread executes
    }
});
t.start();
t.interrupt();  // Interrupting the thread
```

In this example, the thread runs a loop until it is interrupted using the `interrupt()` method.

## **File Handling**
File handling in Java refers to the process of reading from and writing to files stored on a computer or other storage devices.

1. **Creating a File Using the `File` Class**

    This example demonstrates how to create a new file if it doesn't already exist.

    ```java
    import java.io.File;
    import java.io.IOException;

    public class Handler {
        public static void main(String[] args) {
            // Define file path
            File file = new File("newfile.txt");

            try {
                // Create the file if it doesn't already exist
                if (file.createNewFile()) {
                    System.out.println("File created: " + file.getName());
                } else {
                    System.out.println("File already exists.");
                }

                // Print the absolute path of the file
                System.out.println("File absolute path: " + file.getAbsolutePath());
            } catch (IOException e) {
                System.out.println("An error occurred.");
                e.printStackTrace();
            }
        }
    }
    ```

2. **Writing Data to an Existing File**

    This example shows how to write data to a file using `FileWriter`.

    ```java
    import java.io.FileWriter;
    import java.io.IOException;

    public class Handler {
        public static void main(String[] args) {
            // Use FileWriter to write to the file
            try (FileWriter writer = new FileWriter("newfile.txt")) {
                // Write text to the file
                writer.write("Hello, this is a test file.\n");
                writer.write("This is the second line of the file.");
    ```
    ```java
                System.out.println("Data written to the file.");
            } catch (IOException e) {
                System.out.println("An error occurred.");
                e.printStackTrace();
            }
        }
    }
    ```
3. **Reading Data from the File**

    This example demonstrates how to read the content of a file using `BufferedReader`.
    ```java
    import java.io.FileReader;
    import java.io.BufferedReader;
    import java.io.IOException;

    public class Handler {
        public static void main(String[] args) {
            // Use BufferedReader to read data from the file
            try (BufferedReader reader = new BufferedReader(new FileReader("newfile.txt"))) {
                String line;
                // Read each line of the file
                while ((line = reader.readLine()) != null) {
                    System.out.println(line);  // Print the content of the file
                }
            } catch (IOException e) {
                System.out.println("An error occurred.");
                e.printStackTrace();
            }
        }
    }
    ```
4. **Appending Data to an Existing File**

    This example shows how to append data to an existing file using `FileWriter` with the append flag set to true.

    ```java
    import java.io.FileWriter;
    import java.io.IOException;

    public class Handler {
        public static void main(String[] args) {
            // Use FileWriter to append to the file
            try (FileWriter writer = new FileWriter("newfile.txt", true)) {
                // Append data to the file
    ```
    ```java
                writer.write("\nThis line is appended to the file.");
                System.out.println("Data appended to the file.");
            } catch (IOException e) {
                System.out.println("An error occurred.");
                e.printStackTrace();
            }
        }
    }
    ```

5. **Viewing File Properties (Size, Path, etc.)**

    This example demonstrates how to retrieve and display file properties like size and path.

    ```java
    import java.io.File;

    public class Handler {
        public static void main(String[] args) {
            // Create a File object
            File file = new File("newfile.txt");

            // Check if file exists and display its properties
            if (file.exists()) {
                System.out.println("File Name: " + file.getName());
                System.out.println("File Path: " + file.getAbsolutePath());
                System.out.println("File Size in bytes: " + file.length());
                System.out.println("Is it a directory? " + file.isDirectory());
            } else {
                System.out.println("File does not exist.");
            }
        }
    }
    ```

6. **Deleting a File**

    This example demonstrates how to delete a file if it exists.

    ```java
    import java.io.File;

    public class Handler {
        public static void main(String[] args) {
            File file = new File("newfile.txt");

            if (file.exists()) {
                if (file.delete()) {
                    System.out.println("File deleted successfully.");
                } else {
    ```
    ```java
                    System.out.println("Failed to delete the file.");
                }
            } else {
                System.out.println("File does not exist.");
            }
        }
    }
    ```

7. **Creating a Directory**

    This example shows how to create a new directory using `Files.createDirectory()` from the `java.nio.file` package.

    ```java
    import java.nio.file.*;
    import java.io.IOException;

    public class Handler {
        public static void main(String[] args) {
            Path dirPath = Paths.get("newDirectory");

            try {
                // Create the directory if it doesn't exist
                if (!Files.exists(dirPath)) {
                    Files.createDirectory(dirPath);
                    System.out.println("Directory created: " + dirPath.getFileName());
                } else {
                    System.out.println("Directory already exists.");
                }
            } catch (IOException e) {
                System.out.println("An error occurred while creating the directory.");
                e.printStackTrace();
            }
        }
    }
    ```
