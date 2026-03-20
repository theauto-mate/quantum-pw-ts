# Login Page Test Plan

## Application Overview

Comprehensive test plan for the login functionality of THE AUTO-MATE CRM application. Covers positive and negative scenarios for username and password validation, including field length constraints (username: 6-15 characters, password: 8-15 characters), authentication flows, and edge cases.

## Test Scenarios

### 1. Positive Login Scenarios

**Seed:** `tests/seed.spec.ts`

#### 1.1. Valid Login with Correct Credentials

**File:** `tests/login-positive.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter a valid username (6-15 characters)
  3. Enter a valid password (8-15 characters)
  4. Click the 'Sign In' button

**Expected Results:**
  - User is successfully logged in and redirected to the dashboard or home page

#### 1.2. Login with Minimum Length Credentials

**File:** `tests/login-positive.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter a username with exactly 6 characters
  3. Enter a password with exactly 8 characters
  4. Click the 'Sign In' button

**Expected Results:**
  - User is successfully logged in and redirected to the dashboard or home page

#### 1.3. Login with Maximum Length Credentials

**File:** `tests/login-positive.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter a username with exactly 15 characters
  3. Enter a password with exactly 15 characters
  4. Click the 'Sign In' button

**Expected Results:**
  - User is successfully logged in and redirected to the dashboard or home page

### 2. Negative Login Scenarios - Field Validation

**Seed:** `tests/seed.spec.ts`

#### 2.1. Username Too Short (Less than 6 characters)

**File:** `tests/login-negative-validation.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter a username with less than 6 characters (e.g., 'abc')
  3. Enter a valid password (8-15 characters)
  4. Click the 'Sign In' button

**Expected Results:**
  - Error message displayed indicating username is too short
  - User remains on login page

#### 2.2. Username Too Long (More than 15 characters)

**File:** `tests/login-negative-validation.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter a username with more than 15 characters
  3. Enter a valid password (8-15 characters)
  4. Click the 'Sign In' button

**Expected Results:**
  - Error message displayed indicating username is too long
  - User remains on login page

#### 2.3. Password Too Short (Less than 8 characters)

**File:** `tests/login-negative-validation.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter a valid username (6-15 characters)
  3. Enter a password with less than 8 characters
  4. Click the 'Sign In' button

**Expected Results:**
  - Error message displayed indicating password is too short
  - User remains on login page

#### 2.4. Password Too Long (More than 15 characters)

**File:** `tests/login-negative-validation.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter a valid username (6-15 characters)
  3. Enter a password with more than 15 characters
  4. Click the 'Sign In' button

**Expected Results:**
  - Error message displayed indicating password is too long
  - User remains on login page

#### 2.5. Empty Username Field

**File:** `tests/login-negative-validation.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Leave username field empty
  3. Enter a valid password (8-15 characters)
  4. Click the 'Sign In' button

**Expected Results:**
  - Error message displayed indicating username is required
  - User remains on login page

#### 2.6. Empty Password Field

**File:** `tests/login-negative-validation.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter a valid username (6-15 characters)
  3. Leave password field empty
  4. Click the 'Sign In' button

**Expected Results:**
  - Error message displayed indicating password is required
  - User remains on login page

#### 2.7. Both Fields Empty

**File:** `tests/login-negative-validation.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Leave both username and password fields empty
  3. Click the 'Sign In' button

**Expected Results:**
  - Error message displayed indicating both fields are required
  - User remains on login page

### 3. Negative Login Scenarios - Edge Cases

**Seed:** `tests/seed.spec.ts`

#### 3.1. Username with Special Characters

**File:** `tests/login-negative-edge.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter username with special characters (e.g., 'user@#$%') within 6-15 length
  3. Enter a valid password
  4. Click the 'Sign In' button

**Expected Results:**
  - Error message displayed or login fails appropriately

#### 3.2. Password with Special Characters

**File:** `tests/login-negative-edge.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter a valid username
  3. Enter password with special characters (e.g., 'pass@#$%') within 8-15 length
  4. Click the 'Sign In' button

**Expected Results:**
  - Error message displayed or login fails appropriately

#### 3.3. Username with Leading/Trailing Spaces

