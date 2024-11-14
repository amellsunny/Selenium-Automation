# Selenium Automation Cheat Sheet (Java)

## Getting Started

### Set Up Selenium

Add the following dependencies to your `pom.xml` (if using Maven):

```xml
<dependency>
    <groupId>org.seleniumhq.selenium</groupId>
    <artifactId>selenium-java</artifactId>
    <version>4.x.x</version>
</dependency>
```

### Import and Setup WebDriver

```java
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.By;

public class SeleniumExample {
    public static void main(String[] args) {
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");
        WebDriver driver = new ChromeDriver();
        driver.get("https://example.com");
    }
}
```

---

## Basic Commands

### Opening and Closing Browser

```java
driver.get("https://example.com");  // Open URL
driver.close();                     // Close current tab
driver.quit();                      // Quit the entire browser
```

### Navigating

```java
driver.navigate().back();           // Go back
driver.navigate().forward();        // Go forward
driver.navigate().refresh();        // Refresh page
```

---

## Locating Elements

### By Different Selectors
```java
driver.findElement(By.id("element-id"));             // By ID
driver.findElement(By.name("element-name"));         // By Name
driver.findElement(By.className("class-name"));      // By Class Name
driver.findElement(By.tagName("tag-name"));          // By Tag Name
driver.findElement(By.linkText("Link Text"));        // By Link Text
driver.findElement(By.partialLinkText("Text"));      // By Partial Link Text
driver.findElement(By.cssSelector("css=selector"));  // By CSS Selector
driver.findElement(By.xpath("//tag[@attr='value']"));// By XPath
```

### Multiple Elements

```java
List<WebElement> elements = driver.findElements(By.className("class-name"));  // Returns list of matching elements
```

---

## Interacting with Elements

### Clicking and Typing

```java
element.click();                      // Click element
element.sendKeys("text");             // Type text in input field
```

### Clearing Text Fields

```java
element.clear();                      // Clear existing text in input field
```

### Selecting Checkboxes and Radio Buttons

```java
WebElement checkbox = driver.findElement(By.id("checkbox-id"));
checkbox.click();                     // Select checkbox or radio button
```

---

## Verifying Elements

### Checking if Displayed, Enabled, or Selected

```java
element.isDisplayed();                // Returns true if visible
element.isEnabled();                  // Returns true if enabled
element.isSelected();                 // Returns true if selected (for checkboxes/radios)
```

### Asserting Text or Attributes

```java
Assert.assertEquals("Expected Text", element.getText());   // Verify element text
Assert.assertEquals("value", element.getAttribute("attribute")); // Verify attribute value
```

---

## Waiting for Elements

### Implicit Wait

```java
driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));  // Waits 10 seconds for elements to appear
```

### Explicit Wait

```java
import org.openqa.selenium.support.ui.WebDriverWait;
import org.openqa.selenium.support.ui.ExpectedConditions;

WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));  // 10-second explicit wait

// Wait until element is clickable
WebElement element = wait.until(ExpectedConditions.elementToBeClickable(By.id("element-id")));
```

---

## Handling Alerts and Pop-ups

### Alert Handling

```java
Alert alert = driver.switchTo().alert();
alert.accept();                      // Accept alert
alert.dismiss();                     // Dismiss alert
alert.sendKeys("text");              // Send text to alert (if input field is present)
```

---

## Working with Frames

### Switching to a Frame

```java
driver.switchTo().frame("frame-name");                      // Switch by name or ID
driver.switchTo().frame(driver.findElement(By.tagName("iframe"))); // Switch by WebElement
driver.switchTo().defaultContent();                         // Switch back to main content
```

---

## Taking Screenshots

### Full Page Screenshot

```java
File screenshot = ((TakesScreenshot)driver).getScreenshotAs(OutputType.FILE);
FileUtils.copyFile(screenshot, new File("screenshot.png"));
```

### Element Screenshot

```java
WebElement element = driver.findElement(By.id("element-id"));
File screenshot = element.getScreenshotAs(OutputType.FILE);
FileUtils.copyFile(screenshot, new File("element_screenshot.png"));
```

---

## Scrolling and Actions

### Scrolling to Element

```java
WebElement element = driver.findElement(By.id("element-id"));
((JavascriptExecutor)driver).executeScript("arguments[0].scrollIntoView();", element);
```

### Advanced User Actions

```java
import org.openqa.selenium.interactions.Actions;

Actions actions = new Actions(driver);
actions.moveToElement(element).click().perform(); // Hover and click
actions.dragAndDrop(source, target).perform();    // Drag and drop
```

---

## Closing Browser

### Exiting WebDriver

```java
driver.close();  // Close current tab
driver.quit();   // Close all tabs and exit WebDriver
```

---

## Tips & Best Practices

- **Use Explicit Waits**: Prefer `WebDriverWait` over implicit waits for better control.
- **Avoid `Thread.sleep()`**: Use Selenium’s waits instead for reliability.
- **Organize Locators**: Store locators in constants or external files.
- **Capture Screenshots on Failures**: This can help you debug failed tests.

---