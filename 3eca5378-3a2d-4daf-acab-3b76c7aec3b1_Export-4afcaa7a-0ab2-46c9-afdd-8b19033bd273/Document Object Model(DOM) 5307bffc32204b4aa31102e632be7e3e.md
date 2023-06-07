# Document Object Model(DOM)

HTML document is structured as a JavaScript Object. Every HTML element has a different properties which can help to manipulate it. It is possible to get, create, append or remove HTML elements using JavaScript. Selecting HTML element using JavaScript is similar to selecting using CSS. To select an HTML element, we use tag name, id, class name or other attributes.

### **Getting Element**

We can access already created element or elements using JavaScript. To access or get elements we use different methods. The code below has four *h1* elements. Let us see the different methods to access the *h1* elements.

```flow
<!DOCTYPE html>
  <html lang="en">
    <head>
      <title>Document Object Model</title>
    </head>
    <body>

     <h1 class='title' id='first-title'>First Title</h1>
     <h1 class='title' id='second-title'>Second Title</h1>
     <h1 class='title' id='third-title'>Third Title</h1>
     <h1></h1>

    </body>
  </html>
```

### **Getting elements by tag name**

Takes a tag name as a string parameter and this method returns an HTML Collection object. 

An HTML Collection is an array-like object of HTML elements. The length property provides the size of the collection. Whenever we use this method we access the individual elements using the index or after loop through each individual item.

 An HTML Collection does not support all array methods therefore we should use regular for loop instead of for each.

```flow
// syntax
document.getElementsByTagName('tagname')

const allTitles = document.getElementsByTagName('h1')

console.log(allTitles) //HTMLCollections
console.log(allTitles.length) // 4

for (let i = 0; i < allTitles.length; i++) {
  console.log(allTitles[i]) // prints each elements in the HTMLCollection
}
```

### **Getting elements by class name**

The method returns an HTML Collection object. An HTML Collection is an array-like list of HTML elements. The length property provides the size of the collection. It is possible to loop through all the HTML Collection elements. 

```flow
//syntax
document.getElementsByClassName('classname')

const allTitles = document.getElementsByClassName('title')

console.log(allTitles) //HTMLCollections
console.log(allTitles.length) // 4

for (let i = 0; i < allTitles.length; i++) {
  console.log(allTitles[i]) // prints each elements in the HTMLCollection
}
```

### **Getting an element by id**

Targets a single HTML element. We pass the id without # as an argument.

```flow
//syntax
document.getElementById('id')

let firstTitle = document.getElementById('first-title')
console.log(firstTitle) // <h1>First Title</h1>
```

### **Getting elements by using query Selector methods**

The *document query Selector* method can select HTML or HTML elements by tag name, id, or class name.

***query Selector***: can be used to select HTML elements by its tag name, id, or class. If the tag name is used it selects only the first element.

```flow
let firstTitle = document.querySelector('h1') // select the first available h1 element
let firstTitle = document.querySelector('#first-title') // select id with first-title
let firstTitle = document.querySelector('.title') // select the first available element with class title
```

***query Selector All***: can be used to select HTML elements by their tag name or class. It returns a node List, an array-like object that supports array methods. We can use ***for loop*** or ***for Each*** to loop through each node List elements.

```flow
const allTitles = document.querySelectorAll('h1') # selects all the available h1 elements in the page

console.log(allTitles.length) // 4
for (let i = 0; i < allTitles.length; i++) {
  console.log(allTitles[i])
}

allTitles.forEach(title => console.log(title))
const allTitles = document.querySelectorAll('.title') // the same goes for selecting using class
```

### **Adding attribute**

An attribute is added in the opening tag of HTML which gives additional information about the element. Common HTML attributes: id, class, src, style, href, disabled, title, alt. Lets add id and class for the fourth title.

```flow
const titles = document.querySelectorAll('h1')
titles[3].className = 'title'
titles[3].id = 'fourth-title'
```

### Adding attribute using set Attribute

The ***set Attribute()*** method set any html attribute. It takes two parameters the type of the attribute and the name of the attribute. Let's add class and id attributes for the fourth title.

```flow
const titles = document.querySelectorAll('h1')
titles[3].setAttribute('class', 'title')
titles[3].setAttribute('id', 'fourth-title')
```

### Adding attribute without set Attribute

We can use a normal object setting method to set an attribute but this can not work for all elements. Some attributes are DOM object property and they can be set directly.

```flow
//another way to setting an attribute
titles[3].className = 'title'
titles[3].id = 'fourth-title'
```

### Adding class using class List

The class list method is a good method to append additional classes. It does not override the original class if a class exists rather it adds an additional class for the element.

```flow
//another way to setting an attribute: append the class, doesn't over ride
titles[3].classList.add('title', 'header-title')
```

### Removing class using remove

Similar to adding we can also remove class from an element. We can remove a specific class from an element.

```flow
//another way to setting an attribute: append the class, doesn't over ride
titles[3].classList.remove('title', 'header-title')
```

### Adding Text to HTML element

An HTML is a build block of an opening tag, a closing tag and a text content. We can add a text content using the property *text Content* or *inner HTML.

### Adding Text content using text Content

The *text Content* property is used to add text to an HTML element.

```flow
const titles = document.querySelectorAll('h1')
titles[3].textContent = 'Fourth Title'
```

### Adding Text Content using inner HTML

Most people get confused between *text Content* and *inner HTML*. *text Content* is meant to add text to an HTML element, however inner HTML can add a text or HTML element or elements as a child.

