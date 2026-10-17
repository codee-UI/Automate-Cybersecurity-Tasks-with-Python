# Explore Debugging Techniques in Python

## Introduction

Errors are a normal part of developing code in Python. Understanding the different types of errors and learning how to debug them helps programmers identify and fix problems efficiently.

There are three main types of errors in Python:

1. Syntax errors
2. Logic errors
3. Exceptions

This document explores these errors and debugging strategies, including debuggers, print statements, and AI-powered coding assistants.

---

## 1. Types of Errors

### 1.1 Syntax Errors

A **syntax error** occurs when Python code violates the language's syntax rules.

Common examples include:

- Forgetting a closing quotation mark.
- Missing a closing bracket or parenthesis.
- Forgetting a colon (`:`) after an `if` statement or function definition.
- Using incorrect indentation.

#### Example: Missing quotation mark

```python
message = "You are debugging a syntax error
print(message)
```

**Output:**

```text
SyntaxError: unterminated string literal
```

The error occurs because the string is missing a closing quotation mark.

#### Corrected code

```python
message = "You are debugging a syntax error"
print(message)
```

**Output:**

```text
You are debugging a syntax error
```

#### Common syntax-related errors

- `SyntaxError`: Invalid Python syntax.
- `IndentationError`: Incorrect indentation in the code.

**Debugging tip:** Read the error message carefully and inspect the indicated line and the lines immediately before it.

---

### 1.2 Logic Errors

A **logic error** occurs when code runs successfully but produces an unintended or incorrect result.

Logic errors generally do not generate error messages because the code is syntactically valid.

Common causes include:

- Using the wrong comparison operator.
- Assigning an incorrect value.
- Using an incorrect condition.
- Placing code inside the wrong conditional or loop block.

#### Example: Incorrect comparison operator

```python
login_attempts = 5

if login_attempts >= 5:
    print("User has not reached maximum number of login attempts.")
else:
    print("User has reached maximum number of login attempts.")
```

**Output:**

```text
User has not reached maximum number of login attempts.
```

The output is incorrect because the user has already reached five login attempts.

#### Corrected code

```python
login_attempts = 5

if login_attempts < 5:
    print("User has not reached maximum number of login attempts.")
else:
    print("User has reached maximum number of login attempts.")
```

**Output:**

```text
User has reached maximum number of login attempts.
```

**Debugging tip:** Check whether conditions, operators, variable values, and program flow match the intended behavior.

---

### 1.3 Exceptions

An **exception** occurs when Python encounters a problem while executing code, even though the code is syntactically correct.

Common exceptions include:

- `NameError`
- `IndexError`
- `TypeError`
- `FileNotFoundError`

#### A. NameError

A `NameError` occurs when Python encounters a name that has not been defined.

**Example:**

```python
username = "elarson"
month = "March"
total_logins = 75
failed_logins = 18

print("Login report for", username, "in", month)
print("Total logins:", total_logins)
print("Failed logins:", failed_logins)
print("Unusual logins:", unusual_logins)
```

The variable `unusual_logins` has not been defined.

**Output:**

```text
NameError: name 'unusual_logins' is not defined
```

**Corrected code:**

```python
username = "elarson"
month = "March"
total_logins = 75
failed_logins = 18
unusual_logins = 4

print("Login report for", username, "in", month)
print("Total logins:", total_logins)
print("Failed logins:", failed_logins)
print("Unusual logins:", unusual_logins)
```

#### B. IndexError

An `IndexError` occurs when you access a sequence using an index that does not exist.

Python list indices start at `0`.

**Example:**

```python
usernames = ["bmoreno", "tshah", "elarson"]

print(usernames[3])
```

The list contains three elements with indices `0`, `1`, and `2`.

**Output:**

```text
IndexError: list index out of range
```

**Corrected code:**

```python
usernames = ["bmoreno", "tshah", "elarson"]

print(usernames[2])
```

**Output:**

```text
elarson
```

#### C. TypeError

A `TypeError` occurs when an operation is applied to incompatible data types.

**Example:**

```python
age = 25
message = "Age: " + age

print(message)
```

Python cannot concatenate a string and an integer using the `+` operator in this example.

**Corrected code:**

```python
age = 25
message = "Age: " + str(age)

print(message)
```

**Output:**

```text
Age: 25
```

The `str()` function converts the integer into a string.

#### D. FileNotFoundError

A `FileNotFoundError` occurs when Python attempts to open a file that cannot be found at the specified location.

**Example:**

```python
with open("missing_file.txt", "r") as file:
    content = file.read()

print(content)
```

**Possible solutions:**

- Check the filename.
- Verify the file path.
- Confirm that the file exists.
- Check the current working directory.

---

## 2. Debugging Strategies

When a program contains multiple errors, Python generally reports the first error it encounters during execution.

After fixing that error, run the program again to identify additional problems.

Syntax error messages often help identify the source of a problem. Logic errors and some exceptions may require additional debugging techniques.

### 2.1 Use Debuggers

A **debugger** is a software tool that helps programmers locate errors and understand how their programs execute.

An **Integrated Development Environment (IDE)** is a software application that provides tools for writing, testing, and debugging code.

Examples of IDEs include:

- Visual Studio Code
- PyCharm
- Other Python-compatible development environments

#### Important debugger features

**Breakpoints**

Breakpoints are markers placed on executable lines of code. They pause program execution so you can inspect what is happening.

**Step-by-step execution**

Debuggers allow you to execute code one statement at a time.

**Variable inspection**

You can inspect variable values as the program executes. This is especially useful when a variable unexpectedly changes or a condition produces an incorrect result.

