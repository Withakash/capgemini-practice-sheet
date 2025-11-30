# Problem Statement 1

Alice likes collecting soft toys. Every day, she adds one soft toy to her collection more than she did the day before.

* She adds **1** soft toy on the **first day**
* **2** soft toys on the **second day**
* **3** soft toys on the **third day**, and so on

A day is considered **special** if the **total number of soft toys collected up to that day** is **divisible by 5**.

You are given an integer **N**, representing the total number of days.
Your task is to **find and return the count of special days** between **1 and N (inclusive)**.

---

## Input Specification

* **input1:** An integer **N**, representing the number of days Alice collects soft toys.

## Output Specification

* Return an integer value representing the **count of special days** between **1 and N**.

---

## Example 1

**Input:**

```
6
```

### Working

| Day | Total Soft Toys | Divisible by 5? |
| --- | --------------- | --------------- |
| 1   | 1               | No              |
| 2   | 3               | No              |
| 3   | 6               | No              |
| 4   | 10              | Yes             |
| 5   | 15              | Yes             |
| 6   | 21              | No              |

**Special Days:** 4, 5
**Count:** 2

**Output:**

```
2
```

---

## Example 2

**Input:**

```
10
```

**Output:**

```
4
```

---

# Problem Statement 2

You are a teacher organizing a field trip for your students. You have a class of **N students**, and you want to divide them into **two groups** for the trip.

However, there is a **special requirement**:

* **One group must contain only students with even-numbered IDs**
* **The other group must contain only students with odd-numbered IDs**
* **Both groups must be of the same length**

Your task is to find and return an integer value representing the **maximum number of students** that can be included **in both groups**.

---

## Input Specification

* **input1:** An integer value **N** representing the total number of students.
* **input2:** An integer array containing the **IDs of the students**.

---

## Output Specification

Return an integer value representing the **maximum number of students** that can be included in both groups.

---

## Example 1

**Input:**

```
input1: 4
input2: {5, 2, 3, 6}
```

### Explanation

There are four students with IDs {5, 2, 3, 6}.

* Even IDs: {2, 6} → count = 2
* Odd IDs: {5, 3} → count = 2

Both groups can have **2 students each**, which is the maximum possible.

**Output:**

```
2
```

---

## Example 2

**Input:**

```
input1: 3
input2: {1, 2, 1}
```

### Explanation

* Even IDs: {2} → count = 1
* Odd IDs: {1, 1} → count = 2

The groups must be of equal size, so the maximum possible group size is **1**.

**Output:**

```
1
```


# Problem Statement 3

A spinner game has the digits **0-9** on it. In each round, the spinner shows the **last digit of your current number**.

You start the first round with a number **N**.
In each following round, you **multiply K with your current number**.

You are given the starting number **N** and the multiplier **K**.
Your task is to:

1. Determine **all distinct digits** that can appear on the spinner if the game continues forever.
2. Compute and return the **product of these distinct digits**.

---

## Input Specification

* **input1:** An integer value **N**, denoting the starting number.
* **input2:** An integer value **K**, denoting the multiplier for each round.

---

## Output Specification

Return an integer value representing the **product of all distinct possible digits** that will show up on the spinner if the game is played forever.

---

## Example 1

**Input:**

```
input1: 11
input2: 3
```

### Explanation

* Start with **11** → last digit **1**
* Next: 11 × 3 = 33 → last digit **3**
* Next: 33 × 3 = 99 → last digit **9**
* Next: 99 × 3 = 297 → last digit **7**
* Next: 297 × 3 = 891 → last digit **1** (cycle repeats)

Distinct digits appearing: **1, 3, 9, 7**

Product = **1 × 3 × 9 × 7 = 189**

**Output:**

```
189
```



# Problem Statement 4

Tom is a maths teacher who is teaching **Geometric Progression (GP)** in his class.
He starts with a sequence where the first term is **A₁** and the common ratio is **R**.

Each subsequent term in the sequence is obtained by multiplying the previous term by **R**.

Your task is to generate and return an **integer array** that contains the GP series **up to the largest term that is less than or equal to a given limit Z**.

---

## Input Specification

* **input1:** An integer value **A₁**, representing the first term of the sequence.
* **input2:** An integer value **R**, representing the common ratio of the sequence.
* **input3:** An integer value **Z**, representing the upper limit.

