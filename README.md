# ☕ Core JavaScript for Automation

<div align="center">

![JavaScript](https://img.shields.io/badge/JavaScript-ES2022%2B-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Node.js](https://img.shields.io/badge/Node.js-18%2B-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Playwright](https://img.shields.io/badge/Playwright-45ba4b?style=for-the-badge&logo=playwright&logoColor=white)
![Cypress](https://img.shields.io/badge/Cypress-17202C?style=for-the-badge&logo=cypress&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

### 🚀 Fast-track Your Journey from Manual Tester to Automation Engineer

*Learn ONLY the JavaScript you need for Test Automation - No Fluff, Just Real-World Skills*

[📖 Documentation](#-topics-covered) • [🎯 Getting Started](#-getting-started) • [💡 Examples](#-learning-path) • [🤝 Contribute](#-contributing)

</div>

---

## 📖 Overview

Welcome to **Core JavaScript for Automation**! This repository is your express lane to mastering JavaScript for Test Automation. Whether you're working with **Playwright**, **Cypress**, **WebdriverIO**, or **Puppeteer**, this repo teaches you the exact JavaScript concepts you'll use daily.

### 🎯 What Makes This Different?

| ❌ Traditional JavaScript Courses | ✅ This Repository |
|:----------------------------------|:-------------------|
| Covers DOM manipulation (jQuery) | **Focuses on Automation Patterns** |
| Generic programming examples | **Real Playwright/Cypress scenarios** |
| 500+ hours of content | **Targeted 40-hour learning path** |
| Theory-heavy | **Code-first approach with comments** |

---

## 🎪 JavaScript Concepts → Automation Mapping

See how JavaScript powers your automation framework:

```
┌─────────────────────────────────────────────────────────────────┐
│                    AUTOMATION FRAMEWORK                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  🔄 Async/Await                                                 │
│     const page = await browser.newPage(); ← Promise-based       │
│                                                                 │
│  🔐 Classes & Encapsulation                                     │
│     #loginBtn = page.locator('#login'); ← Page Object Model     │
│     async clickLogin() {...}                                    │
│                                                                 │
│  🧬 Inheritance                                                 │
│     BasePage ← LoginPage ← CheckoutPage  ← Reusable setup      │
│                                                                 │
│  📚 Arrays & Objects                                            │
│     const links = await page.$$('a');                           │
│     const testData = JSON.parse(fs.readFileSync(...));          │
│                                                                 │
│  ⚠️ Error Handling                                              │
│     try { await element.click(); }                              │
│     catch (error) { await page.screenshot(); throw error; }     │
│                                                                 │
│  🌊 Array Methods (ES6+)                                        │
│     const links = await page.$$('a');                           │
│     const visibleLinks = links.filter(el => el.isVisible());   │
│     const texts = await Promise.all(links.map(el => el.textContent())); │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📂 Repository Structure

```
core-js-for-automation/
│
├── 📁 src/
│   │
│   ├── 📂 basics/
│   │   ├── dataTypesDemo.js              # Primitives vs Objects
│   │   ├── operatorsExample.js           # Conditional checks in tests
│   │   ├── loopsDemo.js                  # Iterating elements
│   │   └── stringManipulation.js         # Parsing UI text & JSON
│   │
│   ├── 📂 oops/
│   │   ├── inheritanceExample.js         # BasePage pattern
│   │   ├── classesAndObjects.js          # Page Object Model
│   │   ├── encapsulationPOM.js           # Private fields in POM
│   │   └── abstractionDemo.js            # Interfaces via duck typing
│   │
│   ├── 📂 async/
│   │   ├── promisesExample.js            # Understanding Promises
│   │   ├── asyncAwaitDemo.js             # async/await in tests
│   │   ├── promiseAllExample.js          # Parallel test actions
│   │   └── errorHandlingAsync.js         # Handling async errors
│   │
│   ├── 📂 collections/
│   │   ├── arrayMethodsDemo.js           # map, filter, find, reduce
│   │   ├── setExample.js                 # Unique window handles
│   │   ├── mapExample.js                 # Test data management
│   │   └── destructuringDemo.js          # ES6 destructuring
│   │
│   ├── 📂 exceptions/
│   │   ├── tryCatchExample.js            # Handling test exceptions
│   │   ├── customErrors.js               # Framework-specific errors
│   │   └── bestPractices.js              # Error handling patterns
│   │
│   └── 📂 fileio/
│       ├── readEnvFile.js                # .env config management
│       ├── readExcelData.js              # Data-driven testing
│       └── readJSONFile.js               # JSON test data
│
├── 📁 tests/                              # Test specs for each concept
├── 📁 resources/
│   ├── .env                               # Sample configuration
│   ├── testdata.xlsx                      # Excel test data
│   └── users.json                         # JSON test data
│
├── package.json                           # npm dependencies
├── playwright.config.js                   # Playwright configuration
├── README.md                              # You are here!
└── LICENSE
```

---

## 📚 Topics Covered

### 🔷 Module 1: JavaScript Fundamentals
<details>
<summary>Click to expand</summary>

#### ✅ Variables & Data Types
```javascript
// Why it matters: Playwright/Cypress return different data types
const timeout = 10000;                           // Wait duration in ms
const pageTitle = await page.title();            // String from UI
const isVisible = await element.isVisible();     // Boolean validation flag
let retryCount = 0;                              // Mutable counter

// use const by default, let only when reassignment is needed
```

#### ✅ Control Flow & Loops
```javascript
// Real automation scenario: Verify all links on a page
const links = await page.$$('a');

for (const link of links) {
    const isVisible = await link.isVisible();
    if (isVisible) {
        const text = await link.textContent();
        console.log(text);
    }
}
```

</details>

---

### 🔷 Module 2: String Manipulation
<details>
<summary>Click to expand</summary>

Strings are everywhere in automation: URLs, selectors, test data, API responses.

```javascript
// Building dynamic selectors (Template Literals)
const username = 'admin';
const dynamicSelector = `//div[text()='${username}']`;

// Validating text from UI
const actualText = (await element.textContent()).trim().toLowerCase();
expect(actualText).toContain('welcome');

// String methods for parsing responses
const responseBody = await response.text();
const lines = responseBody.split('\n');
const trimmed = lines.map(line => line.trim());
```

**Key Methods:** `substring()`, `split()`, `replace()`, `includes()`, `trim()`, `toLowerCase()`, `startsWith()`, `endsWith()`

**Template Literals (ES6):** Use backticks `` ` `` for dynamic string building — much cleaner than concatenation!

</details>

---

### 🔷 Module 3: Classes & Object-Oriented Patterns
<details>
<summary>Click to expand</summary>

#### 🎯 Classes & Objects
```javascript
// Page Object Model pattern
class LoginPage {
    constructor(page) {
        this.page = page;
        this.usernameField = page.locator('#username');
        this.passwordField = page.locator('#password');
        this.loginButton = page.locator('#loginBtn');
    }

    async login(username, password) {
        await this.usernameField.fill(username);
        await this.passwordField.fill(password);
        await this.loginButton.click();
    }
}

module.exports = { LoginPage };
```

#### 🎯 Inheritance
```javascript
// BasePage class - Reusable methods for all pages
class BasePage {
    constructor(page) {
        this.page = page;
    }

    async navigateTo(url) {
        await this.page.goto(url);
    }

    async waitForPageLoad() {
        await this.page.waitForLoadState('networkidle');
    }
}

class LoginPage extends BasePage {
    constructor(page) {
        super(page); // Calls BasePage constructor
        this.loginButton = page.locator('#loginBtn');
    }
}
```

#### 🎯 Private Fields (ES2022)
```javascript
// Protecting internal state — like Encapsulation in Java
class LoginPage {
    #page;                              // Private field
    #loginButton;

    constructor(page) {
        this.#page = page;
        this.#loginButton = page.locator('#loginBtn');
    }

    async clickLogin() {               // Public method
        await this.#loginButton.click();
    }
}
```

#### 🎯 Duck Typing as Abstraction
```javascript
// JavaScript doesn't have interfaces, but we follow the same pattern
// Any object with a .click(), .fill() etc. can be used as a WebElement
class HighlightedElement {
    constructor(locator) {
        this.locator = locator;
    }

    async click() {
        await this.locator.highlight();
        await this.locator.click();
    }
}
```

</details>

---

### 🔷 Module 4: Async / Await & Promises
<details>
<summary>Click to expand</summary>

> ⚡ This is the most important module for JavaScript automation. Every browser action is asynchronous!

#### Understanding Promises
```javascript
// Playwright returns Promises for every browser interaction
const titlePromise = page.title();  // Returns a Promise, not a string yet
const title = await titlePromise;   // Resolve the Promise
```

#### async/await in Tests
```javascript
// Every test function must be async
test('Login test', async ({ page }) => {
    await page.goto('https://example.com/login');
    await page.fill('#username', 'admin');
    await page.fill('#password', 'password');
    await page.click('#loginBtn');
    await expect(page).toHaveURL('/dashboard');
});
```

#### Running Actions in Parallel with Promise.all
```javascript
// Sequential (SLOW): Each waits for the previous to complete
const title = await page.title();
const url = page.url();

// Parallel (FAST): Both run at the same time
const [title, url] = await Promise.all([
    page.title(),
    Promise.resolve(page.url())
]);

// Real use case: Hover and wait for tooltip simultaneously
await Promise.all([
    page.hover('#info-icon'),
    page.waitForSelector('.tooltip')
]);
```

</details>

---

### 🔷 Module 5: Array Methods (ES6+)
<details>
<summary>Click to expand</summary>

| Method | Automation Use Case | Returns |
|:-------|:--------------------|:--------|
| **filter()** | Find visible/enabled elements | New filtered array |
| **map()** | Extract text from all elements | Transformed array |
| **find()** | Get the first matching element | Single element |
| **forEach()** | Perform action on each element | undefined |
| **some()** | Check if any element matches | Boolean |
| **every()** | Check all elements match | Boolean |
| **reduce()** | Aggregate test results | Single value |

```javascript
// map(): Extract text from all table rows
const rows = await page.$$('table tr');
const rowTexts = await Promise.all(
    rows.map(row => row.textContent())
);

// filter(): Keep only visible links
const links = await page.$$('a');
const visibleLinks = [];
for (const link of links) {
    if (await link.isVisible()) {
        visibleLinks.push(link);
    }
}

// find(): Get first element with specific text
const errorMsg = rowTexts.find(text => text.includes('Error'));

// every(): Validate all prices are positive
const prices = [10.99, 25.00, 5.49];
const allPositive = prices.every(price => price > 0); // true
```

</details>

---

### 🔷 Module 6: Destructuring & Spread (ES6)
<details>
<summary>Click to expand</summary>

```javascript
// Object Destructuring: Clean up test data extraction
const userData = { username: 'admin', password: 'Test@123', role: 'admin' };
const { username, password } = userData; // Extract only what you need

// Array Destructuring: Useful with Promise.all
const [titleResult, urlResult] = await Promise.all([
    page.title(),
    Promise.resolve(page.url())
]);

// Default values in destructuring
const { timeout = 5000, retries = 3 } = config;

// Spread operator: Merge test config objects
const defaultConfig = { timeout: 30000, headless: true };
const testConfig = { ...defaultConfig, headless: false }; // Override headless
```

</details>

---

### 🔷 Module 7: Exception Handling
<details>
<summary>Click to expand</summary>

#### Common Automation Errors You'll Handle:
- `TimeoutError` → Element not found within timeout
- `Error: strict mode violation` → Multiple elements matched a selector
- `Error: Target page, context or browser has been closed` → Browser crashed
- `AssertionError` → Test assertion failed

```javascript
// Robust click with error handling
async function safeClick(page, selector) {
    try {
        await page.click(selector, { timeout: 5000 });
    } catch (error) {
        if (error.message.includes('timeout')) {
            console.error(`Element not found: ${selector}`);
            await page.screenshot({ path: 'error-screenshot.png' });
            throw error; // Re-throw so the test fails
        }
        // Try JavaScript click as fallback
        await page.$eval(selector, el => el.click());
    }
}

// Custom Error class for framework errors
class ElementNotReadyError extends Error {
    constructor(selector) {
        super(`Element '${selector}' is not ready for interaction`);
        this.name = 'ElementNotReadyError';
        this.selector = selector;
    }
}
```

</details>

---

### 🔷 Module 8: File Handling (I/O)
<details>
<summary>Click to expand</summary>

Essential for:
- Reading `.env` files (URLs, credentials)
- Excel files for data-driven testing
- JSON files for API test data

```javascript
// Reading .env file (using dotenv package)
require('dotenv').config();
const appUrl = process.env.APP_URL;
const username = process.env.USERNAME;

// Reading JSON test data (built-in)
const fs = require('fs');
const testData = JSON.parse(fs.readFileSync('./resources/users.json', 'utf-8'));
const { username, password } = testData.users[0];

// Reading Excel (using exceljs package)
const ExcelJS = require('exceljs');
const workbook = new ExcelJS.Workbook();
await workbook.xlsx.readFile('./resources/testdata.xlsx');
const sheet = workbook.getWorksheet('TestData');
const username = sheet.getRow(2).getCell(1).value;
```

</details>

---

### 🔷 Module 9: Modern JavaScript (ES2020+)
<details>
<summary>Click to expand</summary>

#### Optional Chaining (`?.`)
```javascript
// Before: Verbose null checks
const text = element && element.textContent ? element.textContent : null;

// With optional chaining
const text = await element?.textContent();

// Useful when element might not exist
const errorMessage = await page.$('.error-msg');
const errorText = await errorMessage?.textContent() ?? 'No error shown';
```

#### Nullish Coalescing (`??`)
```javascript
// Use default values cleanly
const timeout = config.timeout ?? 30000;
const baseUrl = process.env.BASE_URL ?? 'http://localhost:3000';
```

#### Arrow Functions
```javascript
// Before ES6
links.forEach(function(link) {
    console.log(link.textContent());
});

// With Arrow Functions
links.forEach(link => console.log(link.textContent()));

// Multi-line arrow function
const getVisibleLinks = async (page) => {
    const links = await page.$$('a');
    return links.filter(async link => await link.isVisible());
};
```

</details>

---

## 🛠️ Prerequisites

Before you begin, ensure you have:

| Tool | Version | Download Link |
|:-----|:--------|:--------------|
| 🟢 **Node.js** | 18 LTS or 20+ | [Download Node.js](https://nodejs.org/) |
| 📦 **npm** | Comes with Node.js | Bundled with Node.js |
| 💻 **IDE** | Latest | [VS Code](https://code.visualstudio.com/) (Recommended) |
| 📦 **Git** | Latest | [Download Git](https://git-scm.com/downloads) |

### ✅ Verify Installation

```bash
# Check Node.js version
node -v

# Check npm version
npm -v

# Check Git version
git --version
```

---

## 🚀 Getting Started

### Step 1: Clone the Repository

```bash
git clone https://github.com/your-username/core-js-for-automation.git
cd core-js-for-automation
```

### Step 2: Install Dependencies

```bash
npm install
```

### Step 3: Install Playwright Browsers (if using Playwright)

```bash
npx playwright install
```

### Step 4: Run Your First Example

```bash
node src/basics/dataTypesDemo.js
```

Or run Playwright tests:

```bash
npx playwright test
```

### Step 5: Open in VS Code

```bash
code .
```

> 💡 **Recommended VS Code Extensions:**
> - Playwright Test for VS Code
> - ESLint
> - Prettier
> - JavaScript (ES6) code snippets

---

## 💡 Learning Path

Follow this sequence for optimal learning:

```
Week 1: Basics
  ├─ Day 1-2: Variables, Data Types, let/const/var
  ├─ Day 3-4: Control Flow & Loops
  └─ Day 5-7: String Manipulation & Template Literals

Week 2: OOPs & Async
  ├─ Day 8-9: Classes, Objects, Methods
  ├─ Day 10-11: Inheritance & Private Fields
  └─ Day 12-14: Promises, async/await, Promise.all

Week 3: Collections & Exceptions
  ├─ Day 15-17: Array Methods (map, filter, find, reduce)
  └─ Day 18-21: Exception Handling & Custom Errors

Week 4: Advanced Concepts
  ├─ Day 22-24: File I/O (JSON, Excel, .env)
  └─ Day 25-28: ES2020+ Features, Destructuring, Modules

🎯 Total Duration: 28 Days (1 hour/day)
```

---

## 🎓 Practical Exercises

Each module includes:

- ✅ **Commented Code Examples** - Understand *why* this matters for automation
- ✅ **Real Playwright/Cypress Scenarios** - See JavaScript concepts in action
- ✅ **Practice Challenges** - Reinforce your learning
- ✅ **Mini Projects** - Build actual automation utilities

### 🏆 Example Mini Projects

1. **Config Reader Utility** - Read `.env` / JSON config for test configuration
2. **Excel Data Provider** - Build data-driven test framework with ExcelJS
3. **Custom Wait Utility** - Implement smart waits using async/await
4. **Page Object Generator** - Auto-generate POM classes for any page

---

## 📦 Key npm Packages Used

| Package | Purpose | Install |
|:--------|:--------|:--------|
| `playwright` | Browser automation | `npm i @playwright/test` |
| `cypress` | E2E testing | `npm i cypress` |
| `dotenv` | Read `.env` files | `npm i dotenv` |
| `exceljs` | Read/write Excel files | `npm i exceljs` |
| `axios` | HTTP requests for API tests | `npm i axios` |

---

## 🔄 Java → JavaScript Quick Reference

Coming from Java? Here's your cheat sheet:

| Java Concept | JavaScript Equivalent |
|:-------------|:----------------------|
| `WebDriver driver = new ChromeDriver()` | `const browser = await chromium.launch()` |
| `driver.findElement(By.id("x"))` | `page.locator('#x')` |
| `Thread.sleep(2000)` | `await page.waitForTimeout(2000)` |
| `List<WebElement>` | `await page.$$('selector')` |
| `HashMap<String, String>` | `const map = {}` or `new Map()` |
| `try { } catch (Exception e) { }` | `try { } catch (error) { }` |
| `System.out.println()` | `console.log()` |
| `@BeforeMethod` (TestNG) | `test.beforeEach()` (Playwright) |
| `Assert.assertEquals()` | `expect().toBe()` |

---

## 🤝 Contributing

We welcome contributions! Here's how:

1. **Fork** this repository
2. Create a **feature branch** (`git checkout -b feature/AsyncAwaitExample`)
3. **Commit** your changes (`git commit -m 'Add async/await filtering example'`)
4. **Push** to the branch (`git push origin feature/AsyncAwaitExample`)
5. Open a **Pull Request**

### 📝 Contribution Guidelines

- Add comments explaining *why* this concept matters for automation
- Include real Playwright/Cypress/WebdriverIO examples where possible
- Follow existing code structure and naming conventions (`camelCase` for files)
- Update README if adding new topics

---

## 📖 Additional Resources

- 📘 [Playwright Documentation](https://playwright.dev/docs/intro)
- 📙 [Cypress Documentation](https://docs.cypress.io/)
- 📗 [Node.js Docs](https://nodejs.org/en/docs/)
- 📕 [MDN JavaScript Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference)
- 📒 [WebdriverIO Docs](https://webdriver.io/docs/gettingstarted)

---

## 📝 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

---

## 🌟 Star This Repo!

If this repository helped you, please ⭐ **star it** to show your support and help others discover it!

---

<div align="center">

### 💬 Questions or Feedback?

Open an [Issue](https://github.com/your-username/core-js-for-automation/issues) or start a [Discussion](https://github.com/your-username/core-js-for-automation/discussions)

**Happy Automating! 🚀**

</div>