#### When to use a debugger

Use a debugger when:

- You cannot identify the source of an error.
- A variable contains an unexpected value.
- A loop behaves incorrectly.
- A conditional statement produces an unexpected result.
- You need to understand the execution flow.

### 2.2 Use AI-Powered Coding Assistants

AI-powered coding assistants can help programmers analyze code, identify possible errors, suggest corrections, and explain programming concepts.

For example, Gemini Code Assist integrates with development environments such as Visual Studio Code and JetBrains IDEs.

These tools can help with:

- Explaining error messages.
- Identifying potential bugs.
- Suggesting code modifications.
- Improving code readability.
- Answering technical questions.

However, AI-generated suggestions may be inaccurate, inefficient, or insecure.

**Best practice:** Always review, test, and validate AI-generated code before using it. AI tools should support your debugging process rather than replace your judgment.

### 2.3 Use Print Statements

Another effective debugging technique is to insert temporary `print()` statements at strategic locations in your program.

Print statements help you determine:

- Which parts of the code execute.
- Whether a loop runs the expected number of times.
- Whether a condition is satisfied.
- What values variables contain.
- Where unexpected behavior begins.

#### Example: Incorrect user approval logic

Suppose a program adds new users to an approved list but should not add users who are already present.

```python
new_users = ["sgilmore", "bmoreno"]
approved_users = ["bmoreno", "tshah", "elarson"]

def add_users():
    for user in new_users:
        if user in approved_users:
            print(user, "already in list")

        approved_users.append(user)

add_users()

print(approved_users)
```

**Output:**

```text
bmoreno already in list
['bmoreno', 'tshah', 'elarson', 'sgilmore', 'bmoreno']
```

The program prints a warning for `bmoreno`, but it still adds that username to the list.

This is a logic error because `approved_users.append(user)` executes regardless of whether the user is already present.

#### Add print statements to investigate

```python
new_users = ["sgilmore", "bmoreno"]
approved_users = ["bmoreno", "tshah", "elarson"]

def add_users():
    for user in new_users:
        print("Inside for loop")

        if user in approved_users:
            print("Inside if statement")
            print(user, "already in list")

        print("Before append method")
        approved_users.append(user)

add_users()

print(approved_users)
```

**What the output reveals:**

1. `Inside for loop` appears twice because the loop processes both usernames.
2. `Inside if statement` appears once because only `bmoreno` is already in the list when checked.
3. `Before append method` appears twice because the append operation executes for both usernames.

These messages help isolate the problem: the append operation is outside the `if` statement and executes even when a username already exists.

#### Corrected code using an else statement

```python
new_users = ["sgilmore", "bmoreno"]
approved_users = ["bmoreno", "tshah", "elarson"]

def add_users():
    for user in new_users:
        if user in approved_users:
            print(user, "already in list")
        else:
            approved_users.append(user)

add_users()

print(approved_users)
```

**Output:**

```text
bmoreno already in list
['bmoreno', 'tshah', 'elarson', 'sgilmore']
```

Now, a username is added only when it is not already present in the approved list.

**Debugging tip:** Remove temporary debugging print statements when they are no longer needed, or replace them with appropriate logging in larger applications.

---

## 3. Comparison of Python Errors

| Error type | Description | Example |
|---|---|---|
| `SyntaxError` | Invalid Python syntax | Missing quotation mark |
| `IndentationError` | Incorrect indentation | Misaligned code block |
| Logic error | Code produces an unintended result | Incorrect comparison operator |
| `NameError` | Undefined name | Using an unassigned variable |
| `IndexError` | Invalid sequence index | Accessing `usernames[3]` in a three-element list |
| `TypeError` | Incompatible data types or operations | Adding a string to an integer |
| `FileNotFoundError` | File cannot be found | Opening a nonexistent file |

**Important distinction:** Logic errors usually do not produce exceptions. The program runs, but its result is incorrect.

---

## 4. A Practical Debugging Workflow

Follow these steps when debugging Python code:

1. **Run the program.** Observe the output and any error messages.
2. **Identify the error type.** Determine whether it is a syntax error, logic error, or exception.
3. **Read the error message.** Check the line number, error description, and relevant variables.
4. **Inspect the code.** Review the affected line and surrounding statements.
5. **Use debugging tools.** Insert print statements or set breakpoints when necessary.
6. **Check variable values.** Verify that values and data types match your expectations.
7. **Correct the problem.** Make a targeted change to the code.
8. **Run the program again.** Confirm that the error is resolved.
9. **Test different cases.** Ensure the correction works for expected and unexpected inputs.
10. **Remove temporary debugging statements.** Keep the final code clean.

---

## 5. Key Takeaways

- **Syntax errors** occur when code violates Python's syntax rules.
- **Logic errors** occur when code runs but produces unintended results.
- **Exceptions** occur when a problem prevents a statement from executing successfully.
- Python error messages often help identify syntax errors and exceptions.
- Debuggers help inspect program execution using breakpoints, step-by-step execution, and variable inspection.
- Print statements help identify which parts of the code execute and reveal unexpected variable values.
- AI coding assistants can support debugging, but their suggestions must be reviewed and tested.
- Fixing one error may reveal another, so rerunning the program after each correction is important.
- Testing multiple scenarios helps ensure that a fix works correctly.

---

## Conclusion

Debugging is an essential part of Python programming. By understanding syntax errors, logic errors, and exceptions, programmers can diagnose problems more effectively.

Using error messages, debuggers, print statements, and carefully validated AI assistance makes it easier to locate errors, correct mistakes, and develop reliable code.