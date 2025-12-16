# Saucedemo Login Feature


## Scenario 1: Login with Valid Credentials

**Given** the user is on the Saucedemo login page  
**When** the user enters username `standard_user`  
**And** the user enters password `secret_sauce`  
**And** the user clicks the Login button  
**Then** the user should be redirected to the Products page

---

## Scenario 2: Login Attempt with Empty Fields

**Given** the user is on the Saucedemo login page  
**When** the user leaves the username field empty  
**And** the user leaves the password field empty  
**And** the user clicks the Login button  
**Then** an error message should be displayed saying "Username is required"

---

## Scenario 3: Login Attempt with Invalid Credentials

**Given** the user is on the Saucedemo login page  
**When** the user enters username `invalid_user`  
**And** the user enters password `wrong_password`  
**And** the user clicks the Login button  
**Then** an error message should be displayed saying "Username and password do not match any user in this service"

---
