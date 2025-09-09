# Student Grade Management System Challenge

## Your Mission
Build a comprehensive grade management system that demonstrates your understanding of functions, parameters, and data structures. You can choose to implement this using **dictionaries**, **lists**, or **2D arrays** - the choice is yours!

---

## Learning Goals
- Design and implement functions with parameters
- Choose appropriate data structures for the problem
- Handle data validation and error checking
- Practice problem decomposition

---

## Challenge Overview

You will build a system that can:
- Store student information and grades
- Add new students and grades
- Calculate averages and letter grades
- Generate individual student reports
- Provide class-wide statistics

---

## Core Requirements

### Challenge 1: Student Storage System
**Create a data structure to store:**
- Student name and unique ID
- Multiple subject grades for each student
- Choose your approach: dictionaries, lists, or 2D arrays

### Challenge 2: Add Student Function
**Write a function:**
- Function name: `add_student`
- Parameters: student database, student name, student ID
- Should check if student ID already exists
- Should return success/failure status and a message

### Challenge 3: Add Grade Function
**Write a function:**
- Function name: `add_grade`
- Parameters: student database, student ID, subject name, grade value
- Should validate that the student exists
- Should validate that the grade is between 0-100
- Should return success/failure status and a message

### Challenge 4: Calculate Statistics
**Write these functions:**
1. `calculate_average(student_data)` - Calculate average grade for one student
2. `get_letter_grade(average)` - Convert numerical average to letter grade

**Grade Boundaries:**
- A*: 90+, A: 80-89, B: 70-79, C: 60-69, D: 50-59, E: 40-49, U: Below 40

### Challenge 5: Student Report Generator
**Write a function:**
- Function name: `generate_report`
- Parameters: students (your data structure), student ID
- Should display: student name, ID, all grades, average, letter grade
- Should handle case where student doesn't exist

**Example Output:**
```
=== STUDENT REPORT ===
Name: Alice Johnson
ID: S001
Average Grade: 88.3%
Letter Grade: A

Individual Grades:
  Mathematics: 85%
  Physics: 92%
  Computer Science: 88%
```

### Challenge 6: Class Overview
**Write a function:**
- Function name: `class_statistics`
- Parameters: students (your data structure)
- Should calculate and display:
  - Total number of students
  - Class average grade
  - Highest individual average
  - Lowest individual average
  - Number of students in each letter grade category

---

## Implementation Choices

### Option 1: Dictionary Approach
```python
# Example structure:
students = {
    "S001": {
        "name": "Alice Johnson",
        "grades": [85, 92, 88]  # or use subject:grade pairs
    }
}
```

### Option 2: List Approach
```python
# Example structure:
students = [
    ["S001", "Alice Johnson", [85, 92, 88]],
    ["S002", "Bob Smith", [78, 82, 95]]
]
```

### Option 3: 2D Array with Parallel Lists
```python
# Example structure:
student_ids = ["S001", "S002", "S003"]
student_names = ["Alice Johnson", "Bob Smith", "Carol Wilson"]
student_grades = [[85, 92, 88], [78, 82, 95], [91, 87, 89]]
```

---

## Testing Your System

### Test Data
Use these students to test your functions:
- Alice Johnson (S001): Math=85, Physics=92, CompSci=88
- Bob Smith (S002): Math=78, Physics=82, CompSci=95
- Carol Wilson (S003): Math=91, Physics=87, CompSci=89

### Expected Results
- Alice average: 88.33, Grade: A
- Bob average: 85.0, Grade: A  
- Carol average: 89.0, Grade: A
- Class average: 87.44

### Test Cases to Include
1. Adding students successfully
2. Handling duplicate student IDs
3. Adding valid grades
4. Rejecting invalid grades (below 0 or above 100)
5. Generating reports for existing students
6. Handling requests for non-existent students
7. Calculating class statistics with multiple students

---

## File Requirements
- **Filename:** `grade_manager.ipynb` (Jupyter notebook)
- **Location:** Save in your cloned repository
- **Structure:** Use markdown cells for explanations, code cells for implementation
- **Testing:** Run each function as you build it

---

## Reflection Questions
After completing your implementation, consider:

1. **Data Structure Choice:** Why did you choose your approach? What are the trade-offs?
2. **Function Design:** Which function was most challenging and why?
3. **Error Handling:** How did you handle edge cases and invalid inputs?
4. **Improvements:** What features would you add with more time?
5. **Real-world Application:** How could this be extended for actual school use?

---

## Extension Challenges

### For Early Finishers:

**Search Functions:**
- Find all students with grades above/below a threshold
- Find top N performing students
- Search students by name

**Data Persistence:**
- Save student data to a text file
- Load student data from a text file
- Import/export CSV format

**Advanced Statistics:**
- Calculate median and mode for grades
- Create text-based grade distribution charts
- Track grade trends over time

**User Interface:**
- Create a menu-driven system
- Add input validation for all user entries
- Implement undo/redo functionality

---

## Getting Started Tips

1. **Start Simple:** Begin with basic data storage and one function
2. **Test Early:** Test each function before moving to the next
3. **Use Print Statements:** Debug by printing your data structure
4. **Plan First:** Sketch out your data structure before coding
5. **Ask Questions:** Discuss different approaches with classmates

---

## Grading Criteria

**Functionality (60%):**
- All required functions work correctly
- Proper error handling and validation
- Accurate calculations and output formatting

**Code Quality (25%):**
- Clear, readable code with good variable names
- Appropriate use of functions and parameters
- Efficient data structure usage

**Problem Solving (15%):**
- Evidence of planning and logical thinking
- Creative solutions to challenges
- Thoughtful reflection on design choices

---

## Need Help?

If you get stuck:
1. Check the hints file (`grade_manager_hints.md`)
2. Review the example data structures above
3. Test with simple cases first
4. Ask a classmate about their approach
5. Raise your hand for teacher assistance

Remember: There are multiple correct ways to solve this problem. Focus on making your solution work well with your chosen data structure!