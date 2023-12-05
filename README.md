# MiniJava Compiler

## Overview
This is a simple compiler for `MiniJava`, a minimalistic Java-like programming language. The compiler is implemented in `JavaCC` and was built as part of the "Compilerbau" course at FH Aachen. It can be used to compile `MiniJava` source code into `Java` bytecode.

## Usage

### Using the included JAR
1. Ensure you have `Java` installed on your system.
2. Open a terminal and navigate to the `compiler` directory containing the `MiniJava.jar` file (or get the release [here](https://github.com/BlackyDrum/mini-java-compiler/releases)).
3. Run the following command to compile a `MiniJava` source file:
```
$ java -jar MiniJava.jar < mySourceFile.txt
```
5. The compiler will generate a `Java` class file named `MiniJavaClassFile.class`. Run the compiled class file with the following command:
```
$ java MiniJavaClassFile
```

### Compiling the source code manually
1. Ensure you have `Java` and `JavaCC` installed on your system.
2. Open a terminal and navigate to the `src` directory.
3. Run the following command to generate the `Java` parser:
```
$ javacc MiniJava.jj
```
4. Compile the generated `Java` files:
```
$ javac MiniJava.java
```
5. Run the following command to compile a `MiniJava` source file:
```
$ java MiniJava < mySourceFile.txt
```
6. The compiler will generate a `Java` class file named `MiniJavaClassFile.class`. Run the compiled class file with the following command:
```
$ java MiniJavaClassFile
```

## Sample MiniJava Code
**Example 1:**
```java
final int n = 10;
func fib(int n) {
        int result = 0;
        if n <= 1 {
                result = n;
        }
        else {
                result = fib(n - 1) + fib(n - 2);
        }
	return (result);
}
print(fib(n));
```

**Example 2:**
```java
final int a = 3, b = 6;
int c = 2, d = 6, i = 0;
void myPrint(int i) {
        print(i);
}

func f1(int a, int b) {
        int c = 2;
        if a < b {
                c = a + 1;
                d = 5 + 5;
                while c < 15 {
                        c = c + 1;
                }
        }
        else {
                d = 33;
        }
        return (c + d);
}
{
	while i < 10 {
		i = i + 1;
		if i == 5 {
			i = i + 10;
		}
		else {
			print(i);
		}
	}
	myPrint(f1(1, 5));
}

```

## LL(1) Grammar Analyzer
I have also built a calculator for generating `first`, `follow`, and `lookahead` sets to check if a grammar is `LL(1)`. You can find the calculator [here](https://blackydrum.github.io/first-follow-ll1-calculator/).
Feel free to explore and use it in conjunction with the `MiniJava` compiler. The `MiniJava` language grammar used by the compiler is also available in this repository. <br> <br>
**Please note that the provided grammar is not `LL(1)` due to the presence of the 'else' keyword in the `<optElse>` production, which introduces ambiguity. This is because after seeing an `if` statement, the parser cannot determine whether to expand `<optElse>` to `else` `<statement>` or to `epsilon`.**


