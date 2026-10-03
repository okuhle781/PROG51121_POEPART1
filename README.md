## PROG5121POE — Part 1

This project implements a simple **registration and login system in Java**. The application allows a user to register by providing their personal information, username, password, and South African cell phone number. It then validates the information and allows the user to log in using their registered credentials.

The project also includes **JUnit tests** to verify that the validation and login functionality works correctly.

---

## Features

The application provides the following functionality:

* Register a new user.
* Validate the username.
* Validate password complexity.
* Validate the South African cell phone number.
* Display appropriate registration messages.
* Log in using the registered username and password.
* Display a successful or unsuccessful login message.
* Run automated JUnit tests.

---

## Project Structure

```text
src/
│
├── Main.java
├── Login.java
└── LoginTest.java
```

### `Login.java`

The `Login` class contains the main registration and login functionality.

It contains the following methods:

* `checkUserName()`
* `checkPasswordComplexity()`
* `checkCellPhoneNumber()`
* `registerUser()`
* `loginUser()`
* `returnLoginStatus()`

### `Main.java`

The `Main` class runs the console application.

It:

1. Requests the user's first name.
2. Requests the user's last name.
3. Requests a username.
4. Requests a password.
5. Requests a cell phone number.
6. Validates the registration information.
7. Requests login details.
8. Displays the login status.

### `LoginTest.java`

The `LoginTest` class contains JUnit tests for the registration and login functionality.

The tests check both valid and invalid inputs.

---

## Username Validation

The username must:

* Contain an underscore (`_`).
* Be no more than **5 characters long**.

For example:

```text
kyl_1
```

is a valid username.

An example of an invalid username is:

```text
kyle!!!!!!1!
```

The validation is performed by:

```java
public boolean checkUserName() {
    return username.contains("_") && username.length() <= 5;
}
```

---

## Password Validation

The password must:

* Contain at least **8 characters**.
* Contain at least **one capital letter**.
* Contain at least **one number**.
* Contain at least **one special character**.

For example:

```text
Ch&&sec@ke99!
```

satisfies the password requirements.

The validation is performed by:

```java
public boolean checkPasswordComplexity() {
    if (password.length() < 8) {
        return false;
    }

    boolean hasCapital = false;
    boolean hasNumber = false;
    boolean hasSpecialCharacter = false;

    for (char c : password.toCharArray()) {
        if (Character.isUpperCase(c)) {
            hasCapital = true;
        }

        if (Character.isDigit(c)) {
            hasNumber = true;
        }

        if (!Character.isLetterOrDigit(c)) {
            hasSpecialCharacter = true;
        }
    }

    return hasCapital && hasNumber && hasSpecialCharacter;
}
```

---

## Cell Phone Validation

The application checks that the South African cell phone number is entered using the international format beginning with:

```text
+27
```

Example of a valid number:

```text
+27838968976
```

The validation uses the following regular expression:

```java
^\\+27[0-9]{10}$
```

This ensures that the number begins with `+27` and is followed by 10 digits.

---

## Registration

The `registerUser()` method checks the username, password and cell phone number.

If the information is valid, the following message is returned:

```text
User registered successfully.
```

If the username is invalid, an appropriate error message is displayed.

If the password is invalid, an appropriate password error message is displayed.

If the cell phone number is invalid, an appropriate cell phone error message is displayed.

---

## Login

The `loginUser()` method compares the username and password entered by the user with the registered credentials.

Example:

```java
public boolean loginUser(String enteredUsername, String enteredPassword) {
    return username.equals(enteredUsername)
            && password.equals(enteredPassword);
}
```

If both credentials are correct, the login is successful.

The `returnLoginStatus()` method then displays:

```text
Welcome Kyle Smith, it is great to see you again.
```

If the credentials are incorrect, the application displays:

```text
Username or password incorrect, please try again.
```

---

## Testing

JUnit is used to test the functionality of the application.

The tests include:

### Username Tests

* Correct username.
* Incorrect username.

### Password Tests

* Correct password.
* Incorrect password.

### Cell Phone Tests

* Correct cell phone number.
* Incorrect cell phone number.

### Login Tests

* Successful login.
* Failed login.

Both `assertEquals`, `assertTrue`, and `assertFalse` are used to test the expected results.

---

## Example Test Data

| Field      | Valid Example   | Invalid Example |
| ---------- | --------------- | --------------- |
| Username   | `kyl_1`         | `kyle!!!!!!1!`  |
| Password   | `Ch&&sec@ke99!` | `password`      |
| Cell Phone | `+27838968976`  | `08966553`      |

---

## How to Run the Application

### 1. Clone the Repository

Clone the project from GitHub and open it in your Java IDE.

### 2. Open the Project

Open the project in an IDE such as:

* IntelliJ IDEA
* NetBeans
* Eclipse

### 3. Compile the Project

Make sure that the Java files are located in the appropriate source folder.

### 4. Run `Main.java`

Run:

```text
Main.java
```

The application will open in the console and request the user's registration information.

### 5. Run the Tests

Run:

```text
LoginTest.java
```

using the JUnit test runner.

All tests should pass when the implementation is correct.

---

## Example Console Interaction

```text
===== Registration =====

Enter your first name: Kyle
Enter your last name: Smith
Enter username: kyl_1
Enter password: Ch&&sec@ke99!
Enter South African cell phone number: +27838968976

User registered successfully.
Username successfully captured.
Password successfully captured.
Cell number successfully captured.

===== Login =====

Enter username: kyl_1
Enter password: Ch&&sec@ke99!

Welcome Kyle Smith, it is great to see you again.
```

---

## Technologies Used

* **Java**
* **JUnit 5**
* **GitHub**
* Console-based Java application

---

## Testing Approach

The application uses unit testing to verify individual methods independently.

The tests verify that:

1. Valid usernames are accepted.
2. Invalid usernames are rejected.
3. Valid passwords are accepted.
4. Invalid passwords are rejected.
5. Valid cell phone numbers are accepted.
6. Invalid cell phone numbers are rejected.
7. Correct login credentials result in a successful login.
8. Incorrect login credentials result in a failed login.

---

## Author

**PROG5121POE — Part 1**

Registration and Login Feature implemented in Java.
