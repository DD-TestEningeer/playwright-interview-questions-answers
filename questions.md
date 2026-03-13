# Playwright Interview Answers (Section 1 – Basic Questions)

Playwright is a modern automation framework developed by Microsoft and commonly used with Node.js for web automation testing.

---

# 1. What is Playwright?

## Answer
Playwright is an **open-source end-to-end automation testing framework** used to test **web applications across multiple browsers**.

It allows testers to automate:

- UI testing
- Cross-browser testing
- End-to-end testing
- API testing
- Mobile view testing

### Supported Browsers

- Chromium
- Firefox
- WebKit (Safari engine)

---

### Practical QA Example

User flow:

1. Open login page  
2. Enter username  
3. Enter password  
4. Click login  
5. Verify dashboard

### Example Code

```javascript
import { test, expect } from '@playwright/test';

test('Login test', async ({ page }) => {

  await page.goto("https://example.com/login");

  await page.fill("#username","admin");

  await page.fill("#password","admin123");

  await page.click("#login");

  await expect(page).toHaveURL(/dashboard/);

});
````

---

# 2. What are the main features of Playwright?

## Answer

Playwright provides several powerful features:

* Cross-browser testing
* Auto waiting
* Parallel execution
* Built-in reporting
* Network interception
* Mobile device emulation
* Screenshot and video capture

---

### Practical Example (Auto Waiting)

Bad practice:

```javascript
await page.waitForTimeout(5000);
```

Better approach:

```javascript
await page.click("#loginButton");
```

Playwright automatically waits until the element is:

* visible
* enabled
* stable

---

# 3. Who developed Playwright?

Playwright was developed by **Microsoft** and released in **2020**.

It was created by the same engineering team that worked on **Puppeteer**.

### Goal

Create a **modern automation framework with reliable cross-browser testing**.

---

# 4. Which programming languages does Playwright support?

Playwright supports:

* JavaScript
* TypeScript
* Python
* Java
* .NET (C#)

Most companies use:

* JavaScript
* TypeScript

Example:

```javascript
await page.goto("https://example.com");
```

---

# 5. Which browsers are supported by Playwright?

Playwright supports three browser engines.

| Browser Engine | Example Browser |
| -------------- | --------------- |
| Chromium       | Chrome, Edge    |
| Firefox        | Firefox         |
| WebKit         | Safari          |

---

### Practical QA Example

Run the same test across browsers.

```javascript
projects: [

{ name: 'chromium' },

{ name: 'firefox' },

{ name: 'webkit' }

]
```

---

# 6. What is the Playwright Test Runner?

Playwright Test Runner is a **built-in framework** used to execute tests.

Features:

* Parallel execution
* Test retries
* Fixtures
* Reporting
* Test grouping

---

### Example Test

```javascript
import { test, expect } from '@playwright/test';

test('Verify title', async ({ page }) => {

  await page.goto("https://example.com");

  await expect(page).toHaveTitle("Example Domain");

});
```

Run test:

```
npx playwright test
```

---

# 7. How do you install Playwright in a new project?

### Step 1 — Install Node.js

Verify installation:

```
node -v
```

---

### Step 2 — Create Playwright project

```
npm init playwright@latest
```

---

### Step 3 — Choose configuration

Options:

```
JavaScript
Install browsers
Example tests
GitHub Actions
```

---

### Project Structure

```
tests
playwright.config.js
package.json
```

---

# 8. What is the role of Node.js in Playwright?

Node.js is the **runtime environment** used to run Playwright scripts.

Node.js allows us to:

* execute JavaScript automation scripts
* manage dependencies
* install packages using npm

Example command:

```
npx playwright test
```

---

# 9. What is the difference between Playwright and Selenium?

| Feature            | Playwright | Selenium       |
| ------------------ | ---------- | -------------- |
| Auto waiting       | Yes        | No             |
| Speed              | Faster     | Slower         |
| Setup              | Simple     | Complex        |
| Browser control    | Direct     | WebDriver      |
| Parallel execution | Built-in   | External setup |

---

### Example Problem

Selenium often fails with:

```
ElementNotInteractableException
```

Because the element is not loaded.

Playwright automatically waits for the element.

---

# 10. What are the advantages of Playwright over Selenium?

Advantages:

* Auto waiting
* Faster execution
* Network mocking
* Built-in parallel execution
* Modern locator strategies
* Trace viewer debugging

---

### Example (API Mocking)

```javascript
await page.route("**/api/login", route => {

route.fulfill({

status:200,

body:JSON.stringify({success:true})

})

});
```

---

# 11. What is a Browser in Playwright?

A **Browser** represents the browser application instance.

Examples:

* Chromium
* Firefox
* WebKit

---

### Example

```javascript
const browser = await chromium.launch();
```

---

# 12. What is a Page in Playwright?

A **Page** represents a **browser tab**.

Example structure:

```
Browser
   └ Page
        └ Website
```

---

### Example

```javascript
await page.goto("https://google.com");
```

---

# 13. What is a Browser Context in Playwright?

Browser Context is an **isolated browser session** similar to **incognito mode**.

Example:

```
Browser
 ├ Context 1 (User1)
 └ Context 2 (User2)
```

Cookies and sessions are not shared.

---

### Practical QA Example

Testing multiple users:

```
Admin user
Normal user
```

---

# 14. How does Playwright support cross-browser testing?

Playwright runs tests on multiple browsers.

Example configuration:

```javascript
projects: [

{ name: 'chromium' },

{ name: 'firefox' },

{ name: 'webkit' }

]
```

---

### QA Example

Test login flow on:

* Chrome
* Firefox
* Safari

---

# 15. What is headless mode in Playwright?

Headless mode runs the browser **without a visible UI**.

Example:

```
Browser runs in background
```

---

### Example

```javascript
browser.launch({ headless: true })
```

Used in:

* CI/CD pipelines
* automation servers

---

# 16. What is headed mode in Playwright?

Headed mode runs the browser **with a visible UI**.

Example:

```
Browser window visible
```

---

### Example

```javascript
browser.launch({ headless: false })
```

Used for:

* debugging
* test development

---

# 17. How do you run Playwright tests from command line?

Run all tests:

```
npx playwright test
```

Run specific test file:

```
npx playwright test login.spec.js
```

Run UI mode:

```
npx playwright test --ui
```

---

# 18. What is the Playwright configuration file?

The configuration file is:

```
playwright.config.js
```

It defines:

* browsers
* retries
* workers
* timeouts
* reporters

---

### Example

```javascript
module.exports = {

retries:1,

workers:4,

use:{ headless:true }

}
```

---

# 19. What is the command to generate Playwright reports?

Run tests:

```
npx playwright test
```

Open report:

```
npx playwright show-report
```

---

### Report includes

* test results
* screenshots
* execution time
* traces

---

# 20. What is the Playwright Inspector?

Playwright Inspector is a **debugging tool**.

It allows testers to:

* pause test execution
* inspect locators
* step through code
* analyze failures

---

### Run Inspector

```
npx playwright test --debug
```

---

### Capabilities

```
Pause test
Highlight element
Step execution
View DOM
```


