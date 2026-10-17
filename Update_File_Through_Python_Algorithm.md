
# Update a File Through a Python Algorithm

## 1. Project Description

This project demonstrates how Python can be used to update an access control list by removing IP addresses that are no longer authorized to access restricted resources. In this scenario, a healthcare organization maintains an `allow_list.txt` file containing the IP addresses of employees who can access a restricted subnetwork containing personal patient records. A separate `remove_list` contains IP addresses that must be removed from the allow list. The Python algorithm reads the file, converts its contents into a list, removes unauthorized IP addresses, and writes the updated information back to the file. This automation improves the consistency and efficiency of access management and supports the protection of sensitive healthcare information.

## 2. Open the File That Contains the Allow List

### Python Code

```python
import_file = "allow_list.txt"

with open(import_file, "r") as file:
    # File is opened for reading
    pass
```

### Explanation

- **`import_file`**: A variable that stores the name of the file to be opened.
- **`"allow_list.txt"`**: The file containing the authorized IP addresses.
- **`with`**: A keyword used to manage the file resource. It automatically closes the file when the block finishes.
- **`open()`**: A built-in Python function used to open a file.
- **`"r"`**: The file mode indicating that the file is opened for reading.
- **`as file`**: Assigns the opened file object to the variable `file`.
- **Indentation**: Defines the statements that belong to the `with` block.

The `pass` statement is included here only to illustrate the opening step in isolation. It is not required in the complete algorithm.

## 3. Read the File Contents

### Python Code

```python
with open(import_file, "r") as file:
    ip_addresses = file.read()
```

### Explanation

- **`file.read()`**: Reads the contents of the opened file and returns them as a string.
- **`ip_addresses`**: Stores the file contents as a string.
- **`with open()`**: Opens the file and manages its lifecycle.

At this stage, the IP addresses are stored in a single string, with newline characters separating individual entries.

## 4. Convert the String into a List

### Python Code

```python
ip_addresses = ip_addresses.split()
```

### Explanation

- **`.split()`**: A string method that separates a string into a list of substrings.
- **`ip_addresses`**: The variable is reassigned to hold the resulting list.
- **Default whitespace splitting**: Calling `.split()` without an argument separates the string at whitespace, including spaces, tabs, and newline characters.

For example:

```python
ip_addresses = "192.168.1.1\n192.168.1.2\n192.168.1.3"

ip_addresses = ip_addresses.split()

print(ip_addresses)
```

Output:

```text
['192.168.1.1', '192.168.1.2', '192.168.1.3']
```

Converting the string into a list makes it possible to remove individual IP addresses.

## 5. Iterate Through the Remove List

### Python Code

```python
remove_list = ["192.168.1.2", "192.168.1.3"]

for element in remove_list:
    # Check and remove matching IP addresses
    pass
```

### Explanation

- **`remove_list`**: A list containing the IP addresses that must be removed from the allow list.
- **`for`**: A keyword that begins a loop.
- **`element`**: The loop variable that stores the current IP address being processed.
- **`in`**: Specifies the collection through which the loop iterates.
- **Colon (`:`)**: Marks the beginning of the loop body.
- **Indentation**: Identifies the statements executed during each iteration.

The loop processes each IP address in `remove_list` individually.

The `pass` statement is only a placeholder in this isolated example. The next section provides the actual removal logic.

## 6. Remove IP Addresses That Are on the Remove List

### Python Code

```python
for element in remove_list:
    if element in ip_addresses:
        ip_addresses.remove(element)
```

### Explanation

- **`for element in remove_list`**: Iterates through every IP address that needs to be removed.
- **`if`**: Begins a conditional statement.
- **`element in ip_addresses`**: Checks whether the current IP address exists in the allow list.
- **`.remove(element)`**: Removes the matching IP address from the `ip_addresses` list.
- **Indentation**: Ensures that the removal occurs only when the condition is true.

The conditional prevents Python from raising a `ValueError` when an IP address in `remove_list` is not present in `ip_addresses`.

**Why is `.remove()` appropriate here?**

Applying `.remove()` in this way is appropriate because the allow list contains no duplicate IP addresses. Each authorized IP address therefore appears at most once, so one removal is sufficient to eliminate a matching entry.

