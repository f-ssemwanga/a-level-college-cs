# Password Strength Checker Challenge

## Your Mission
Create a Python program that evaluates password strength and provides helpful feedback to users.

---

## Requirements

### Core Features (Must Have)
Your program should:

1. **Accept a password input** from the user
2. **Check these criteria:**
   - Length (minimum 8 characters)
   - Contains uppercase letters
   - Contains lowercase letters
   - Contains numbers
   - Contains special characters (!@#$%^&* etc.)

3. **Provide clear feedback** showing which criteria are met/missing
4. **Give an overall strength rating** (Weak/Medium/Strong)
5. **Suggest improvements** for weak passwords

### Output Format
Your program should display results clearly, for example:
```
Password Analysis
================
Length (8+ chars): ✓
Uppercase letter: ✗
Lowercase letter: ✓
Number: ✓
Special character: ✗

Overall Strength: Medium (3/5)

Suggestions:
- Add an uppercase letter
- Add a special character (!@#$%^&*)
```

---

## Getting Started

### Step 1: Plan Your Approach
Before coding, think about:
- How will you check each criterion?
- What data types will you use to track results?
- How will you calculate and display the strength score?

### Step 2: Start Simple
Begin with basic password input and one criterion (e.g., length check).

### Step 3: Build Incrementally
Add one criterion at a time and test as you go.

---

## Testing Your Code

Test your program with these passwords:
- `password` (should be weak)
- `Password123` (should be medium)
- `MyP@ssw0rd!` (should be strong)
- `abc` (should be weak - too short)

---

## Extension Challenges

Once your basic version works, try adding:
- **Forbidden passwords:** Reject common weak passwords like "password123"
- **Repeated character detection:** Warn about passwords with too many repeated characters
- **Dictionary word detection:** Check if password contains common English words
- **Entropy calculation:** Calculate and display password randomness score

---

## Hints

<details>
<summary>Click for hints if you're stuck</summary>

### Checking for character types:
```python
# Check if string has uppercase
any(c.isupper() for c in password)

# Check if string has digits
any(c.isdigit() for c in password)

# Check for special characters
special_chars = "!@#$%^&*()_+-=[]{}|;:,.<>?"
any(c in special_chars for c in password)
```

### Creating visual feedback:
```python
# Use checkmarks and crosses
print(f"Length check: {'✓' if condition else '✗'}")

# Count successful criteria
score = sum([check1, check2, check3, check4, check5])
```

</details>

---

## File Requirements
- **Filename:** `password_checker.py`
- **Location:** Save in your working directory
- **Testing:** Run with `Ctrl+Alt+N` in VS Code