---

## Output Specification

Return an **integer array** containing the GP series **until the largest term that is ≤ Z**.

---

## Example 1

**Input:**

```
input1: 2
input2: 3
input3: 100
```

### Working

* First term = 2
* Next term = 2 × 3 = 6
* Next term = 6 × 3 = 18
* Next term = 18 × 3 = 54
* Next term = 54 × 3 = 162 → exceeds 100 → stop

**Output:**

```
[2, 6, 18, 54]
```















# Problem Statement 5 — Password Strength Indicator

You are creating a **Password Strength Indicator** for a new website.  
The goal is to set up correct logic for checking password strength and displaying appropriate messages.

However, the project is not yet complete, and you need to finish it.

---

## 🎯 Objectives

- Add a **placeholder** attribute with value:  
  **"Enter your password"**  
  to the input element with `id="passwordInput"`

- Fill logic to **check password strength** and **update the strength indicator** when password changes.

- Set color to **#e74c3c** for the strength indicator when class is `"weak"`.

---

## 🧩 Output (Expected UI)

A card-like design showing:

- Password Strength heading  
- Password input field  
- Strength message such as:  
  **Weak Password** (in red background)

---

## 📄 HTML Code

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Password Strength</title>
    <link rel="stylesheet" href="index.css">
</head>
<body>
    <div class="main-container">
        <div class="container">
            <h1>Password Strength</h1>
            <input type="password" id="passwordInput" class="password-input" placeholder="Enter your password">

            <div id="strengthIndicator" class="strength_indicator">
                <span id="strengthText">Enter a password</span>
            </div>
        </div>
    </div>

    <script src="index.js"></script>
</body>
</html>
```

---

## 🎨 CSS Code — `index.css`

```css
body {
    font-family: Arial, sans-serif;
}

.main-container {
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background: #f6f6f6;
}

.container {
    background: white;
    padding: 30px;
    border-radius: 12px;
    box-shadow: 0px 0px 10px rgba(0,0,0,0.1);
}

.password-input {
    width: 100%;
    padding: 10px;
    margin-top: 10px;
    font-size: 16px;
    border: 2px solid #ccc;
    border-radius: 8px;
}

.strength_indicator {
    margin-top: 15px;
    padding: 12px;
    border-radius: 8px;
    text-align: center;
    font-weight: bold;
}

.weak {
    background-color: #e74c3c;
    color: white;
}

.medium {
    background-color: #f1c40f;
    color: white;
}

.strong {
    background-color: #2ecc71;
    color: white;
}
```

---

## ⚙️ JavaScript Code — `index.js`

```javascript
const passwordInput = document.getElementById("passwordInput");
const strengthIndicator = document.getElementById("strengthIndicator");
const strengthText = document.getElementById("strengthText");

passwordInput.addEventListener("input", checkStrength);

function checkStrength() {
    const pwd = passwordInput.value;

    if (pwd.length === 0) {
        strengthIndicator.className = "strength_indicator";
        strengthText.textContent = "Enter a password";
        return;
    }

    let strength = getStrengthLevel(pwd);

    if (strength === "weak") {
        strengthIndicator.className = "strength_indicator weak";
        strengthText.textContent = "Weak Password";
    } 
    else if (strength === "medium") {
        strengthIndicator.className = "strength_indicator medium";
        strengthText.textContent = "Medium Password";
    } 
    else {
        strengthIndicator.className = "strength_indicator strong";
        strengthText.textContent = "Strong Password";
    }
}

function getStrengthLevel(password) {
    let hasLetters = /[a-zA-Z]/.test(password);
    let hasNumbers = /[0-9]/.test(password);
    let hasSpecial = /[^a-zA-Z0-9]/.test(password);

    if (password.length < 4) return "weak";

    if ((hasLetters && hasNumbers) || (hasLetters && hasSpecial) || (hasNumbers && hasSpecial)) {
        if (password.length >= 8) return "strong";
        return "medium";
    }

    return "weak";
}
```

---

## ✅ What This Solves

✔ Adds placeholder  
✔ Implements strength checking  
✔ Updates UI dynamically  
✔ Applies red color (`#e74c3c`) for weak passwords  

---

## 📥 Download File

This `.md` file is generated automatically.




