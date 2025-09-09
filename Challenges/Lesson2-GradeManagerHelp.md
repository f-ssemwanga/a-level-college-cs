# Grade Management System - Hints & Guidance

**Use this notebook only if you're stuck!** Try the main challenge first.

This notebook provides hints and examples for different data structure approaches.

---

## Data Structure Options

### Option 1: Dictionary Approach
**Good for:** Fast lookups by student ID, flexible structure

```python
# Example structure:
students = {
    "S001": {
        "name": "Alice Johnson",
        "grades": [
            {"subject": "Math", "grade": 85},
            {"subject": "Physics", "grade": 92}
        ]
    }
}
```

### Option 2: List of Lists (2D Array)
**Good for:** Simple structure, easy to iterate

```python
# Example structure:
# [student_id, name, [grades...]]
students = [
    ["S001", "Alice Johnson", [85, 92, 88]],
    ["S002", "Bob Smith", [78, 82, 95]]
]

# Or with subject tracking:
subjects = ["Math", "Physics", "CompSci"]
students = [
    ["S001", "Alice Johnson", [85, 92, 88]],
    ["S002", "Bob Smith", [78, 82, 95]]
]
```

### Option 3: Mixed Approach
**Good for:** Combining benefits of both

```python
# Example structure:
students = [
    {"id": "S001", "name": "Alice Johnson", "grades": [85, 92, 88]},
    {"id": "S002", "name": "Bob Smith", "grades": [78, 82, 95]}
]
```

---

## Function Hints

### Add Student Function Hint
```python
def add_student(students, name, student_id):
    # Check if student already exists
    # If using dictionary:
    if student_id in students:
        return False, "Student already exists"
    
    # If using list, you'll need to search:
    # for student in students:
    #     if student[0] == student_id:  # assuming ID is first element
    #         return False, "Student already exists"
    
    # Add the student to your data structure
    # Return success message
    return True, "Student added successfully"
```

### Finding Students Hint
```python
# For dictionary approach:
def find_student(students, student_id):
    return students.get(student_id, None)

# For list approach:
def find_student(students, student_id):
    for student in students:
        if student[0] == student_id:  # assuming ID is first element
            return student
    return None
```

### Average Calculation Hint
```python
def calculate_average(grades):
    if not grades:  # Empty list check
        return 0
    
    # If grades is a list of numbers:
    return sum(grades) / len(grades)
    
    # If grades is a list of dictionaries:
    # total = sum(grade['grade'] for grade in grades)
    # return total / len(grades)
```

### Letter Grade Conversion Hint
```python
def get_letter_grade(average):
    if average >= 90:
        return 'A*'
    elif average >= 80:
        return 'A'
    # Continue the pattern...
    else:
        return 'U'
```

---

## Common Challenges & Solutions

### Challenge: "How do I check if a student exists?"
**Dictionary approach:** Use `student_id in students`
**List approach:** Loop through and check ID field

### Challenge: "How do I handle empty grade lists?"
**Solution:** Always check `if not grades:` before calculating averages

### Challenge: "How do I format the output nicely?"
**Solution:** Use f-strings and `\n` for line breaks:
```python
report = f"Name: {student_name}\n"
report += f"Average: {average}%\n"
```

### Challenge: "How do I validate grade ranges?"
**Solution:** Use conditions:
```python
if not (0 <= grade <= 100):
    return False, "Grade must be between 0 and 100"
```

---

## Testing Examples

### Sample Test Data
Use this data to test your functions:

**Students:**
- Alice Johnson (S001): Math=85, Physics=92, CompSci=88
- Bob Smith (S002): Math=78, Physics=82, CompSci=95
- Carol Wilson (S003): Math=91, Physics=87, CompSci=89

**Expected Results:**
- Alice average: 88.33, Grade: A
- Bob average: 85.0, Grade: A
- Carol average: 89.0, Grade: A
- Class average: 87.44

---

## Debugging Tips

### Print Your Data Structure
Add these lines to see what your data looks like:
```python
print("Current students data:")
print(students)
```

### Test One Function at a Time
Don't try to write everything at once. Test each function before moving to the next.

### Use Simple Test Cases First
Start with one student and one grade, then expand.

### Check Your Return Values
Make sure your functions return what other functions expect.

### Common Error Messages and Solutions
- **"KeyError"** - You're trying to access a dictionary key that doesn't exist
- **"IndexError"** - You're trying to access a list index that's out of range
- **"TypeError"** - You're mixing up data types (like trying to add a string to a number)
- **"NameError"** - You're using a variable that hasn't been defined

### When to Use Each Data Structure

**Use Dictionary when:**
- You need to look up students by ID frequently
- You want flexible data storage
- You prefer readable, self-documenting code

**Use Lists when:**
- You want simple, straightforward data storage
- You need to iterate through all students often
- You're more comfortable with list operations

**Use 2D Arrays when:**
- You need consistent data structure
- You want to treat data like a table
- Memory efficiency is important