## 7. Update the File with the Revised List of IP Addresses

### Python Code

```python
ip_addresses = "\n".join(ip_addresses)

with open(import_file, "w") as file:
    file.write(ip_addresses)
```

### Explanation

- **`"\n"`**: Represents a newline character.
- **`.join(ip_addresses)`**: Combines the list elements into a single string, placing a newline between each IP address.
- **`"w"`**: Opens the file in write mode. If the file already exists, its previous contents are overwritten.
- **`file.write(ip_addresses)`**: Writes the updated string to the file.
- **`with`**: Ensures that the file is properly closed after writing.

The updated file now contains only the IP addresses that remain authorized.

**Important:** Write mode overwrites the existing file. The algorithm should therefore be tested with sample data and appropriate backups before being used on production access control files.

## 8. Complete Python Algorithm

The following code combines all the steps into one algorithm.

```python
# Step 1: Specify the file containing the allow list
import_file = "allow_list.txt"

# Step 2: Read the contents of the file
with open(import_file, "r") as file:
    ip_addresses = file.read()

# Step 3: Convert the string into a list
ip_addresses = ip_addresses.split()

# Step 4: Define the IP addresses that must be removed
remove_list = ["192.168.1.2", "192.168.1.3"]

# Step 5: Remove IP addresses that appear in the remove list
for element in remove_list:
    if element in ip_addresses:
        ip_addresses.remove(element)

# Step 6: Convert the updated list into a string
ip_addresses = "\n".join(ip_addresses)

# Step 7: Write the updated list back to the file
with open(import_file, "w") as file:
    file.write(ip_addresses)

print("The allow list has been updated successfully.")
```

### Example Input

Contents of `allow_list.txt`:

```text
192.168.1.1
192.168.1.2
192.168.1.3
192.168.1.4
```

### Remove List

```python
remove_list = ["192.168.1.2", "192.168.1.3"]
```

### Expected Output

Updated contents of `allow_list.txt`:

```text
192.168.1.1
192.168.1.4
```

The IP addresses `192.168.1.2` and `192.168.1.3` have been removed because they appear in `remove_list`.

## 9. Summary

This project demonstrates how Python can automate the process of updating a file containing authorized IP addresses. The algorithm uses the `open()` function and `with` statement to open and manage the file safely. It uses the `.read()` method to retrieve the file contents and `.split()` to convert the string into a list. A `for` loop iterates through the removal list, while an `if` statement and the `.remove()` method eliminate IP addresses that are no longer authorized. Finally, the `.join()` method converts the revised list back into a string, and `.write()` saves the updated information to the file. This approach demonstrates practical file handling, iteration, conditional logic, and automation skills relevant to cybersecurity.

## 10. Self-Assessment Checklist

Use this checklist to review the completed portfolio activity. Answer each question honestly.

| No. | Assessment Statement | Yes/No |
|---:|---|---|
| 1 | Did I include a project description at the beginning? | |
| 2 | Did I explain how the `open()` function and `with` statement are used? | |
| 3 | Did I explain how the `.read()` method retrieves the file contents? | |
| 4 | Did I explain how the `.split()` method converts a string into a list? | |
| 5 | Did I explain how the `for` loop iterates through `remove_list`? | |
| 6 | Did I explain how the conditional statement and `.remove()` method remove matching IP addresses? | |
| 7 | Did I explain why `.remove()` is appropriate when there are no duplicate IP addresses? | |
| 8 | Did I explain how `.join()` and `.write()` update the file? | |
| 9 | Did I include a summary and screenshots or typed versions of the Python code? | |

**Total possible score:** 9 points

**Recommended passing score:** At least 8 out of 9 points (approximately 89%).

## 11. Evidence for Your Cybersecurity Portfolio

To strengthen this project for prospective employers, include:

1. Screenshots of the relevant code from Tasks 2–7 of the lab, or the corresponding typed code.
2. Explanations of the Python syntax, methods, and keywords used.
3. An example of the original `allow_list.txt` file.
4. An example of the `remove_list` and the updated allow list.
5. The completed project description, summary, and self-assessment.

**Security note:** The IP addresses in this example are illustrative. In a real healthcare environment, access control changes should follow organizational authorization procedures, be logged for auditing, and be tested before deployment.
