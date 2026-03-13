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


````markdown
# Playwright Interview Answers (Section 2 – Locators and Elements)

# 21. What are locators in Playwright?

## Answer

Locators are the **mechanism used to find and interact with elements on a web page**.

Playwright locators are powerful because they include:

- Auto waiting
- Retry logic
- Better stability compared to traditional selectors

Locators represent **a way to query elements repeatedly until the condition is satisfied**.

---

### Example

```javascript
const loginButton = page.locator("#login");
await loginButton.click();
````

---

### Practical QA Example

Test case: Verify login button is visible.

```javascript
await expect(page.locator("#login")).toBeVisible();
```

---

# 22. What are the recommended locator strategies in Playwright?

## Answer

Playwright recommends **user-facing locators** because they are more stable and readable.

Best locator priority order:

1. getByRole
2. getByLabel
3. getByPlaceholder
4. getByText
5. getByTestId
6. CSS/XPath (last option)

---

### Example

```javascript
await page.getByRole("button", { name: "Login" }).click();
```

---

### Practical QA Example

Login button:

```javascript
await page.getByRole("button", { name: "Sign in" }).click();
```

---

# 23. What is the difference between locator() and page.$()?

## Answer

| Feature         | locator() | page.$() |
| --------------- | --------- | -------- |
| Auto wait       | Yes       | No       |
| Retry mechanism | Yes       | No       |
| Recommended     | Yes       | No       |
| Stability       | High      | Low      |

---

### Example using locator()

```javascript
await page.locator("#submit").click();
```

---

### Example using page.$()

```javascript
const element = await page.$("#submit");
await element.click();
```

`locator()` is recommended for modern Playwright automation.

---

# 24. What is the getByRole() locator?

## Answer

`getByRole()` locates elements using **ARIA roles**, which represent how users interact with UI components.

Examples of roles:

* button
* textbox
* link
* checkbox
* heading

---

### Example

```javascript
await page.getByRole("button", { name: "Login" }).click();
```

---

### Practical QA Example

Verify a button exists.

```javascript
await expect(page.getByRole("button", { name: "Submit" })).toBeVisible();
```

---

# 25. What is the getByText() locator?

## Answer

`getByText()` locates elements using **visible text on the page**.

This is useful when elements do not have unique IDs.

---

### Example

```javascript
await page.getByText("Login").click();
```

---

### Practical QA Example

Verify success message.

```javascript
await expect(page.getByText("Login successful")).toBeVisible();
```

---

# 26. What is the getByLabel() locator?

## Answer

`getByLabel()` finds form fields associated with a **label element**.

This is very useful for form automation.

---

### Example

```javascript
await page.getByLabel("Email").fill("test@email.com");
```

---

### Practical QA Example

Login form automation.

```javascript
await page.getByLabel("Username").fill("admin");
await page.getByLabel("Password").fill("admin123");
```

---

# 27. What is the getByPlaceholder() locator?

## Answer

`getByPlaceholder()` locates input fields using their **placeholder text**.

---

### Example

```javascript
await page.getByPlaceholder("Enter email").fill("test@email.com");
```

---

### Practical QA Example

Search functionality.

```javascript
await page.getByPlaceholder("Search products").fill("Laptop");
```

---

# 28. How do you locate dynamic elements in Playwright?

## Answer

Dynamic elements have:

* changing IDs
* dynamic attributes
* generated class names

To handle them:

* Use partial selectors
* Use text-based locators
* Use role-based locators

---

### Example

Dynamic ID:

```html
<button id="login_12345">
```

Use partial match:

```javascript
await page.locator('[id^="login"]').click();
```

---

### Practical QA Example

Locate dynamic product cards.

```javascript
await page.getByText("Add to cart").first().click();
```

---

# 29. How do you handle elements with changing IDs?

## Answer

Avoid using dynamic IDs.

Instead use:

* role locator
* text locator
* relative locator
* CSS partial match

---

### Example

Dynamic element:

```html
<input id="user_83923">
```

Better locator:

```javascript
await page.getByLabel("Username").fill("admin");
```

---

# 30. How do you verify element visibility in Playwright?

## Answer

Playwright provides built-in assertions.

---

### Example

```javascript
await expect(page.locator("#login")).toBeVisible();
```

---

### Practical QA Example

Verify error message appears.

```javascript
await expect(page.getByText("Invalid credentials")).toBeVisible();
```

---

# 31. How do you verify element text in Playwright?

## Answer

Use `toHaveText()` assertion.

---

### Example

```javascript
await expect(page.locator("#message"))
.toHaveText("Login successful");
```

---

### Practical QA Example

Verify order confirmation.

```javascript
await expect(page.getByText("Order placed")).toBeVisible();
```

---

# 32. How do you check if an element is enabled or disabled?

## Answer

Playwright provides two assertions:

* toBeEnabled()
* toBeDisabled()

---

### Example

```javascript
await expect(page.locator("#submit")).toBeEnabled();
```

---

### Practical QA Example

Verify submit button is disabled until form is filled.

```javascript
await expect(page.locator("#submit")).toBeDisabled();
```

---

# 33. How do you verify element attribute value?

## Answer

Use `toHaveAttribute()`.

---

### Example

```javascript
await expect(page.locator("#email"))
.toHaveAttribute("type", "email");
```

---

### Practical QA Example

Verify link URL.

```javascript
await expect(page.locator("a.contact"))
.toHaveAttribute("href","/contact");
```

---

# 34. How do you locate elements inside shadow DOM?

## Answer

Playwright automatically supports **shadow DOM traversal**.

---

### Example

```javascript
await page.locator("custom-element >> button").click();
```

---

### Practical QA Example

Testing web components.

```javascript
await page.locator("app-login >> #submit").click();
```

---

# 35. How do you chain locators in Playwright?

## Answer

Locator chaining allows finding elements **inside another element**.

This improves locator accuracy.

---

### Example

```javascript
await page.locator(".product-card")
.locator("button")
.click();
```

---

### Practical QA Example

Select a product and click add to cart.

```javascript
await page.locator(".product-card")
.filter({ hasText: "Laptop" })
.getByRole("button", { name: "Add to cart" })
.click();
```

# Playwright Interview Answers (Section 3 – Actions and Interactions)

# 36. How do you navigate to a URL using Playwright?

## Answer

Navigation is performed using the `page.goto()` method.

It opens a webpage in the current browser tab.

---

### Example

```javascript
await page.goto("https://example.com");
````

