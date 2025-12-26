# Week 2: Student Grade Calculator 🎓

## Project Overview

This project is a comprehensive student grade calculator that demonstrates decision-making, loops, and functions in Python. The program takes student marks as input, validates the data, calculates the appropriate grade, and displays encouraging messages based on performance.

**Learning Objectives:**
- Master if-elif-else conditional statements
- Implement while loops for input validation
- Use for loops for processing multiple items
- Create reusable functions with parameters and return values
- Handle errors and invalid inputs gracefully
- Build user-friendly interactive programs

---

## Setup Instructions

### Using Google Colab (Recommended for Beginners)
1. Go to [Google Colab](https://colab.research.google.com/)
2. Click "New Notebook"
3. Copy and paste the code from `grade_calculator.py`
4. Click the "Play" button or press `Shift + Enter` to run
5. Interact with the menu by entering your choices

### Alternative: Local Installation
If you prefer to run locally:
1. Install Python 3.8 or higher from [python.org](https://www.python.org/downloads/)
2. Open terminal/command prompt
3. Navigate to project folder
4. Run: `python grade_calculator.py`

---


## Features

### 1. **Main Menu System**
Interactive menu with 4 options:
- Calculate grade for one student
- Calculate grades for multiple students
- View grading system
- Exit program

### 2. **Single Student Grading**
- Takes student name and marks as input
- Validates marks are between 0-100
- Calculates grade based on marks
- Displays result with encouraging message

### 3. **Multiple Student Grading**
- Processes batch of students using for loop
- Stores all results
- Displays comprehensive summary
- Shows individual grades and messages

### 4. **Input Validation**
- Ensures marks are numeric and within valid range (0-100)
- Validates student name is not empty
- Uses while loop to repeat until valid input
- Provides clear error messages

### 5. **Grading System Display**
- Shows complete grading criteria
- Helps users understand grade boundaries

---

## Grading Logic

The program uses the following grading system:

| Grade | Marks Range | Message |
|-------|-------------|---------|
| A | 90-100 | Outstanding! Excellent work! 🌟 |
| B | 80-89 | Very Good! Keep it up! 👍 |
| C | 70-79 | Good! You're doing well! 😊 |
| D | 60-69 | Satisfactory! There's room for improvement! 💪 |
| F | 0-59 | Keep trying! Don't give up! 🎯 |

---

## How It Works

### Program Flow

```
Start Program
    ↓
Display Main Menu
    ↓
User Selects Option
    ↓
┌─────────────────────────────────┐
│ Option 1: Single Student        │
│   - Get name (validate)         │
│   - Get marks (validate)        │
│   - Calculate grade             │
│   - Display result              │
└─────────────────────────────────┘
┌─────────────────────────────────┐
│ Option 2: Multiple Students     │
│   - Get number of students      │
│   - FOR each student:           │
│       - Get name (validate)     │
│       - Get marks (validate)    │
│       - Calculate grade         │
│       - Store result            │
│   - Display all results         │
└─────────────────────────────────┘
┌─────────────────────────────────┐
│ Option 3: View Grading System   │
│   - Display grade ranges        │
└─────────────────────────────────┘
┌─────────────────────────────────┐
│ Option 4: Exit                  │
│   - Display goodbye message     │
│   - End program                 │
└─────────────────────────────────┘
```

### Key Functions

#### 1. `get_grade(marks)`
```python
def get_grade(marks):
    if marks >= 90 and marks <= 100:
        return "A", "Outstanding! Excellent work! 🌟"
    elif marks >= 80 and marks < 90:
        return "B", "Very Good! Keep it up! 👍"
    # ... more conditions
```
- **Purpose**: Determines grade based on marks
- **Parameters**: marks (float/int)
- **Returns**: tuple (grade, message)
- **Logic**: Uses if-elif-else chain to check mark ranges

#### 2. `validate_marks(marks_str)`
```python
def validate_marks(marks_str):
    try:
        marks = float(marks_str)
        if marks >= 0 and marks <= 100:
            return True, marks
        else:
            return False, None
    except ValueError:
        return False, None
```
- **Purpose**: Validates user input for marks
- **Parameters**: marks_str (string)
- **Returns**: tuple (is_valid, marks_value)
- **Features**: 
  - Handles non-numeric input with try-except
  - Checks if marks are in valid range (0-100)
  - Returns validation status and converted value

#### 3. `calculate_grade()`
```python
def calculate_grade():
    # Get student name
    name = input("Enter student name: ").strip()
    
    # Validate name using while loop
    while name == "":
        print("Name cannot be empty!")
        name = input("Enter student name: ").strip()
    
    # Get marks with validation
    marks = None
    while marks is None:
        marks_input = input("Enter marks (0-100): ")
        is_valid, marks_value = validate_marks(marks_input)
        if is_valid:
            marks = marks_value
        else:
            print("Invalid input!")
```
- **Purpose**: Main function for single student grading
- **Features**: 
  - Uses while loop for input validation
  - Repeats until valid input received
  - Calls helper functions for grade calculation

#### 4. `calculate_multiple_students()`
```python
def calculate_multiple_students():
    # Get number of students
    num_students = int(input("How many students? "))
    
    # Process each student using for loop
    for i in range(num_students):
        # Get name and marks (with validation)
        # Calculate grade
        # Store in results list
    
    # Display all results
    for result in results:
        print(result)
```
- **Purpose**: Process multiple students in batch
- **Features**: 
  - Uses for loop to iterate through students
  - Stores results in list
  - Displays summary at the end

---

## Sample Output

### Example 1: Single Student

```
============================================================
🎓 STUDENT GRADE CALCULATOR - MAIN MENU
============================================================
1. Calculate grade for one student
2. Calculate grades for multiple students
3. View grading system
4. Exit
============================================================

Enter your choice (1-4): 1

============================================================
🎓 STUDENT GRADE CALCULATOR 🎓
============================================================

Enter student name: Priya
Enter marks for Priya (0-100): 85

============================================================
📊 RESULT FOR PRIYA
============================================================
Student Name: Priya
Marks: 85/100
Grade: B
Message: Very Good! Keep it up! 👍
============================================================
```

### Example 2: Input Validation

```
Enter student name: Rahul
Enter marks for Rahul (0-100): 150
❌ Invalid input! Please enter a number between 0 and 100.
Enter marks for Rahul (0-100): -5
❌ Invalid input! Please enter a number between 0 and 100.
Enter marks for Rahul (0-100): abc
❌ Invalid input! Please enter a number between 0 and 100.
Enter marks for Rahul (0-100): 92

============================================================
📊 RESULT FOR RAHUL
============================================================
Student Name: Rahul
Marks: 92/100
Grade: A
Message: Outstanding! Excellent work! 🌟
============================================================
```

### Example 3: Multiple Students

```
Enter your choice (1-4): 2

============================================================
🎓 STUDENT GRADE CALCULATOR 🎓
============================================================
📚 Multiple Student Grade Calculator
============================================================

How many students do you want to grade? 3

--- Student 1 of 3 ---
Enter student name: Aisha
Enter marks for Aisha (0-100): 95

--- Student 2 of 3 ---
Enter student name: Rohan
Enter marks for Rohan (0-100): 78

--- Student 3 of 3 ---
Enter student name: Kavya
Enter marks for Kavya (0-100): 55

============================================================
📊 RESULTS SUMMARY
============================================================

1. Aisha
   Marks: 95/100
   Grade: A
   Outstanding! Excellent work! 🌟

2. Rohan
   Marks: 78/100
   Grade: C
   Good! You're doing well! 😊

3. Kavya
   Marks: 55/100
   Grade: F
   Keep trying! Don't give up! 🎯
============================================================
```

---

## Technical Details

### Concepts Demonstrated

#### 1. **Conditional Statements (if-elif-else)**
```python
if marks >= 90:
    grade = "A"
elif marks >= 80:
    grade = "B"
elif marks >= 70:
    grade = "C"
else:
    grade = "F"
```
- Used to implement grading logic
- Checks conditions in order from highest to lowest
- Provides different outputs based on mark ranges

#### 2. **While Loops**
```python
while marks is None:
    # Get input
    # Validate
    # If valid, assign to marks
    # Otherwise, loop continues
```
- Used for input validation
- Repeats until valid input received
- Prevents program from proceeding with invalid data

#### 3. **For Loops**
```python
for i in range(num_students):
    # Process each student
```
- Used to process multiple students
- Iterates a specific number of times
- Useful for batch processing

#### 4. **Functions**
- **Purpose**: Create reusable code blocks
- **Benefits**: 
  - Code organization
  - Easier testing
  - Reduces repetition
  - Improves readability

#### 5. **Error Handling (try-except)**
```python
try:
    marks = float(marks_str)
except ValueError:
    return False, None
```
- Catches errors when converting string to number
- Prevents program crash on invalid input
- Provides graceful error handling

#### 6. **Comparison Operators**
- `>=` (greater than or equal to)
- `<=` (less than or equal to)
- `<` (less than)
- `>` (greater than)
- `==` (equal to)

#### 7. **Logical Operators**
- `and`: Both conditions must be true
- Example: `marks >= 90 and marks <= 100`

---

## Testing Evidence

The project includes comprehensive testing with 20 test cases covering:

### Functional Tests
- ✅ All grade ranges (A, B, C, D, F)
- ✅ Boundary values (0, 59, 60, 79, 80, 89, 90, 100)
- ✅ Decimal marks (87.5, 92.3)

### Validation Tests
- ✅ Marks above 100
- ✅ Negative marks
- ✅ Non-numeric input
- ✅ Empty name input

### Integration Tests
- ✅ Multiple student processing
- ✅ Menu navigation
- ✅ Complete workflow from input to output

### Edge Cases
- ✅ Special characters in names
- ✅ Very long names
- ✅ Invalid menu choices

**Success Rate: 100% (20/20 tests passed)**

See `test_cases.txt` for detailed test results.

---

## What I Learned

Through this project, I learned:

### 1. **Decision Making with If-Elif-Else**
- How to create branching logic in programs
- Importance of condition order in elif chains
- Using comparison operators effectively

### 2. **Loop Control Structures**
- **While loops**: Perfect for input validation and repeating until condition met
- **For loops**: Ideal for processing known number of items
- When to use each type of loop

### 3. **Function Design**
- Breaking complex programs into smaller functions
- Using parameters and return values
- Creating reusable code components
- Importance of clear function names

### 4. **Input Validation**
- Never trust user input
- Always validate data before processing
- Provide clear error messages
- Use loops to allow users to correct mistakes

### 5. **Error Handling**
- Using try-except to catch errors
- Preventing program crashes
- Providing user-friendly error messages

### 6. **Code Organization**
- Structuring programs with main() function
- Using helper functions for specific tasks
- Keeping functions focused on single responsibility

### Challenges Faced:
- Understanding the flow of nested loops and conditions
- Implementing proper input validation for all cases
- Managing program state across multiple functions
- Deciding when to use while vs for loops

### Key Takeaways:
- Planning program logic on paper before coding helps immensely
- Testing with various inputs reveals bugs early
- Functions make code much easier to understand and modify
- Good error messages improve user experience significantly
- Breaking problems into smaller functions simplifies complex logic

---

## Quality Standards Checklist

- ✅ **Project Overview**: Clear description with learning objectives
- ✅ **Setup Instructions**: Detailed guide for Google Colab and local setup
- ✅ **Code Structure**: Well-organized with clear file hierarchy
- ✅ **Visual Documentation**: Screenshots folder with program functionality
- ✅ **Technical Details**: Comprehensive explanation of all concepts used
- ✅ **Testing Evidence**: 20 test cases with 100% pass rate
- ✅ **Learning Reflection**: Detailed explanation of concepts learned
- ✅ **Code Comments**: Every function and complex logic documented
- ✅ **Error Handling**: All edge cases handled gracefully
- ✅ **User Experience**: Clear prompts, helpful messages, professional formatting

---

## Resources Used

- [Python Official Documentation - Control Flow](https://docs.python.org/3/tutorial/controlflow.html)
- [Python If-Else Statements Tutorial](https://www.w3schools.com/python/python_conditions.asp)
- [Python Loops Tutorial](https://www.w3schools.com/python/python_while_loops.asp)
- [Python Functions Guide](https://realpython.com/defining-your-own-python-function/)
- YouTube: "Python for Beginners - If Else Statements"
- Stack Overflow for troubleshooting validation logic

---

## Future Enhancements

Possible improvements for this project:
- Save grades to a file for record keeping
- Calculate class average and statistics
- Add subject-wise grading
- Generate report cards
- Add grade improvement suggestions
- Implement attendance tracking
- Create graphical visualization of grades
- Add teacher login system
- Send grade notifications via email

---

## Bonus Features Included

Beyond the basic requirements, this project includes:
- 📊 Menu-driven interface for better user experience
- 🎯 Batch processing for multiple students
- ✅ Comprehensive input validation
- 📝 Detailed test cases documentation
- 🎨 Professional formatting with emojis
- 💡 Helpful error messages
- 🔄 Ability to view grading system anytime
- 📈 Results summary for multiple students

---

## Contact & Feedback

If you have questions or suggestions about this project, feel free to reach out!

**Author:**  **Sri Venkata Satyanarayana Gattu**  <br>
**Course:**  Python Basics - Week 2  <br>
**Date:**  December 26, 2025

---

**Note:** This project was completed as part of the Week 2 assignment demonstrating decision-making, loops, and functions in Python. All requirements have been met and exceeded with additional features and comprehensive documentation.