### Text Content

We assign *text Content* HTML object property to a text

```flow
`const titles = document.querySelectorAll('h1')
titles[3].textContent = 'Fourth Title'`
```

### Inner HTML

We use inner HTML property when we like to replace or a completely new children’s content to a parent element. It value we assign is going to be a string of HTML elements.

```flow
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>JavaScript for Everyone:DOM</title>
  </head>
  <body>
    <div class="wrapper">
        <h1>Asabeneh Yetayeh challenges in 2020</h1>
        <h2>30DaysOfJavaScript Challenge</h2>
        <ul></ul>
    </div>
    <script>
    const lists = `
    <li>30DaysOfPython Challenge Done</li>
            <li>30DaysOfJavaScript Challenge Ongoing</li>
            <li>30DaysOfReact Challenge Coming</li>
            <li>30DaysOfFullStack Challenge Coming</li>
            <li>30DaysOfDataAnalysis Challenge Coming</li>
            <li>30DaysOfReactNative Challenge Coming</li>
            <li>30DaysOfMachineLearning Challenge Coming</li>`
  const ul = document.querySelector('ul')
  ul.innerHTML = lists
    </script>
  </body>
</html>
```

### Adding style

### Adding Style Color

Let us add some style to our titles. If the element has even index we give it green color else red.

```flow
const titles = document.querySelectorAll('h1')
titles.forEach((title, i) => {
  title.style.fontSize = '24px' // all titles will have 24px font size
  if (i % 2 === 0) {
    title.style.color = 'green'
  } else {
    title.style.color = 'red'
  }
})
```

### Adding Style Background Color

Let us add some style to our titles. If the element has even index we give it green color else red.

```flow
const titles = document.querySelectorAll('h1')
titles.forEach((title, i) => {
  title.style.fontSize = '24px' // all titles will have 24px font size
  if (i % 2 === 0) {
    title.style.backgroundColor = 'green'
  } else {
    title.style.backgroundColor = 'red'
  }
})
```

### Adding Style Font Size

Let us add some style to our titles. If the element has even index we give it 20px else 30px

```flow
const titles = document.querySelectorAll('h1')
titles.forEach((title, i) => {
  title.style.fontSize = '24px' // all titles will have 24px font size
  if (i % 2 === 0) {
    title.style.fontSize = '20px'
  } else {
    title.style.fontSize = '30px'
  }
})
```

As you have noticed, the properties of CSS when we use it in JavaScript are going to be a camel case. The following CSS properties change from background color to background color, font size to font size, font family to font Family, and margin-bottom to margin Bottom.

### Creating an Element

To create an HTML element we use a tag name. Creating an HTML element using JavaScript is very simple and straightforward. We use the method *document.createElement()*. The method takes an HTML element tag name as a string parameter.

```flow
// syntax
document.createElement('tagname')

<!DOCTYPE html>
<html>

<head>
    <title>Document Object Model:30 Days Of JavaScript</title>
</head>

<body>

    <script>
        let title = document.createElement('h1')
        title.className = 'title'
        title.style.fontSize = '24px'
        title.textContent = 'Creating HTML element DOM Day 2'

        console.log(title)
    </script>
</body>

</html>
```

### Creating elements

To create multiple elements we should use loop. Using loop we can create as many HTML elements as we want. After we create the element we can assign value to the different properties of the HTML object.

```flow
<!DOCTYPE html>
<html>

<head>
    <title>Document Object Model:30 Days Of JavaScript</title>
</head>

<body>

    <script>
        let title
        for (let i = 0; i < 3; i++) {
            title = document.createElement('h1')
            title.className = 'title'
            title.style.fontSize = '24px'
            title.textContent = i
            console.log(title)
        }
    </script>
</body>

</html>
```

### Appending child to a parent element

To see a created element on the HTML document we should append it to the parent as a child element. We can access the HTML document body using *document.body*. The *document.body* support the *appendChild()* method. See the example below.

```flow
<!DOCTYPE html>
<html>

<head>
    <title>Document Object Model:30 Days Of JavaScript</title>
</head>

<body>

    <script>
        // creating multiple elements and appending to parent element
        let title
        for (let i = 0; i < 3; i++) {
            title = document.createElement('h1')
            title.className = 'title'
            title.style.fontSize = '24px'
            title.textContent = i
            document.body.appendChild(title)
        }
    </script>
</body>
</html>
```

### Removing a child element from a parent node

After creating an HTML, we may want to remove element or elements and we can use the *removeChild()* method.

```flow
<!DOCTYPE html>
<html>

<head>
    <title>Document Object Model:30 Days Of JavaScript</title>
</head>

<body>
    <h1>Removing child Node</h1>
    <h2>Asabeneh Yetayeh challenges in 2020</h1>
    <ul>
        <li>30DaysOfPython Challenge Done</li>
        <li>30DaysOfJavaScript Challenge Done</li>
        <li>30DaysOfReact Challenge Coming</li>
        <li>30DaysOfFullStack Challenge Coming</li>
        <li>30DaysOfDataAnalysis Challenge Coming</li>
        <li>30DaysOfReactNative Challenge Coming</li>
        <li>30DaysOfMachineLearning Challenge Coming</li>
    </ul>

    <script>
        const ul = document.querySelector('ul')
        const lists = document.querySelectorAll('li')
        for (const list of lists) {
            ul.removeChild(list)

        }
    </script>
</body>

</html>
```