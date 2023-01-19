# Introduction to Python

### What is python?

Python is a popular programming language. It was created by Guido van Rossum, and released in 1991. It is used for web development (server-side), software development, mathematics, and system scripting. Python is a dynamic, interpreted (byte code-compiled) language. There are no type declarations of variables, parameters, functions, or methods in the source code. This makes the code short and flexible, and you lose the compile-time type checking of the source code. Python tracks the types of all values at runtime and flags code that does not make sense as it runs.

### First Python Program

Most programmers start their programming journey by printing “Hello, World!” in the console. It is so much popular that now it became a tradition. So, we will also start by running the hello world program.

```python
>>> print("Hello, World!")
Hello, World!
```

Here `print()` is a function and `“Hello, World!”` . We are passing the string through the `print()`

function and the function is printing the given string in the display.

### Python Syntax

Python’s syntax is so much more readable. It was actually designed for readability and has some similarities to the English language with influence from mathematics.

Python syntax can be executed by writing directly in the Command Line:

```python
>>> print("Hello, World!")
Hello, World!
```

Or by creating a python file on the server, using the .py file extension, and running it in the Command Line:

```python
C:\Users\Your Name>python myfile.py
```

### Python Indentation

Unlike some other programming languages, python uses indentation to indicate a block of code.

If you write this code, you will get an error:

```python
if 5 > 2:
print("Five is greater than two!")
```

Because this code is not properly indented. The number of spaces that you want to give is totally up to you. Giving 4 spaces is a good practice. You also make sure that you are not doing unnecessary indentation otherwise again you will get an error.

```python
if 5 > 2:
 print("Five is greater than two!")
        print("Five is greater than two!")
```

### **Comments**

Sometimes you need to add some text to your code to describe how your code is working. In that case, you have to use the proper commenting rule. Comments start with a `#`, and Python will render the rest of the line as a comment:

```python
#This is an example of a comment
#This is a comment
print("Like and share this post")
```

Comments can also be placed at the end of a line, and Python will ignore the rest of the line:

```python
print("Like and share this post") #This is an example of a comment
```

You can also comment out even multiple lines of code to prevent Python from executing:

```python
#print("Follow Me")
print("Hi there!")
```

you can add a multi-line string (triple quotes) in your code, and place your comment inside it:

```python
"""
This is a multiline
comment.
"""
print("Hello, World!")
```