---

### Practical QA Example

Test case: Open login page.

```javascript
await page.goto("https://example.com/login");
```

---

# 37. How do you click an element?

## Answer

Playwright provides the `click()` method to perform click actions.

Playwright automatically waits until the element is:

* visible
* enabled
* stable

---

### Example

```javascript
await page.locator("#login").click();
```

---

### Practical QA Example

Click login button.

```javascript
await page.getByRole("button", { name: "Login" }).click();
```

---

# 38. How do you type text in an input field?

## Answer

Use the `fill()` method to enter text.

This method clears existing text before typing.

---

### Example

```javascript
await page.fill("#username", "admin");
```

---

### Practical QA Example

Fill login form.

```javascript
await page.fill("#username", "admin");
await page.fill("#password", "admin123");
```

---

# 39. How do you clear text from a field?

## Answer

Use the `fill()` method with an empty value.

---

### Example

```javascript
await page.fill("#username", "");
```

---

### Practical QA Example

Clear search box.

```javascript
await page.fill("#search", "");
```

---

# 40. How do you perform a double click?

## Answer

Use the `dblclick()` method.

---

### Example

```javascript
await page.dblclick("#file");
```

---

### Practical QA Example

Open file with double click.

```javascript
await page.locator(".document").dblclick();
```

---

# 41. How do you perform a right-click?

## Answer

Right-click can be performed using the `click()` method with button option.

---

### Example

```javascript
await page.click("#menu", { button: "right" });
```

---

### Practical QA Example

Open context menu.

```javascript
await page.locator(".file").click({ button: "right" });
```

---

# 42. How do you perform a hover action?

## Answer

Use the `hover()` method.

Hover is commonly used to open menus.

---

### Example

```javascript
await page.hover("#menu");
```

---

### Practical QA Example

Hover over navigation menu.

```javascript
await page.locator(".nav-menu").hover();
```

---

# 43. How do you select a dropdown value?

## Answer

Use `selectOption()` for HTML select dropdowns.

---

### Example

```javascript
await page.selectOption("#country", "India");
```

---

### Practical QA Example

Select country during registration.

```javascript
await page.selectOption("#country", "USA");
```

---

# 44. How do you check/uncheck checkboxes?

## Answer

Playwright provides `check()` and `uncheck()` methods.

---

### Example

```javascript
await page.check("#terms");
```

---

### Uncheck example

```javascript
await page.uncheck("#terms");
```

---

### Practical QA Example

Accept terms and conditions.

```javascript
await page.check("#acceptTerms");
```

---

# 45. How do you handle radio buttons?

## Answer

Radio buttons can be selected using `check()`.

---

### Example

```javascript
await page.check("#male");
```

---

### Practical QA Example

Select gender option.

```javascript
await page.check("input[value='female']");
```

---

# 46. How do you upload files using Playwright?

## Answer

File uploads are handled using `setInputFiles()`.

---

### Example

```javascript
await page.setInputFiles("#upload", "testfile.pdf");
```

---

### Practical QA Example

Upload profile picture.

```javascript
await page.setInputFiles("#profileUpload", "profile.png");
```

---

# 47. How do you download files using Playwright?

## Answer

Playwright provides `waitForEvent('download')` to capture downloads.

---

### Example

```javascript
const download = await page.waitForEvent("download");

await page.click("#downloadBtn");
```

---

### Practical QA Example

Verify invoice download.

```javascript
const download = await page.waitForEvent("download");

await page.click("#downloadInvoice");
```

---

# 48. How do you take screenshots of a page?

## Answer

Playwright provides `page.screenshot()`.

---

### Example

```javascript
await page.screenshot({ path: "page.png" });
```

---

### Practical QA Example

Capture failure screenshot.

```javascript
await page.screenshot({ path: "login_error.png" });
```

---

# 49. How do you take screenshots of a specific element?

## Answer

You can capture a screenshot of a locator.

---

### Example

```javascript
await page.locator("#logo").screenshot({ path: "logo.png" });
```

---

### Practical QA Example

Capture product card image.

```javascript
await page.locator(".product-card").screenshot({ path: "product.png" });
```

---

# 50. How do you scroll to an element?

## Answer

Use `scrollIntoViewIfNeeded()`.

---

### Example

```javascript
await page.locator("#footer").scrollIntoViewIfNeeded();
```

---

### Practical QA Example

Scroll to load more products.

```javascript
await page.locator(".load-more").scrollIntoViewIfNeeded();
```

```
```



