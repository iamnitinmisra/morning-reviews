# Week 2, Day 3 Review - JavaScript 4



## Lecture Notes and Slides

- Notes: https://github.com/WLH-16/javascript-4
- Slides: https://slides.com/matias_perez/js-in-the-dom/#/

## Important Concepts to Review

1. The DOM

2. Events in JavaScript (event handlers and event listeners)
3. Accessing elements from the DOM in JavaScript (getElementById, getElementsByTagName, querySelector, querySelectorAll)
4. Editing element properties including the style object, className, classList, and innerText

## Review

1. Start by creating 3 files
  - index.html
  - styles.css
  - index.js

2. Connect all 3 files

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="styles.css" />
    <title>Document</title>
</head>
<body>
    
</body>
<script src="index.js"></script>
</html>
```

3. Place a console log at the top of your javascript file to demonstrate to students that the connection is working

4. Create a div with an id of fun-dip, this will be our first example. 


```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <link rel="stylesheet" href="style.css" />
    <title>Document</title>
  </head>
  <body>
    <div id="fun-dip"></div>
  </body>
  <script src="index.js"></script>
</html>
```


5. Give it the following styles:
```css
#fun-dip {
  width: 100px;
  height: 100px;
  background: aqua;
}
```

6. We want to write a function that will change the background color of fun-dip to #bada55 when we click it. Have the students try to get there initially. Final code should looks something like this:

```js
const funDip = document.getElementById('fun-dip')

funDip.addEventListener('click', e => {
  funDip.style.backgroundColor = '#bada55'
})
```

> Take plenty of time to review with them the pattern of adding event listeners as well as what an event is and what the event object is. These concepts will be very helpful moving into React.
 - 1. specify which id you are looking for
 - 2. add an eventListener of your choice of event
 - 3. specify a callback function to change the property you desire

7. Let's change the function to be more dynamic, we want to toggle between our two background colors when we click. The function should look something like this but it is broken:

```js
funDip.addEventListener('click', e => {
  if (funDip.style.backgroundColor === '#bada55') {
    funDip.style.backgroundColor = 'aqua'
  } else {
    funDip.style.backgroundColor = '#bada55'
  }
})
```
> NOTE: When you set the background color using a hex code, it will automatically convert to rgb values. 

this is the correct code
```js
funDip.addEventListener('click', e => {
  if (funDip.style.backgroundColor === 'rgb(186, 218, 85)') {
    funDip.style.backgroundColor = 'aqua'
  } else {
    funDip.style.backgroundColor = '#bada55'
  }
})
```


8. Let's also make our div grow when we click it:

```js
funDip.addEventListener('click', e => {
  funDip.style.height = '500px'
  funDip.style.width = '500px'

  if (funDip.style.backgroundColor === 'rgb(186, 218, 85)') {
    funDip.style.backgroundColor = 'aqua'
  } else {
    funDip.style.backgroundColor = '#bada55'
  }
})
```

- Finally let's demonstrate a couple of other events we have access to, mouseenter and mouseleave

```js
funDip.addEventListener('mouseenter', e => {
  funDip.style.backgroundColor = 'purple'
})

funDip.addEventListener('mouseleave', e => {
  funDip.style.backgroundColor = 'aqua'
})
```

- If you're able, you can also give an example of changing styles using classList

1. Create a div with a class of snickers and give it the following style, 

```css
.snickers {
  width: 300px;
  height: 100px;
  background: chocolate;
  color: white;
  font-size: 1.3rem;
  display: flex;
  justify-content: center;
  align-items: center;
}
```

2. also create an open class

```css
.open {
  width: 600px;
  height: 200px;
  font-size: 1.6rem;
}
```

3. Create a function to toggle the open class:

```js
const snickers = document.querySelector('.snickers')

snickers.addEventListener('click', handleOpen)

function handleOpen() {
  snickers.classList.toggle('open')
}
```

> Also, take this time to review querySelector vs getElementById
- They both have their use cases
- at a high level
  - use querySelector to select classes
  - use getElementById to select IDs

4. Finish up your snickers bar by setting the inner text of the div:

```js
function handleOpen() {
  snickers.classList.toggle('open')

  if (snickers.innerText !== 'SATISFIED') {
    snickers.innerText = 'SATISFIED'
  } else {
    snickers.innerText = `You're not you when you're hungry`
  }
}
```
