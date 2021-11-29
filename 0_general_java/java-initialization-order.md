
#### Java Initialization Order
- sırasıyla static variables and static initializers
- sırasıyla instance variables and instance initializers
- constructors


1. Parent static variables
2. Parent static initializer block is invoked
3. Child static variables
4. Child static initializer block is invoked
5. Parent instance variables
6. Parent instance initializer block is invoked
7. Parent class constructor invoked
8. Child instance variables
9. Child instance initializer block is invoked
10. Child class constructor invoked
11. Parent instance initializer block is invoked (3. instance oluşturuluyor.)
12. Parent class constructor invoked 10
13. Child instance initializer block is invoked
14. Child class constructor invoked 10

```java
class Parent {
    private int parentInstanceVariable = 0;
    private static int parentStaticVariable = 0;

    {
        System.out.println("Parent instance initializer block is invoked");
    }

    static {
        System.out.println("Parent static initializer block is invoked");
    }

    Parent() {
        System.out.println("Parent class constructor invoked");
    }

    Parent(int a) {
        System.out.println("Parent class constructor invoked " + a);
    }
}
class Child extends Parent {
    private int childInstanceVariable = 0;
    private static int childStaticVariable = 0;
    {
        System.out.println("Child instance initializer block is invoked");
    }

    static {
        System.out.println("Child static initializer block is invoked");
    }

    Child() {
        super();
        System.out.println("Child class constructor invoked");
    }

    Child(int a) {
        super(a);
        System.out.println("Child class constructor invoked " + a);
    }

    public static void main(String args[]) {
        Child b1 = new Child();
        Child b2 = new Child(10);
    }
}
```
