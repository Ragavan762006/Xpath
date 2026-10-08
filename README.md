rom selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import Select
import time

# -----------------------------------------
# Start Chrome
# -----------------------------------------

driver = webdriver.Chrome()

# TC01 - Open registration/form page
driver.get("https://www.selenium.dev/selenium/web/web-form.html")

driver.maximize_window()

# -----------------------------------------
# TC02 - Locate Text Input
# Attribute XPath
# -----------------------------------------

text_input = driver.find_element(
    By.XPATH,
    "//input[@name='my-text']"
)

text_input.send_keys("Prashanth")
time.sleep(10)


# -----------------------------------------
# TC03 - Enter Password
# Attribute XPath
# -----------------------------------------

password = driver.find_element(
    By.XPATH,
    "//input[@name='my-password']"
)

password.send_keys("prashanth@123")
time.sleep(10)


# -----------------------------------------
# TC04 - Locate Submit
# text()
# -----------------------------------------

submit = driver.find_element(
    By.XPATH,
    "//button[text()='Submit']"
)

print("Submit button found")
time.sleep(10)

# -----------------------------------------
# TC05 - Locate textbox dynamically
# contains()
# -----------------------------------------

text_box = driver.find_element(
    By.XPATH,
    "//input[contains(@name,'my-text')]"
)

print("Textbox found using contains()")
time.sleep(10)


# -----------------------------------------
# TC06 - Locate element with prefix
# starts-with()
# -----------------------------------------

text_box = driver.find_element(
    By.XPATH,
    "//input[starts-with(@name,'my-')]"
)

print("Element found using starts-with()")
time.sleep(10)


# -----------------------------------------
# TC07 - Two attributes
# and
# -----------------------------------------

password_box = driver.find_element(
    By.XPATH,
    "//input[@type='password' and @name='my-password']"
)

print("Password found using AND")
time.sleep(10)


# -----------------------------------------
# TC08 - Alternatives
# or
# -----------------------------------------

text_box = driver.find_element(
    By.XPATH,
    "//input[@name='my-text' or @type='text']"
)

print("Element found using OR")
time.sleep(10)


# -----------------------------------------
# TC09 - Find parent
# -----------------------------------------

parent = driver.find_element(
    By.XPATH,
    "//input[@name='my-text']/parent::*"
)

print("Parent element found")
time.sleep(10)


# -----------------------------------------
# TC10 - Find form using ancestor
# -----------------------------------------

form = driver.find_element(
    By.XPATH,
    "//input[@name='my-text']/ancestor::form"
)

print("Form found using ancestor")
time.sleep(10)


# -----------------------------------------
# TC11 - Find child inputs
# -----------------------------------------

child_inputs = form.find_elements(
    By.XPATH,
    ".//child::input"
)

print("Child input count:", len(child_inputs))
time.sleep(10)


# -----------------------------------------
# TC12 - Find next element
# following
# -----------------------------------------

next_element = driver.find_element(
    By.XPATH,
    "//input[@name='my-text']/following::input[1]"
)

print("Following element found")
time.sleep(10)


# -----------------------------------------
# TC13 - Find Checkbox
# Attribute + XPath
# -----------------------------------------

checkbox = driver.find_element(
    By.XPATH,
    "//input[@type='checkbox']"
)

checkbox.click()

print("Checkbox selected")
time.sleep(10)


# -----------------------------------------
# TC14 - Find Radio Button
# Attribute + XPath
# -----------------------------------------

radio = driver.find_element(
    By.XPATH,
    "//input[@type='radio']"
)

radio.click()

print("Radio button selected")
time.sleep(10)


# -----------------------------------------
# TC15 - Select Dropdown
# XPath + Select
# -----------------------------------------

dropdown = driver.find_element(
    By.XPATH,
    "//select[@name='my-select']"
)

select = Select(dropdown)

select.select_by_visible_text("Two")

print("Dropdown selected")
time.sleep(10)

# -----------------------------------------
# TC16 - Find second textbox
# XPath index
# -----------------------------------------

second_textbox = driver.find_element(
    By.XPATH,
    "(//input[@type='text'])[2]"
)

print("Second textbox found")
time.sleep(10)


# -----------------------------------------
# TC18 - Find all input fields
# find_elements()
# -----------------------------------------

all_inputs = driver.find_elements(
    By.XPATH,
    "//input"
)

print("Total input fields:", len(all_inputs))
time.sleep(10)

# -----------------------------------------
# TC19 - Find dynamic element
# contains()
# -----------------------------------------

dynamic_element = driver.find_element(
    By.XPATH,
    "//input[contains(@name,'my-')]"
)

print("Dynamic element found")
time.sleep(10)

# -----------------------------------------
# TC20 - Complete form
# -----------------------------------------

print("Completing form...")

# Text
text_input.clear()
text_input.send_keys("Prashanth")

# Password
password.clear()
password.send_keys("Prashanth@123")

# Checkbox
if not checkbox.is_selected():
    checkbox.click()

# Radio
if not radio.is_selected():
    radio.click()

# Dropdown
select.select_by_visible_text("Two")

# Submit
submit.click()

print("Form submitted successfully!")

time.sleep(30)

driver.quit()
