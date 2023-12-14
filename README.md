# Django Mini-Loan App

This Django application is designed to manage loan requests, user authentication, and loan repayments.

## Table of Contents

- [Overview](#overview)
- [Installation](#installation)
- [Usage](#usage)
- [Structure](#structure)
- [Models](#models)
- [Views](#views)
- [URLs](#urls)
- [Authentication](#authentication)
- [Video Demonstration](#video-demonstration)

## Overview

The Mini-Loan app allows users to request loans, view loan details, and manage repayments. It consists of several components:

- **Models**: Defines the database structure including `Customer`, `Loan`, and `Repayment`.
- **Views**: Handles user interactions and data rendering using Django's views.
- **URLs**: Manages the routing and URL configurations for different app functionalities.
- **Authentication**: Manages user authentication using Django's built-in authentication system.

## Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/Danuragtiwari/mini-loan.git
   ```

Apply migrations:

python manage.py migrate

## Usage

To start the Django development server:


python manage.py runserver


Access the app through http://localhost:8000/.

Admin credentials:

Username: admin

Password: admin

#### Structure

* app/: Contains the Django app files.
* models.py: Defines the database models.
* views.py: Handles the app's views and logic.
* urls.py: Manages the app's URL routing.
* templates/: Holds HTML templates for rendering views.

#### Models

###### Customer

    Represents a user and is associated with a Django User instance.

###### Fields:

    user: One-to-One relationship with Django's User model.

###### Loan

    Represents a loan request.

###### Fields:

* customer: Foreign key relationship with Customer.
* amount: Decimal field to store the loan amount.
* term: Integer field to represent the loan term.
* state: Char field for the loan state (e.g., PENDING, APPROVED).

###### Repayment

* Stores repayment details for loans.

###### Fields:

* loan: Foreign key relationship with Loan.
* amount: Decimal field for the repayment amount.
* scheduled_date: Date field for the scheduled repayment date.
* status: Char field for the repayment status (e.g., PENDING, PAID).

## Views

### add_repayment

Handles the addition of repayments for a given loan.

Dependencies:

- Requires a logged-in user.
- Uses Repayment model.

Features:

- Processes user input for repayment amount.
- Updates repayment status and loan status accordingly.
- Redirects to the loan overview page (loan_view).

### change_loan_status

Allows staff members to change the status of a loan.

Dependencies:

- Requires staff privileges.
- Uses Loan model.

Features:

- Accepts a new status via a form.
- Updates the loan status.
- Redirects to the loan overview page (loan_view).

### signup

Handles user registration.

Dependencies:

- Uses Django's UserCreationForm.

Features:

- Validates and saves new user registration.
- Authenticates the user.
- Redirects to the login page.

### user_login

Manages user login.

Dependencies:

- Uses Django's AuthenticationForm.

Features:

- Authenticates user credentials.
- Redirects to the loan overview page (loan_view) on successful login.

### user_logout

Logs out the user.

Features:

- De-authenticates the user.
- Redirects to the login page.

### create_loan

Facilitates the creation of a new loan.

Dependencies:

- Requires a logged-in user.
- Uses Loan model.

Features:

- Processes user input for loan amount and term.
- Creates a new loan instance.
- Redirects to the loan overview page (loan_view).

### approve_loan

Allows staff members to approve a loan.

Dependencies:

- Requires staff privileges.
- Uses Loan model.

Features:

- Changes the loan status to 'APPROVED'.
- Redirects to the loan overview page (loan_view).

### view_loans

Displays a list of loans based on user roles.

Dependencies:

- Uses Loan and Customer models.

Features:

- Differentiates between staff and regular users.
- Retrieves and displays relevant loan information.

## URLs

- [/create_loan/](#create_loan)
- [/approve_loan/](#approve_loan)[int:loan_id](int:loan_id)/
- [/change_loan_status/](#change_loan_status)[int:loan_id](int:loan_id)/
- [/view_loans/](#view_loans)
- [/add_repayment/](#add_repayment)[int:loan_id](int:loan_id)/
- [/signup/](#signup)
- [/login/](#login)
- [/logout/](#logout)

## Authentication

### User Registration (signup)

Allows users to register by providing necessary information and creates a new user account.

### User Login (user_login)

Authenticates user credentials for logging into the system.

### User Logout (user_logout)

Logs out the currently logged-in user from the system.

## Video Demonstration

[Watch the Video Demonstration][(https://drive.google.com/file/d/16oOcDuNBHA2EmmZy6wrMsobb6LS6W3xU/view)]
