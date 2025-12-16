# Part 3 – Theoretical Questions

## 1. What is CI/CD and how do automated tests run in this process?

**CI/CD** stands for **Continuous Integration/Continuous Delivery**. It automates building, testing, and deploying applications.

**Continuous Integration (CI)**: Developers merge code frequently into a central repository. Automated builds and tests run on every commit to catch issues early.

**Continuous Delivery/Deployment (CD)**: After successful CI, code is either prepared for release (Continuous Delivery) or automatically deployed to production (Continuous Deployment).

**How Automated Tests Run:**
1. Developer pushes code to repository
2. CI/CD tool (Jenkins, GitHub Actions, etc.) detects the change
3. Code is built in a clean environment
4. Tests execute in order: unit tests → integration tests → E2E tests
5. Results are reported to the team
6. If tests pass, code proceeds to deployment; if tests fail, pipeline stops


---

## 2. What is the difference between E2E, Smoke, and Regression testing?

**End-to-End (E2E) Testing**
- Tests complete user workflows from start to finish
- Covers the entire application: frontend, backend, database, and integrations
- Example: login → browse products → add to cart → checkout → payment
- Comprehensive but slower execution

**Smoke Testing**
- Quick verification that critical features work after deployment
- Tests only the most important functionality (happy paths)
- Example: Can users log in? Does the homepage load?
- Fast execution, acts as a sanity check before running full test suite

**Regression Testing**
- Ensures new code changes haven't broken existing functionality
- Re-runs existing test cases to verify previously working features
- Example: After adding a new payment method, verify existing payment methods still work
- Comprehensive and typically automated


---

## 3. Why are waits important in automation and what is the correct way to use them in Playwright?

**Why Waits Are Important**

Modern web applications load elements asynchronously. Without proper waits, tests become flaky because elements may not be ready when the test tries to interact with them. This causes intermittent failures that are hard to debug.

**Correct Way to Use Waits in Playwright**

**1. Auto-Waiting (Default)**
Playwright automatically waits for elements to be actionable:

```typescript
await page.click('#submitButton');
await page.fill('#username', 'testuser');
```

**2. Explicit Waits with Assertions**

```typescript
// Wait for element to be visible
await expect(page.locator('#successMessage')).toBeVisible();

// Wait for element to contain text
await expect(page.locator('.status')).toContainText('Completed');
```

**3. Wait for Network/State**

```typescript
await page.waitForLoadState('networkidle');
await page.waitForResponse(response => 
  response.url().includes('/api/users')
);
```

**What to Avoid**

```typescript
// Don't use hard-coded timeouts
await page.waitForTimeout(3000); // Makes tests slow and still flaky
```