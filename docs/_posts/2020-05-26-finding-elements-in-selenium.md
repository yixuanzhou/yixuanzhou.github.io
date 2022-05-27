# Finding elements in Selenium
## CSS Selector to find elements
**Syntax: tag[attribute=“value”]**
IMPORTANT: NEVER USE CSS SELECTOR TO FIND TWO MATCHING NODES
1. “#” -> id
2. “.” -> class
* ex1. Find an input element with id=“displayed-text”
“input[id=displayed-text]”
“#displayed-text”
“input#displayed-text”
* ex2. Find an input element with class=“displayed-text” 
“input[class=displayed-class]”
“.displayed-class”
“input.displayed-class”
* ex3. Find an input element with class=“inputs displayed-text”
“.inputs.displayed-text” (two classes, this is called appending class)

### Using wildcards in CSS Selectors
1. “^” -> Represents the starting text
2. “$” -> Represents the ending text
3. “*” -> Represents the text contained
**Syntax: tag[attribute<special character>=‘value’]**
Say there exists an input element with class=“inputs displayed-text”
* ex1. Find an element with class starts from “inputs”
“input[class^=‘inputs’]”
* ex2. Find an element with class ends with “displayed-text”
“input[class$=‘displayed-text’]”
* ex3. Find an element with class contains “Enter” anywhere
“input[class*=‘Enter’]”

### Finding children using CSS Selectors
“>” -> Navigates to children elements
* ex. Find table element with id=“product” under “fieldset” parent
“fieldset>table”
“fieldset>#product”

## XPATH to find elements
Not all elements have a static id, unique name or unique link text. For those elements we can use xpath to locate them.
**Syntax: tag[@attribute=‘value’]**
**’/‘ single slash** signifies to look for the element immediately inside the parent element.
**’‘ double slash** signifies to look for any child or nested-child element inside the parent element.

1. Absolute Xpath:
Not recommended, if there is a change in the middle of the path, the whole xpath will become invalid.

2. Relative Xpath:

### Using “Text” property to build Xpath
div[@class=‘homepage’]a[text()=‘Login’]

### Build Xpath using “contains” keyword
**tag[contains(attribute, ‘value’)]**
* ex1. Find anchor tag which has “Login” as its text
“div[@id=‘navbar’]a[contains(text(), ‘Login’)]”
* ex2. Find anchor tag which has ‘navbar-link’ in class and ‘sign_in’ in href
“div[@id=‘navbar’]a[contains(@class, ‘navbar-link’) and contains(@href, ‘sign_in’)]”

### Using “starts-with” to find elements
* ex. Find all anchor tags which have ‘navbar-link’ in class
 “div[@id=‘navbar’]a[starts-with(@class, ‘navbar-link’)]”

### Find parent and sibling nodes
* Parent: xpath-to-some-elementparent::<tag>
* Preceding sibling: xpath-to-some-elementpreceding-sibling::<tag>
* Following sibling: xpath-to-some-elementfollowing-sibling::<tag> 

#selenium