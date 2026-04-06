#  Bug & Error Finder

**Static code analysis tool** that scans JavaScript, TypeScript, and Python-like code for syntax errors, runtime pitfalls, security risks, and logic smells — all in your browser.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow.svg)
![Platform](https://img.shields.io/badge/platform-Web%20%7C%20Browser-lightgrey)

---

##  Features

-  **Instant Bug Detection** – Paste code and get real-time diagnostics
-  **Smart Heuristics** – Catches undefined variables, type coercion, missing await, dangerous `eval()`, loose equality, and more
-  **Multi-language Support** – Works with JavaScript, TypeScript, Python (basic), and pseudo-code
-  **Severity Levels** – Issues are classified as **Error**, **Warning**, or **Suggestion**
-  **Clean Dashboard** – Side-by-side editor and report panel
-  **Example Loader** – One-click example to demonstrate detection capabilities
-  **Zero Dependencies** – Pure HTML/CSS/JS, runs entirely client-side

---

##  Live Demo

Try it instantly: **[Bug & Error Finder Live](https://your-username.github.io/bug-error-finder)**  
*(Replace with your actual GitHub Pages URL after deployment)*

---

##  How It Works

1. **Paste** your code into the editor
2. **Click** "Find Bugs & Errors"
3. **Review** the report with line numbers and fix suggestions

The analyzer scans for:
- Unbalanced brackets / parentheses
- Implicit global variables
- `==` vs `===` misuse
- Missing `await` in async functions
- `eval()` and `Function()` constructor usage
- Potential XSS via `innerHTML`
- Infinite loops (`while(true)`, `for(;;)`)
- Console statements left in production
- Python-specific issues (missing colons, bare `except`)

---

##  Screenshot

```
+-----------------------------+-----------------------------+
|  Code Editor                |  Bug Report                 |
|  ┌─────────────────────┐    |   WARNING: Implicit global|
|  │ function divide(a,b)│    |   ERROR: Assignment in if |
|  │   if(b = 0) {...}   │    |   SUGGESTION: Use ===     |
|  │ }                   │    |                             |
|  └─────────────────────┘    |  Stats: 2 errors, 1 warning  |
+-----------------------------+-----------------------------+
```

---

## Installation & Usage

### Local Setup
```bash
git clone https://github.com/your-username/bug-error-finder.git
cd bug-error-finder
open index.html
```

### Or use directly
Copy the `index.html` file and open it in any modern browser — no server required.

---

##  Example Code to Test

Paste this snippet to see the analyzer in action:

```javascript
// Buggy example
function calculate(a, b) {
  if (b = 0) {         //  Assignment instead of equality
    return "Cannot divide by zero";
  }
  return a / b;
}

let result = calculate(10, 0);
myGlobal = 42;         // Implicit global

let total = "5" + 10;  // String coercion: "510"

async function fetchData() {
  const data = fetch('/api');  //  Missing await
  console.log(data);
}

eval('alert("unsafe")');       //  Dangerous eval
```

---

##  Detection Rules (Partial List)

| Category | Pattern Detected | Severity |
|----------|------------------|----------|
| Syntax | Unbalanced `{}`, `()`, `[]` | Error |
| Security | `eval()`, `new Function()` | Error |
| Logic | Assignment in `if` condition | Error |
| Best Practice | Loose equality `==` | Suggestion |
| Type Safety | String + number concatenation | Warning |
| Async | Promise without `await` or `.then` | Warning |
| Scope | Implicit global variable | Warning |
| Performance | Infinite loop patterns | Warning |
| Python | Missing colon after `def` | Error |
| Debugging | Leftover `console.log` | Suggestion |
| XSS Risk | `innerHTML` with dynamic content | Warning |

---

##  Technologies Used

- **HTML5** – Structure and layout
- **CSS3** – Gradient backgrounds, glassmorphism, responsive grid
- **JavaScript (ES6+)** – Static analysis engine, regex-based heuristics
- **Font Awesome Icons** (via emoji) – Clean visual indicators

---

##  Project Structure

```
bug-error-finder/
├── index.html          # Main application (all-in-one)
└── README.md           # This file
```

*(The tool is self-contained in a single HTML file for easy deployment)*

---

##  Contributing

Contributions are welcome! To add new detection rules:

1. Fork the repository
2. Open `index.html`
3. Locate the `BugFinder` class (around line 200+)
4. Add a new method like `detectMyPattern()`
5. Call it inside the `analyze()` method
6. Submit a pull request

Example rule addition:
```javascript
detectMyPattern() {
  if (this.code.includes('dangerousPattern')) {
    this.addIssue('error', 'Title', 'Description', null, 'error');
  }
}
```

---

##  License

MIT License – free for personal and commercial use.

---
##  Acknowledgements

- Inspired by ESLint, PyLint, and other static analysis tools
- Icons and styling with modern CSS trends

---

##  Contact

Open an issue on GitHub for bugs, suggestions, or feature requests.

---

**Happy bug hunting!** 🐞🔍
```
