# Java Shadowing Problems

## Problem 1: Shadowing in Nested Scopes

### Description
Shadowing can happen in nested scopes, where variables declared in a more local scope can hide variables of the same name from an outer scope.

Consider this Java program:

java
public class ShadowingExample {
    static int value = 100;

    public static void outerFunction() {
        int value = 50;
        {
            int value = 25;
            System.out.println("Innermost value: " + value);
        }
        System.out.println("Outer value: " + value);
    }

    public static void main(String[] args) {
        outerFunction();
        System.out.println("Global value: " + value);
    }
}


#Tasks
1. Predict the Output
Predict what will be printed when this program is executed.

2. Modify to Access All Variables
Modify the outerFunction so that it prints all three value variables (global, outerFunction, and innermost block) inside the innermost block.

Requirements
Use Java's scope resolution to access the shadowed variables (e.g., by referencing this or class name).
Ensure the program compiles and runs correctly after modifications.
Problem 2: Variable Shadowing with Closures (Java)
Description
Variable shadowing can also happen in Java when working with anonymous classes or lambdas (closures). Consider the following Java example using a lambda expression.

java
Copy code
import java.util.ArrayList;
import java.util.List;

public class ClosureExample {
    public static void main(String[] args) {
        List<Runnable> counters = new ArrayList<>();

        for (int i = 0; i < 3; i++) {
            counters.add(() -> System.out.println(i));
        }

        counters.get(0).run(); // ?
        counters.get(1).run(); // ?
        counters.get(2).run(); // ?
    }
}
Tasks
1. Explain the Output
Explain the output of each counters.get(index).run() and why this behavior occurs.

2. Fix the Shadowing Issue
Modify the ClosureExample so that each lambda prints the correct index (0, 1, 2) when executed.

3. Use Local Variables to Prevent Shadowing
Refactor the original code so that each lambda retains the correct index without needing to create new methods or structures.

Requirements
Provide code snippets for the modified solution.
Explain how shadowing happens in closures and how to fix it with local variable references.