**File:** `tests/login-negative-edge.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter username with leading or trailing spaces (total 6-15 characters)
  3. Enter a valid password
  4. Click the 'Sign In' button

**Expected Results:**
  - Error message displayed or login fails appropriately

#### 3.4. Password with Leading/Trailing Spaces

**File:** `tests/login-negative-edge.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter a valid username
  3. Enter password with leading or trailing spaces (total 8-15 characters)
  4. Click the 'Sign In' button

**Expected Results:**
  - Error message displayed or login fails appropriately

#### 3.5. Username with Unicode Characters

**File:** `tests/login-negative-edge.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter username with unicode characters (e.g., 'tëstûsër') within 6-15 length
  3. Enter a valid password
  4. Click the 'Sign In' button

**Expected Results:**
  - Error message displayed or login fails appropriately

#### 3.6. Password with Unicode Characters

**File:** `tests/login-negative-edge.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter a valid username
  3. Enter password with unicode characters (e.g., 'pâsswörd') within 8-15 length
  4. Click the 'Sign In' button

**Expected Results:**
  - Error message displayed or login fails appropriately

### 4. Negative Login Scenarios - Security

**Seed:** `tests/seed.spec.ts`

#### 4.1. SQL Injection Attempt in Username

**File:** `tests/login-negative-security.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter SQL injection payload in username field (e.g., "' OR '1'='1")
  3. Enter a valid password
  4. Click the 'Sign In' button

**Expected Results:**
  - Login attempt is blocked or sanitized
  - No unauthorized access

#### 4.2. SQL Injection Attempt in Password

**File:** `tests/login-negative-security.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter a valid username
  3. Enter SQL injection payload in password field (e.g., "' OR '1'='1")
  4. Click the 'Sign In' button

**Expected Results:**
  - Login attempt is blocked or sanitized
  - No unauthorized access

#### 4.3. XSS Attempt in Username

**File:** `tests/login-negative-security.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter XSS payload in username field (e.g., "<script>alert('xss')</script>")
  3. Enter a valid password
  4. Click the 'Sign In' button

**Expected Results:**
  - Login attempt is blocked or sanitized
  - No unauthorized access

#### 4.4. XSS Attempt in Password

**File:** `tests/login-negative-security.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter a valid username
  3. Enter XSS payload in password field (e.g., "<script>alert('xss')</script>")
  4. Click the 'Sign In' button

**Expected Results:**
  - Login attempt is blocked or sanitized
  - No unauthorized access

### 5. Negative Login Scenarios - Authentication

**Seed:** `tests/seed.spec.ts`

#### 5.1. Invalid Username with Valid Password

**File:** `tests/login-negative-auth.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter a non-existent username (6-15 characters)
  3. Enter a valid password (8-15 characters)
  4. Click the 'Sign In' button

**Expected Results:**
  - Error message displayed indicating invalid credentials
  - User remains on login page

#### 5.2. Valid Username with Invalid Password

**File:** `tests/login-negative-auth.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter a valid username (6-15 characters)
  3. Enter an incorrect password (8-15 characters)
  4. Click the 'Sign In' button

**Expected Results:**
  - Error message displayed indicating invalid credentials
  - User remains on login page

#### 5.3. Both Invalid Credentials

**File:** `tests/login-negative-auth.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter a non-existent username (6-15 characters)
  3. Enter an incorrect password (8-15 characters)
  4. Click the 'Sign In' button

**Expected Results:**
  - Error message displayed indicating invalid credentials
  - User remains on login page

#### 5.4. Case Sensitive Username Check

**File:** `tests/login-negative-auth.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter a valid username with different case (e.g., 'UserName' instead of 'username')
  3. Enter the correct password
  4. Click the 'Sign In' button

**Expected Results:**
  - Error message displayed indicating invalid credentials
  - User remains on login page

#### 5.5. Case Sensitive Password Check

**File:** `tests/login-negative-auth.spec.ts`

**Steps:**
  1. Navigate to the login page
  2. Enter a valid username
  3. Enter the correct password with different case (e.g., 'Password' instead of 'password')
  4. Click the 'Sign In' button

**Expected Results:**
  - Error message displayed indicating invalid credentials
  - User remains on login page
