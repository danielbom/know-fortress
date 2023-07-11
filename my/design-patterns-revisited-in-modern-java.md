---
tags: programming,Java
---

Based on this [youtube video](https://www.youtube.com/watch?v=V7iW27F9oog&ab_channel=DevoxxUK).

# Topics

- Design and design patterns
- Optional: pattern and anti-patterns
- Lightweight Strategy
- Factory Method using default methods
- Decorators using Lambda Expressions
- Execute Around Method Pattern
- Creating a Closed Hierarchy with sealed
- Summary

---

## Optional: pattern and anti-patterns

```java
import java.util.*;

public class Example {
  public static void main(String[] args) {
    Optional<String> optional = Optional.empty();

    // bad idea
    optional.get();

    // good
    optional.orElse("...");
    optional.orElseThrow(() -> new NullPointerException());
  }
}

class SampleOld {
  public void setName(String name) {
    // old code
    if (name == null) { // null is smell
      // use a default value
    } else {
      // use the given name
    }
  }
}

class SampleOptional {
  public void setName(Optional<String> name) { // bad idea
    if (name.isPresent()) {
      // use the value
    }
  }

  public Optional<String> getName() {
    return null; // Oh no
  }

  public static void example() {
    SampleOptional sample = new SampleOptional();
    sample.setName(Optional.empty());
    sample.setName(Optional.of("Some name"));
  }
}

class SampleEmpathy {
  // Code should reflect empathy
  public void setName() {
    // use default value
  }

  public void setName(String name) {
    // use the given name
  }

  public static void example() {
    SampleEmpathy sample = new SampleEmpathy();
    sample.setName();
    sample.setName("Some name");
  }
}
```

---

## Lightweight Strategy

```java
import java.util.*;
import java.util.function.*;


public class Example {
  public static int totalAllValues(List<Integer> values,
      Predicate<Integer> predicate) {
    int result = 0;

    for (var number : values) {
      if (predicate.test(number)) {
        result += number;
      }
    }

    return result;
  }

  public static int totalAllValues(List<Integer> values) {
    int result = 0;

    for (var number : values) {
      result += number;
    }

    return result;
  }

  public static int totalAllEvenValues(List<Integer> values) {
    int result = 0;

    for (var number : values) {
      if (number % 2 == 0) {
        result += number;
      }
    }

    return result;
  }

  public static void main(String[] args) {
    var values = List.of(1, 2, 3, 4, 5, 6, 7, 8);

    System.out.println(totalAllValues(values));
    System.out.println(totalAllEvenValues(values));
    System.out.println(totalAllValues(values, (x) -> x % 2 == 0));
  }
}

```

## Factory Method using default methods

```java
class Pet {}
class Dog extends Pet {
  public String toString() {
    return "Dog";
  }
}
class Cat extends Pet {
  public String toString() {
    return "Cat";
  }
}

interface Person {
  Pet getPet();

  default void play() {
    System.out.println("Playing with " + getPet());
  }
}

class DogPerson implements Person {
  Pet pet = new Dog();

  public Pet getPet() {
    return pet;
  }
}

class CatPerson implements Person {
  Pet pet = new Cat();

  public Pet getPet() {
    return pet;
  }
}

public class Example {
  public static void main(String[] args) {
    new CatPerson().play();
    new DogPerson().play();
  }
}

```

## Decorators using Lambda Expressions

### Function composition

```java
import java.util.*;
import java.util.function.*;

public class Example {
  public static void print(int number, String message,
      Function<Integer, Integer> func) {
    System.out.println(number + " " + message + ": " +
        func.apply(number));
  }

  public static void main(String[] args) {
    Function<Integer, Integer> inc = number -> number + 1;

    print(5, "incremented", inc);
    print(6, "incremented", inc);

    Function<Integer, Integer> doubleIt = number -> number * 2;
    print(5, "doubled", doubleIt);
    print(6, "doubled", doubleIt);

    var incAndDoubleIt = inc.andThen(doubleIt);
    print(5, "incremented and doubled", incAndDoubleIt);
  }
}

```

### Camara decorator

```java
import java.util.*;
import java.util.function.*;
import java.util.stream.*;
import java.awt.Color;

class Camara {
  private Function<Color, Color> filter;

  public Camara(Function<Color, Color> aFilter) {
    filter = aFilter;
  }

  public static Camara createWithFor(Function<Color, Color>... filters) {
    Function<Color, Color> filter = Function.identity();

    for (var aFilter : filters) {
      filter = filter.andThen(aFilter);
    }

    return new Camara(filter);
  }

  public static Camara create(Function<Color, Color>... filters) {
    var filter = Stream.of(filters)
      .reduce(Function.identity(), Function::andThen);
    return new Camara(filter);
  }

  public Color snap(Color input) {
    return filter.apply(input);
  }
}

public class Example {
  public static void print(Camara camara) {
    System.out.println(camara.snap(new Color(125, 125, 125)));
  }

  public static void main(String[] args) {
    print(Camara.create());
    print(Camara.create(Color::brighter));
    print(Camara.create(Color::darker));
    print(Camara.create(Color::brighter, Color::darker));
  }
}
```

## Execute Around Method Pattern

```java
import java.util.*;
import java.util.function.*;

class Resource implements AutoCloseable {
  public Resource() {
    System.out.println("creating an external resource");
  }

  public Resource op1() {
    System.out.println("op1");
    return this;
  }

  public Resource op2() {
    System.out.println("op2");
    return this;
  }

  public void close() {
    System.out.println("cleaning up external resource");
  }

  public static void use(Consumer<Resource> block) {
    var resource = new Resource();
    try {
      block.accept(resource);
    } finally {
      resource.close();
    }
  }
}

public class Example {
  public static void autoCloseable() {
    try(Resource resource = new Resource()) {
      resource.op1();
      resource.op2();
    }
  }
  public static void call() {
    Resource.use(resource -> resource.op1().op2());
  }
  public static void main(String[] args) {
    call();
  }
}

```
