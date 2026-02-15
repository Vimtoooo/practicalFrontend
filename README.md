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

### Variables for Design Tokens:

Now that we know how to declare and use CSS variables, let's see how they help organize your design.

**Design tokens** are special CSS variables that store your site's main colors, fonts, and other style values.

B using design tokens, you keep your styles consistent and easy to update - just change the token once, and the whole site reflects the change!

#### Basic Syntax:

Her is how to create CSS variables for you design tokens:

```css
:root {
  /* Colors */
  --primary-color: #3498db;
  --secondary-color: #2ecc71;
  
  /* Spacing */
  --spacing-small: 8px;
  --spacing-medium: 16px;
  --spacing-large: 24px;
  
  /* Typography */
  --font-size-small: 12px;
  --font-size-medium: 16px;
  --font-size-large: 24px;
}
```

And right here, we apply these design tokens to your elements:

```css
.button {
  background-color: var(--primary-color);
  padding: var(--spacing-small) var(--spacing-medium);
  font-size: var(--font-size-medium);
}

.card {
  border: 1px solid var(--secondary-color);
  margin: var(--spacing-medium);
  padding: var(--spacing-large);
}
```

#### Why use Design Tokens?

Using design tokens ensures consistency acros your website and makes updates easier, making the addition of new features and other variables simplified. But as the design token becomes robust, always keep variables organized based on specific sections, global/main styles, content spacing and so on.

#### Example of Usage:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Design Tokens</title>
    <style>
      /* Design tokens: colors, fonts, spacing */
      :root {
        --color-primary: #27ae60;
        --secondary-color: #f39c12;
        --color-text: #2c3e50;      
        --font-base: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        --spacing-small: 8px;
        --spacing-medium: 16px;
        --spacing-large: 24px;
        --border-radius: 8px;
        --bg-light: #e8f5e9;          
      }
    
      body {
        font-family: var(--font-base);
        color: var(--color-text);
        background: var(--bg-light);
        margin: 0;
        padding: var(--spacing-large);
        line-height: 1.5;
      }
    
      header {
        text-align: center;
        margin-bottom: var(--spacing-large);
      }
    
      header h1 {
        color: var(--color-primary);
        margin-bottom: 0.2em;
      }
    
      header p {
        font-size: 1.1rem;
        color: #4a6a4a;
      }
    
      section {
        max-width: 700px;
        margin: 0 auto;
        padding: var(--spacing-medium);
        background: white;
        border-radius: var(--border-radius);
        box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      }
    
      h2 {
        margin-top: 0;
        color: var(--secondary-color);
      }
    
      article {
        margin-bottom: var(--spacing-large);
      }
    
      article:last-child {
        margin-bottom: 0;
      }
    
      .btn {
        display: inline-block;
        background-color: var(--color-primary);
        color: white;
        border: none;
        padding: var(--spacing-small) var(--spacing-small);
        border-radius: var(--border-radius);
        font-weight: 600;
        cursor: pointer;
        transition: background-color 0.3s ease;
        text-decoration: none;
      }
    
      .btn:hover {
        background-color: #1e8449;
      }
    </style>
    </head>
    <body>
    
    <header>
      <h1>Eat Healthy, Feel Great!</h1>
      <p>Your guide to nutritious and delicious foods.</p>
    </header>
    
    <section>
      <article>
        <h2>Avocados</h2>
        <p>Rich in healthy fats and fiber, avocados support heart health and keep you full longer.</p>
        <button class="btn">Learn More</button>
      </article>

      <article>
        <h2>Quinoa</h2>
        <p>A complete protein source, quinoa is great for vegetarians and provides essential amino acids.</p>
        <button class="btn">Learn More</button>
      </article>

      <article>
        <h2>Blueberries</h2>
        <p>Packed with antioxidants and vitamins, blueberries promote brain health and fight inflammation.</p>
        <button class="btn">Learn More</button>
      </article>
    </section>
</body>
</html>
```

##### Result:

![Variables for Design Tokens](Assets/Photos/Design%20Tokens.jpg)