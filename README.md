# Bash-Script-for-Generating-a-Multiplication-Table

## Introduction
Bash (Bourne Again Shell) is a Unix shell and command language widely used for automating tasks, managing system processes, and interacting with the operating system. It is a powerful tool for developers and system administrators, allowing them to write scripts to streamline repetitive tasks, manage files, and execute commands efficiently. Bash scripts are especially valuable for handling tasks like file processing, system monitoring, and automation in Linux environments.

One practical example of using Bash scripting is creating a script to generate a multiplication table. This is a simple yet effective way to practice scripting skills and automate calculations. The script takes an input number and generates its multiplication table up to a specified range. It’s useful for quick calculations, educational purposes, or as a foundational project to understand Bash concepts like loops, user input, and formatted output.

## Project Objectives
- Automate multiplication table generation.
- Enhance understanding of Bash scripting concepts.
- Provide a practical and educational tool for calculations.

## Project Requirements
- **User Input for Number:** The script must first ask the user to input a number for which the multiplication table will be generated.
- **Choice of Table Range:** Next, ask the user if they want a full multiplication table (1 to 10) or a partial table. If they choose partial, prompt them for the start and end of the range.
- **Use of Loops:** Implement the logic to generate the multiplication table using loops. You may use either the list form or C-style `for` loop based on what's appropriate.
- **Conditional Logic:** Use `if-else` statements to handle the logic based on the user's choices (full vs. partial table and valid range input).
- **Input Validation:** Ensure that the user enters valid numbers for the multiplication table and the specified range. Provide feedback for invalid inputs and default to a full table if the range is incorrect.
- **Readable Output:** Display the multiplication table in a clear and readable format, adhering to the user's choice of range.
- **Comments and Code Quality:** Your script should be well-commented, explaining the purpose of different sections and any important variables or logic used.

## Definition of Some Bash Scripting Terms

### Shebang (`#!`)
The first line in a script that specifies the interpreter to execute the script. It ensures the script is run using the correct shell or interpreter.
```bash
#!/bin/bash
```

### Variables
Containers to store data or values. Makes scripts more flexible and reusable.
```bash
name="Alice"
echo "Hello, $name"
```

### Conditional Statements (`if`, `else`, `elif`)
Used to execute code based on conditions. Adds decision-making capabilities to scripts.
```bash
if [ $age -ge 18 ]; then
  echo "Adult"
else
  echo "Minor"
fi
```

### Loops (`for`, `while`)
Used to repeat tasks. Automates repetitive tasks efficiently.
```bash
for i in {1..5}; do
  echo "Iteration $i"
done
```

## Project Steps

### 1. Create a File Named `multiplication_table.sh`
```bash
touch multiplication_table.sh
```

### 2. Use a Text Editor to Update the Script
```bash
vi multiplication_table.sh
```

### 3. Copy and Paste the Below Script
```bash
#!/bin/bash

# Function to generate and display the multiplication table
generate_table() {
    local number=$1
    local start=$2
    local end=$3

    echo "Multiplication Table for $number (from $start to $end):"
    for ((i=start; i<=end; i++)); do
        echo "$number x $i = $((number * i))"
    done
}

# Function to validate if the input is a valid integer
validate_number() {
    if ! [[ $1 =~ ^-?[0-9]+$ ]]; then
        echo "Invalid input. Please enter a valid integer."
        return 1
    fi
    return 0
}

# Prompt the user for the number
read -p "Enter the number for which you want the multiplication table: " number
validate_number "$number" || exit 1

# Ask the user for the table range
echo "Do you want a full table (1 to 10) or a partial table?"
echo "Enter 'full' for the full table or 'partial' for a specific range."
read -p "Your choice (full/partial): " choice

if [[ "$choice" == "partial" ]]; then
    # Get the range from the user
    read -p "Enter the start of the range: " start
    validate_number "$start" || exit 1

    read -p "Enter the end of the range: " end
    validate_number "$end" || exit 1

    # Ensure start is less than or equal to end
    if ((start > end)); then
        echo "Invalid range. Defaulting to full table (1 to 10)."
        start=1
        end=10
    fi
else
    # Default to full table if the choice is not 'partial'
    start=1
    end=10
fi

# Generate the multiplication table
generate_table "$number" "$start" "$end"
```

### 4. Make the Script Executable
```bash
chmod +x multiplication_table.sh
```

### 5. Run the Script
```bash
./multiplication_table.sh
```

## Key Features
- **User Input for Number:** Prompts the user to input the base number for the table.
- **Choice of Table Range:** Offers a choice between a full table or a custom range.
- **Input Validation:** Ensures the inputs are valid integers and provides feedback for invalid entries.
- **Loop Logic:** Uses a loop to generate the table within the specified range.
- **Conditional Logic:** Handles different cases (full vs. partial table) and validates the range.
- **Readable Output:** Clearly displays the table with formatted results.

## Conclusion
The Multiplication Table Generator project demonstrates the effective use of Bash scripting to create an interactive and user-friendly utility. By incorporating user input, conditional logic, loops, and input validation, the script provides flexibility and ensures robustness in handling various scenarios.

Key features like the ability to choose between a full table or a custom range and clear, formatted output enhance the usability of the tool. The implementation showcases the power of Bash for creating lightweight yet functional scripts suitable for quick automation tasks.

This project serves as an excellent example of how scripting can solve everyday problems efficiently, offering a strong foundation for further enhancements such as adding support for advanced formatting or exporting results to a file. It also highlights the importance of good coding practices, including clear commenting and input validation, to ensure maintainability and user satisfaction.

