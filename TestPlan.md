# T-Mobile Website UI Testing: Test Plan

## Project Overview
This project aims to validate the UI elements and core functionality of the T-Mobile website using Selenium WebDriver in Java. 
The focus is on testing crucial site sections (Home, Shop, Deals, Support, Account, and Footer) to ensure a smooth user experience and functional interactions. 
The automation will be implemented with TestNG and Maven to enable continuous integration and reliable testing.


## 1. Test Plan Details
- **Project Name**: T-Mobile Website UI Test Automation
- **Prepared by**: Amal Sunny
- **Date**: 06 January 2024
- **Tools and Technologies**: Selenium WebDriver, TestNG, Java, Maven, ChromeDriver, GitHub for version control



## 2. Scope of Testing
This test plan addresses functional UI testing for several critical website sections:
- **Home Page**: Testing navigation, banners, and search bar.
- **Shop Page**: Testing product filters, categories, and product details.
- **Deals Page**: Validating promotions and deal categories.
- **Support Page**: Verifying FAQ, Contact Us, and Chat Support options.
- **Account Page**: Testing login, account display, and logout.
- **Footer**: Checking social media, legal links, and newsletter subscription.


## 3. Test Objectives
Key objectives include:
- **Ensuring** that navigation between main pages is seamless.
- **Verifying** essential UI components like banners, links, and search bars function correctly.
- **Validating** product filters and search functionality.
- **Confirming** support and account access work as intended.
- **Ensuring** footer links redirect accurately.
-

## 4. Test Cases Overview
A summary of test cases for each section:

### HomePageTests
1. Verify that the main banner loads correctly.
2. Check navigation links (Shop, Deals, Support).
3. Validate search functionality.
4. Ensure footer links are accessible and correctly redirect.

### ShopPageTests
1. Confirm Shop page filters display as expected.
2. Test category filtering (e.g., Phones).
3. Verify product detail page access.
4. Validate Add to Cart functionality.

### DealsPageTests
1. Ensure deals are visible.
2. Test category filtering on deals (e.g., Phones).
3. Verify accessibility of promotional deals.
4. Check navigation back to the homepage.

### SupportPageTests
1. Test Support page and main section visibility.
2. Access FAQ page.
3. Verify Contact Us button.
4. Confirm chat support availability.

### AccountPageTests
1. Test login with valid credentials.
2. Verify login error with invalid credentials.
3. Confirm account information display.
4. Test logout functionality.

### FooterTests
1. Check social media links are clickable.
2. Verify legal links (Privacy Policy, Terms).
3. Test newsletter subscription.


## 5. Test Execution Strategy
### Environment
Tests will be executed using the Chrome browser to match user experience on popular web environments.

### Execution Order
The order of test execution will follow the structure:
1. Homepage
2. Shop
3. Deals
4. Support
5. Account
6. Footer

### Automation
Tests will be automated using Selenium WebDriver with TestNG for structured assertions, allowing detailed reports and better integration with CI/CD pipelines.


## 6. Test Entry and Exit Criteria
### Entry Criteria
- Fully configured test environment.
- Access to the T-Mobile test URLs.
- Completion of all test setup and preparation.

### Exit Criteria
- Successful execution of all critical test cases.
- All major issues documented.
- Any failed tests are logged for further review and analysis.


## 7. Risks and Dependencies
### Risks
- UI layout changes may necessitate updates to locators and test flows.
- Potential issues accessing third-party URLs or social media links if they change or are blocked.

### Dependencies
- Testing is limited to Chrome compatibility; additional browsers may need separate testing.
- Some pages or links might be restricted based on user permissions or geographical restrictions.

