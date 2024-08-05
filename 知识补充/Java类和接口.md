类（Class）和接口（Interface）是 Java 编程语言中的两种核心概念，它们有着不同的用途和特性。以下是它们的主要区别：

### 1. 定义和用途

- **类（Class）**：
  - **定义**：类是创建对象的蓝图或模板。它定义了对象的属性（字段）和行为（方法）。
  - **用途**：用于实现具体的对象和逻辑。类可以实例化对象，包含方法的具体实现。
  
- **接口（Interface）**：
  - **定义**：接口是一个抽象类型，它定义了一组方法，但不提供实现。这些方法必须由实现接口的类来实现。
  - **用途**：用于定义某种行为的规范，强调了实现者必须遵守的契约。接口不能实例化对象，只能由类实现。

### 2. 继承关系

- **类（Class）**：
  - **继承**：类使用关键字 `extends` 来继承另一个类。Java 是单继承的，也就是说一个类只能继承一个父类。
  - **实现接口**：类可以使用关键字 `implements` 来实现一个或多个接口。

- **接口（Interface）**：
  - **继承**：接口使用关键字 `extends` 来继承一个或多个接口。接口可以多继承。

### 3. 实现方式

- **类（Class）**：
  - **方法实现**：类中可以包含方法的具体实现。
  - **字段（变量）**：类可以包含实例变量和类变量（静态变量）。

- **接口（Interface）**：
  - **方法实现**：接口中的方法默认是抽象的，不能有具体实现（Java 8 以后可以有默认方法和静态方法）。
  - **字段（变量）**：接口中只能包含常量（默认 `public static final`）。

### 4. 访问修饰符

- **类（Class）**：
  - 可以使用所有的访问修饰符：`private`、`default`（包级私有）、`protected` 和 `public`。

- **接口（Interface）**：
  - 方法默认是 `public`，只能是 `public` 或者默认（包级私有）。
  - 变量默认是 `public static final`。

### 5. 示例代码

#### 类的示例：

```java
// 定义一个类
public class Animal {
    private String name;

    // 构造方法
    public Animal(String name) {
        this.name = name;
    }

    // 方法
    public void makeSound() {
        System.out.println("Animal sound");
    }

    // 获取名字
    public String getName() {
        return name;
    }
}

// 继承类
public class Dog extends Animal {
    public Dog(String name) {
        super(name);
    }

    @Override
    public void makeSound() {
        System.out.println("Woof");
    }
}
```

#### 接口的示例：

```java
// 定义一个接口
public interface Animal {
    // 接口中的方法默认为public abstract
    void makeSound();
    String getName();
}

// 实现接口的类
public class Dog implements Animal {
    private String name;

    public Dog(String name) {
        this.name = name;
    }

    @Override
    public void makeSound() {
        System.out.println("Woof");
    }

    @Override
    public String getName() {
        return name;
    }
}
```

### 总结

- **类（Class）**：用于实现具体对象的模板，包含属性和方法的具体实现，可以继承另一个类并实现多个接口。
- **接口（Interface）**：用于定义行为规范，不包含具体实现，只能包含抽象方法（Java 8 以后可以有默认方法和静态方法），可以被类实现并且接口间可以多继承。

类和接口的设计使得 Java 可以实现强大的面向对象编程，支持多态、封装和接口继承等特性。