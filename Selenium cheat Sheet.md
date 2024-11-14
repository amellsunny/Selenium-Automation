# Selenium Automation Cheat Sheet

## Table of Contents
1. [Setting Up Selenium](#1.-setting-up-selenium)
2. [Locating Elements](#2.-locating-elements)
3. [Element Interactions](3.-#element-interactions)
4. [Assertions](#4.-assertions)
5. [Waiting for Elements](#5.-waiting-for-elements)
6. [Browser Management](#6.-browser-management)
7. [Common Actions](#7.-common-actions)

---

## 1. Setting Up Selenium

### Install Selenium

from selenium import webdriver

from selenium.webdriver.common.by import By

from selenium.webdriver.common.keys import Keys

from selenium.webdriver.support.ui import WebDriverWait

from selenium.webdriver.support import expected_conditions as EC


## 2. Locating Elements

### By ID

element = driver.find_element(By.ID, "element-id")

### By Name

element = driver.find_element(By.NAME, "element-name")

### By Class Name

element = driver.find_element(By.CLASS_NAME, "element-class")

### By XPath

element = driver.find_element(By.XPATH, "//tagname[@attribute='value']")

### By CSS Selector

element = driver.find_element(By.CSS_SELECTOR, "css-selector")

### By Link Text

element = driver.find_element(By.LINK_TEXT, "Link Text")

### By Partial Link Text

element = driver.find_element(By.PARTIAL_LINK_TEXT, "Partial Link")

## 3. Element Interactions

### Clicking an Element

element.click()

### Sending Keys (Typing in Input Fields)

element.send_keys("text to type")

### Clear Text in Input Field

element.clear()

### Submit a Form

element.submit()

### Get Element Text

text = element.text

### Get Element Attribute

attribute_value = element.get_attribute("attribute-name")

### Check if an Element is Selected (Checkbox, Radio Button)

is_selected = element.is_selected()

### Check if an Element is Displayed (Visible)

is_displayed = element.is_displayed()

### Check if an Element is Enabled (Interactable)

is_enabled = element.is_enabled()

## 4. Assertions

### Assert Text Matches Expected Value

assert element.text == "Expected Text", "Text does not match!"

### Assert Element is Selected (for Checkboxes)

assert element.is_selected() == True, "Element is not selected!"

### Assert Attribute Matches Expected Value

assert element.get_attribute("attribute-name") == "expected-value", "Attribute does not match!"

## 5. Waiting for Elements

### Implicit Wait (Global)

driver.implicitly_wait(10)  # waits for elements up to 10 seconds

### Explicit Wait (Condition-Based)

wait = WebDriverWait(driver, 10)  # Wait for a condition up to 10 seconds

element = wait.until(EC.element_to_be_clickable((By.ID, "element-id")))

### Wait Until Element is Visible

wait.until(EC.visibility_of(element))

### Wait Until Element is Clickable

wait.until(EC.element_to_be_clickable((By.ID, "element-id")))

## 6. Browser Management

### Launching a Browser (Chrome)

driver = webdriver.Chrome(executable_path="/path/to/chromedriver")

### Launching a Browser (Firefox)

driver = webdriver.Firefox(executable_path="/path/to/geckodriver")

### Open URL

driver.get("https://example.com")

### Maximize Window

driver.maximize_window()

### Close the Current Browser Window

driver.close()

### Quit the WebDriver (Close All Windows)

driver.quit()

## 7. Common Actions

### Switch to a Different Window

driver.switch_to.window(driver.window_handles[1])

### Switch to an Iframe

driver.switch_to.frame("iframe-id")

### Switch Out of an Iframe

driver.switch_to.default_content()

### Scroll to Element

from selenium.webdriver.common.action_chains import ActionChains
actions = ActionChains(driver)
actions.move_to_element(element).perform()

### Handle Alerts (Accept)

alert = driver.switch_to.alert
alert.accept()

### Handle Alerts (Dismiss)

alert = driver.switch_to.alert
alert.dismiss()

### Take a Screenshot

driver.save_screenshot("screenshot.png")

## Notes
Always ensure you are using the correct WebDriver for your browser (ChromeDriver for Chrome, GeckoDriver for Firefox).
Use WebDriverWait and expected conditions to handle dynamic elements and avoid flaky tests.
Always remember to close or quit the browser after your test using driver.close() or driver.quit().
