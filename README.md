# Practical Frontend

## Variables:

### Introduction to Variables in CSS:

As you create bigger and more complex websites, managing repeated colors, sizes, or fonts gets harder. Changing one value means updating many places.

**CSS variables** let you save these values as names (like `--main-color`) and reuse them throughout your CSS. Change the variable once, and it updates everywhere automatically!

They are very helpful for keeping code clean and consistent, and many developers use them to build modern websites.

### Using CSS Variables:

CSS variables, also called **custom properties**, let you save values under a name and reuse them throughout your CSS.

Variables are declared inside a selector (commonly `:root` so the variable works everywhere on the page, it is called global) using the syntax:

#### Basic Syntax:

```css
:root {
 --main-color: midnightblue;
 --padding: 16px;
}
```

#### Breakdown:

* `:root`: Declares a global root selector so that it can be accessed anywhere on the website, since it is defined as a global-scope selector.
* `--main-color`: CSS variable which stores a value of a particular color.
* `--padding`: CSS variable which stores a padding value in pixels.

#### Utilizing Variables:

To use the value stored in a variable, you must use the `var()` function:

```css
.button {
  background-color: var(--main-color);
  padding: var(--padding);
}
```

#### Example of Usage:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>How to declare a variable</title>
    <style>
        :root { /* Root selector with global scope variables */
            --bg-color: #4c87f5;
            --main-color: seagreen;
        }
        body {
            font-family: Arial, sans-serif;
            background: var(--bg-color);
            padding: 20px;
        }
        .movie {
            background: white;
            padding: 15px;
            margin-bottom: 15px;
            border-radius: 8px;
        }
        .movie h2 {
            margin: 0 0 10px;
        }
        .movie p {
            margin: 0 0 10px;
        }
        button {
            color: black;
            border: none;
            padding: 8px 12px;
            border-radius: 4px;
            cursor: pointer;
            /* Sets the background color to all buttons to seagreen */
            background-color: var(--main-color);
        }
    </style>
</head>
<body>
    <h1>Today's Movies</h1>
    <div class="movie">
        <h2>Ocean Whispers</h2>
        <p>A sailor discovers a hidden island and the secrets of the sea.</p>
        <button>Buy Ticket</button>
    </div>
    
    <div class="movie">
        <h2>Midnight Chase</h2>
        <p>A detective races against the clock to stop a mysterious heist.</p>
        <button>Buy Ticket</button>
    </div>
    
    <div class="movie">
        <h2>Starlight Bakery</h2>
        <p>A warm comedy about friendship and following your dreams.</p>
        <button>Buy Ticket</button>
</div>
</body>
</html>
```

##### Result:

![CSS Variables](Assets/Photos/Declaring%20Variables.jpg)