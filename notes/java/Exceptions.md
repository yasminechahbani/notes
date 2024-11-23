



In Java, exceptions are divided into two main categories: **checked** and **unchecked** exceptions. These two types determine how Java handles exceptions at compile-time and runtime, and they each have specific use cases and handling requirements.

### 1. Checked Exceptions
Checked exceptions are exceptions that are checked at **compile-time**. Java forces you to either handle these exceptions using a `try-catch` block or declare them using the `throws` keyword in the method signature. If you fail to handle or declare them, the code won’t compile.

#### Characteristics:
- **Compile-Time Checking**: Checked exceptions are detected by the compiler, so they must be either caught or declared in the method signature.
- **Recoverable Situations**: They often represent situations that a program might recover from, like reading a file or connecting to a database. For example, if a file is missing, you might notify the user and allow them to select a different file.
- **Common Examples**: `IOException`, `SQLException`, `FileNotFoundException`.

#### Example:
```java
public void readFile(String filePath) throws IOException {
    FileReader fileReader = new FileReader(filePath); // IOException must be handled or declared
}
```

### 2. Unchecked Exceptions
Unchecked exceptions are exceptions that are not checked at compile-time but instead are checked at **runtime**. These are also known as **runtime exceptions**, and the compiler doesn’t force you to handle or declare them. This means you don’t need to use `try-catch` or `throws` for unchecked exceptions, though you can if you want to.

#### Characteristics:
- **Runtime Checking**: Unchecked exceptions are only caught at runtime, so the compiler doesn’t check if they are handled or declared.
- **Programming Errors**: They typically indicate programming logic errors that the program cannot easily recover from, like accessing an out-of-bounds array index or calling a method on a `null` object.
- **Common Examples**: `NullPointerException`, `ArrayIndexOutOfBoundsException`, `ArithmeticException`.

#### Example:
```java
public void divide(int a, int b) {
    int result = a / b; // ArithmeticException (division by zero) is unchecked
}
```

### Key Differences Between Checked and Unchecked Exceptions
| Feature               | Checked Exceptions                         | Unchecked Exceptions                   |
|-----------------------|--------------------------------------------|----------------------------------------|
| **Checked at**        | Compile-time                               | Runtime                                |
| **Forced Handling**   | Must be handled with `try-catch` or `throws`| No forced handling                     |
| **Typical Use**       | External issues (I/O, networking)          | Programming errors (logic flaws)       |
| **Examples**          | `IOException`, `SQLException`              | `NullPointerException`, `ArithmeticException` |

### Why Two Types of Exceptions?
Java’s checked exceptions encourage programmers to think about error handling at compile time, especially for operations where failures are likely and may be recoverable. However, forcing every exception to be handled can lead to overly verbose code and poor practices (like catching generic `Exception` types just to satisfy the compiler). Unchecked exceptions provide more flexibility, particularly for coding errors that are often best fixed in code rather than handled at runtime.

### When to Use Checked vs. Unchecked Exceptions
- **Use Checked Exceptions** when the caller might reasonably handle the error, like file handling or database operations.
- **Use Unchecked Exceptions** for programming mistakes that should not be handled by the caller, like accessing an invalid index or dividing by zero.