Core Definition :

- An Interface with one abstract method also called as Single Abstract Method.
- It is known as functional interface because it wraps a function as an interface.
- FI can have any number of default, static and overridden methods.
- If FI uses more than one abstract method, then it will generate a compile error.

Types with example :

**Predicate Functional Interface**

- A predicate functional interface is the one whose method accepts one argument, and it will return either true or false.
- A predicate functional interface is mainly used in comparison to sort elements or to filter a value based on certain condition(s) applied on the input passed.
- Java provides predicate functional interfaces for primitives as well as IntPredicate, DoublePredicate, and LongPredicate, which accept only Integer, Double, and Long respectively.
- Usage : Predicate predicate = (value) -> value != 0; or Predicate predicate = (value) -> test(value);
- Example : 
      isEvenNumber check
        List<Integer> numbers = Arrays.asList(1,2,3,4,5,6,7,8,9);
        Predicate<Integer> evenNums = n -> n%2 == 0;
        numbers = numbers.stream().filter(evenNums).toList();
        System.out.println(numbers);

**Consumer Functional Interface**

- A consumer functional interface is one whose method accepts one argument and will not return anything.
- A consumer functional interface is mainly used for side effect operations.
- A BiConsumer functional interface can accept two parameters.
- Java provides consumer functional interfaces for primitives as well as IntConsumer, DoubleConsumer, and LongConsumer, which accept only Integer, Double, and Long respectively.
- Usage : Consumer consumer = (value) -> System.out.println(value); or Consumer consumer1 = System.out::println; or Consumer consumer2 = (value) -> accept(value);
  - Example :
        Print all numbers present in the list.
        List<Integer> numbers = Arrays.asList(1,2,3,4,5,6,7,8,9);
        Consumer<Integer> consumer = (value) -> System.out.println(value);
        Consumer<Integer> consumer1 = System.out::println;
        System.out.println("Printing using consumer functional interface as lambda expression");
        numbers.forEach(consumer);
        System.out.println("Printing using consumer functional interface as method reference");
        numbers.forEach(consumer1);

**Supplier Functional Interface**

- The supplier functional interface is the one whose method does not have any arguments to pass and will return a value.
- A supplier functional interface is mainly used to generate values lazily.
- Usage : Supplier supplier = () -> Math.random() * 10; or Supplier supplier1 = () -> get();
  - Example : 
        Supplier<Integer> supplier = (int) -> Math.random() * 10;
        List<Integer> randomNums = new ArrayList();
        for(int i=0;i<=10;i++) {
            randomNums.add(supplier.get())
        }
        System.out.println(randomNums);

**Function Functional Interface**

- Function functional interface is one whose method accepts one argument and will return a value.
- A function functional interface is mainly used to get the processed value.
- There are other variants of Function as well like BiFunction.
- Java provides function functional interfaces for primitives as well as IntFunction, DoubleFunction, and LongFunction, which accept only Integer, Double, and Long respectively.
- Two more utility interfaces UnaryOperator which extends Function Interface and BinaryOperator which extends Bi-Function Interface.
- Usage : Function function = (value) -> Math.random() * 10; or Function function1 = (value) -> apply(value);
    - Example :
      List<Integer> numbers = Arrays.asList(1,2,3,4,5,6,7,8);
      Function<Integer, Integer> squared = (value) -> value * value;
      List<Integer> squaredNumbers =  numbers.stream().map(squared).toList();
      System.out.println(squaredNumbers);

Note : With Java, many existing interfaces are annotated as functional interfaces and can be used in lambda expressions. For example:
    * Runnable − provides run() method
    * Callable − provides call() method
    * Actionlistener − provides actionPerformed() method
    * Comparable − provides compareTo() method to compare two numbers