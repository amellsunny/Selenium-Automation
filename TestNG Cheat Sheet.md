# TestNG Cheat Sheet

## Table of Contents
1. [Setting Up TestNG](#setting-up-testng)
2. [TestNG Annotations](#testng-annotations)
3. [TestNG Configuration Annotations](#testng-configuration-annotations)
4. [Assertions](#assertions)
5. [Grouping Tests](#grouping-tests)
6. [Parameterization](#parameterization)
7. [TestNG XML Configuration](#testng-xml-configuration)
8. [DataProvider (Data-Driven Testing)](#dataprovider-data-driven-testing)
9. [Dependency Testing](#dependency-testing)
10. [TestNG Reports](#testng-reports)

---

## 1. Setting Up TestNG

### Maven Dependency
Add this to your `pom.xml` to use TestNG with Maven:

```xml
<dependency>
    <groupId>org.testng</groupId>
    <artifactId>testng</artifactId>
    <version>7.4.0</version>
    <scope>test</scope>
</dependency>
```
### Importing TestNG Classes

```
import org.testng.annotations.Test;
import org.testng.Assert;
```
## 2. TestNG Annotations

### @Test
Marks a method as a test method.

```java
@Test
public void testMethod() {
    // Test code
}
```

### @BeforeSuite
Runs before all tests in the suite.

```java
@BeforeSuite
public void beforeSuite() {
    // Setup code
}
```

### @AfterSuite
Runs after all tests in the suite.

```java
@AfterSuite
public void afterSuite() {
    // Cleanup code
}
```

### @BeforeTest
Runs before any <test> tag in the XML.

```java
@BeforeTest
public void beforeTest() {
    // Initialization code
}
```

### @AfterTest
Runs after all <test> tags in the XML.

```java
@AfterTest
public void afterTest() {
    // Tear down code
}
```
## 3. TestNG Configuration Annotations

### @BeforeClass and @AfterClass
Runs before/after the first method in the current class.

```java
@BeforeClass
public void beforeClass() {
    // Code to run before class
}
```

@AfterClass
public void afterClass() {
    // Code to run after class
}
### @BeforeMethod and @AfterMethod
Runs before/after each test method.

```java
@BeforeMethod
public void beforeMethod() {
    // Setup code
}

@AfterMethod
public void afterMethod() {
    // Teardown code
}
```

## 4. Assertions

### Assert Equals

```java
Assert.assertEquals(actual, expected, "Optional failure message");
```

### Assert True / False
```java
Assert.assertTrue(condition, "Optional failure message");
Assert.assertFalse(condition, "Optional failure message");
```
### Assert Not Null / Null
```java
Assert.assertNotNull(object, "Optional failure message");
Assert.assertNull(object, "Optional failure message");
```

### Fail Explicitly
```java
Assert.fail("Forced failure message");
```

## 5. Grouping Tests

### Define Groups

```java
@Test(groups = {"smoke", "regression"})
public void testMethod() {
    // Test code
}
```
### Run Specific Groups (testng.xml)
```xml
<groups>
    <run>
        <include name="smoke"/>
        <include name="regression"/>
    </run>
</groups>
```

## 6. Parameterization

### Parameters in XML

```java
@Test
@Parameters({"parameterName"})
public void testMethod(String parameterName) {
    System.out.println("Parameter value: " + parameterName);
}
```

Define parameters in testng.xml:

```xml
<parameter name="parameterName" value="parameterValue"/>
```

## 7. TestNG XML Configuration

### Basic Structure of testng.xml

```xml
<!DOCTYPE suite SYSTEM "https://testng.org/testng-1.0.dtd" >
<suite name="SuiteName">
    <test name="TestName">
        <classes>
            <class name="com.example.YourTestClass"/>
        </classes>
    </test>
</suite>
Define Multiple Classes
xml
Copy code
<classes>
    <class name="com.example.FirstTestClass"/>
    <class name="com.example.SecondTestClass"/>
</classes>
```

## 8. DataProvider (Data-Driven Testing)

### Using @DataProvider
Define a @DataProvider and link it to the test.

```java
@DataProvider(name = "dataMethod")
public Object[][] dataProviderMethod() {
    return new Object[][] { { "data1" }, { "data2" } };
}

@Test(dataProvider = "dataMethod")
public void testMethod(String data) {
    System.out.println("Data: " + data);
}
```

## 9. Dependency Testing

### Dependent Tests
Run a test only if another test is successful.

```java
@Test(dependsOnMethods = {"methodName"})
public void dependentTest() {
    // Test code
}
```

### Dependency on Groups

```java
@Test(dependsOnGroups = {"groupName"})
public void groupDependentTest() {
    // Test code
}
```
## 10. TestNG Reports

### Default HTML and XML Reports

After running tests, TestNG generates test-output folder with:

- index.html (HTML report)
- testng-results.xml (XML report)

### Custom Listeners for Advanced Reporting

Implement custom reporting with listeners by creating a class that implements ITestListener, ISuiteListener, or other interfaces.

Example:

```java
import org.testng.ITestListener;
import org.testng.ITestResult;

public class CustomListener implements ITestListener {
    @Override
    public void onTestSuccess(ITestResult result) {
        System.out.println("Test Passed: " + result.getName());
    }

    // Implement other listener methods as needed
}
```

### Adding Listeners in XML

Add a listener in testng.xml:

```xml
<listeners>
    <listener class-name="com.example.CustomListener"/>
</listeners>
```

## Additional Tips

Parallel Execution: Configure parallel execution in testng.xml by setting parallel attribute in <suite>.

Retry Logic: Use IRetryAnalyzer to retry failed tests.

Soft Assertions: Use SoftAssert for multiple assertions without stopping on the first failure.

Ignoring Tests: Use @Test(enabled = false) to skip a test.

