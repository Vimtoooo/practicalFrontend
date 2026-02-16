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

### Local Variables:

You may have noticed we often use `:root` to declare variables, this is because `:root` is **global**. Variables defined here apply to the whole HTML page (as we mentioned before).

But sometimes you want variables that only affect certain parts of the page. For example, imagine building an online shop with many product cards, you can create variables inside a `.card` class to style just those cards without affecting other elements.

#### Basic Syntax:

```css
.card {
  --card-color: orchid;
  background-color: var(--card-color);
}
```

This way, the variable only works inside `.card` elements (class), giving you more control over specific areas.

#### Example of Usage:

```html
<html>
<head>
    <title>Local Variables</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400..900;1,400..900&display=swap" rel="stylesheet">    <style>
      /* Global variable for body background */
      :root {
        --body-bg: #000f26;
        --font-family: "Playfair Display", serif;
      }
    
      body {
        background-color: var(--body-bg);
        font-family: var(--font-family);
        padding: 20px;
        display: flex;
        gap: 20px;
        justify-content: center;
      }
    
      /* Card styles */
      .card {
        --card-bg: white;
        --card-accent: coral;
        background-color: var(--card-bg);
        border-radius: 10px;
        padding: 15px;
        width: 250px;
        text-align: center;
        box-shadow: 0 4px 8px rgba(0,0,0,0.1);
      }
    
      .card h3 {
        color: var(--card-accent);
        margin-top: 0;
      }
    
      .card p {
        font-size: 0.9rem;
        color: #333;
      }
    
      .card button {
        border: none;
        background-color: var(--card-accent);
        color: #000f26;
        padding: 8px 12px;
        border-radius: 5px;
        cursor: pointer;
        font-weight: bold;
        margin-top: 10px;
        width: 100%;
      }
    
    </style>
    </head>
    <body>
    
    <div class="card">
      <h3>Classic Sneakers</h3>
      <p>Comfortable and stylish sneakers for everyday wear.</p>
      <button>Buy Now</button>
    </div>
    
    <div class="card special">
      <h3>Luxury Watch</h3>
      <p>Elegant watch with a unique design for special occasions.</p>
      <button>Buy Now</button>
    </div>
    
    <div class="card">
      <h3>Leather Backpack</h3>
      <p>Durable, spacious backpack made from premium leather.</p>
      <button>Buy Now</button>
    </div>
    
    </body>
</html>
```

##### Result:

![Local Variables](Assets/Photos/Local%20Variables.jpg)

### Recap - Variables:

Here is the recap on **variables**:

* **Declaring Variables**: Variables must be declared inside a selector (either inside a `:root` or a specific element/class/id `.nameOfClass`), with the syntax `--var-name: value;`:
    - `--var-name`: The variable name, that should always start with two dashes/hyphens.
    - `value`: The desired value that the variable will hold, this can represent any possible value in the CSS context.
* **Using Variables**: Manipulate with the `var()` function to effectively mention global or local-scope variables following the syntax `color: var(--color-var);`:
    - `color`: The `color` property used to add coloring to text.
    - `var(--color-var)`: The section which mentions the variable inside the `var()` function, this variable stores the desired value like `blue` or `pink`...

#### Example of a Webpage:

```html
<html>
<head>
  <title>CSS Variables Recap Challenge</title>
  <style>
    /* Global Variables */
    :root {
      --main-bg: #fdf00f;
      --main-font: 'Segoe UI', serif;
    }

    body {
      margin: 0;
      padding: 0;
      background-color: var(--main-bg);
      font-family: var(--main-font);
    }

    header {
      background-color: var(--primary-color);
      color: white;
      padding: 20px;
      text-align: center;
    }

    header h1 {
      margin: 0;
      font-size: 2rem;
    }

    header p {
      margin: 5px 0 0;
      font-size: 1rem;
      opacity: 0.9;
    }

    main {
      padding: 20px;
      display: grid;
      gap: 20px;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    }
    .hero {
        background: url('https://upload.wikimedia.org/wikipedia/commons/c/c0/Healthy_Food_-_Colourful_Fruit_and_Veg_-_50191699151.jpg') center/cover no-repeat;
        color: white;
        text-align: center;
        padding: 30px 20px 50px 20px;
        border-radius: 10px;
        margin: 10px;
        }

    .hero button {
        background-color: var(--primary-color);
        padding: 10px 20px;
        border: none;
        border-radius: 5px;
        font-weight: bold;
        cursor: pointer;
        color: white;
    }

    .card {
      /* Local Variable for Card */
      --card-accent: tomato;

      background: white;
      border-radius: 10px;
      padding: 15px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }

    .card h2 {
      margin: 0 0 10px;
      color: var(--card-accent);
    }

    .card p {
      font-size: 0.9rem;
      color: #333;
    }

    .card button {
      background-color: var(--card-accent);
      margin-top: 10px;
      border: none;
      padding: 8px 12px;
      color: black;
      border-radius: 5px;
      font-weight: bold;
      cursor: pointer;
    }

    footer {
      background-color: #eee;
      text-align: center;
      padding: 15px;
      font-size: 0.85rem;
      margin-top: 20px;
    }
  </style>
</head>
<body>

  <header>
    <h1>Healthy Recipes</h1>
    <p>Fresh, tasty, and colorful meals you can make at home</p>
  </header>
<section class="hero">
  <div class="hero-content">
    <h2>Eat Healthy, Live Happy</h2>
    <button>Explore Recipes</button>
  </div>
</section>
  <main>
    <div class="card">
      <h2>Avocado Salad</h2>
      <p>A healthy salad with fresh avocado, tomatoes, and herbs.</p>
      <button>Read Recipe</button>
    </div>

    <div class="card special">
      <h2>Berry Smoothie</h2>
      <p>Refreshing smoothie with blueberries, strawberries, and yogurt.</p>
      <button>Read Recipe</button>
    </div>

    <div class="card">
      <h2>Quinoa Bowl</h2>
      <p>Nutritious quinoa with roasted vegetables and chickpeas.</p>
      <button>Read Recipe</button>
    </div>
  </main>

  <footer>
    &copy; 2025 Healthy Recipes. All rights reserved.
  </footer>

</body>
</html>
```

##### Result:

![Recap - Variables](Assets/Photos/Recap%20-%20Variables.jpg)

## Mobile-First Strategy:

### What "mobile-first" means:

**Mobile-first** is a design strategy where you build your website for mobile devices first, then progressively enhance it for larger screens.

The main idea is that most users now brows th wb on their phons, so starting small ensures your site works wll for the majority of visitors.

#### Starting Point for Writing Mobile Styles:

The first step is to start writing mobile styles:

```css
body {
  font-size: 16px;
  padding: 10px;
}
```

Then you would use **media queries** to adapt your design for larger screens:

```css
/* Styles for devices wider than 768px */
@media (min-width: 768px) {
  body {
    font-size: 18px;
    padding: 20px;
  }
}
```

This approach ensures your site works well on small screens first, then enhances the experience for users on larger devices.

#### Example of Usage:

```html
<!DOCTYPE html>
<html>
<head>
  <title>What “mobile-first” means</title>
  <style>
    /* Mobile-first Approach */
    .menu {
      display: flex;
      flex-direction: column;
      width: auto;
      max-height: 250px;
      list-style: none;
      padding: 0;
      margin: 0;
    }
    
    .menu li {
      margin-bottom: 10px;
      background-color: rgb(25, 220, 10);
      margin-right: 10px;
      padding: 10px;
    }
    
    .menu a {
      display: block;
      text-align: center;
      text-decoration: none;
      color: black;
    }
    
    /* Bigger screen styles */
    @media (min-width: 768px) {
      .menu {
        display: flex;
        flex-direction: row;
        padding: 3px;
      }
      
      .menu li {
      
      }
    }
  </style>
</head>
<body>
  <nav>
    <ul class="menu">
      <li><a href="#">Home</a></li>
      <li><a href="#">About</a></li>
      <li><a href="#">Services</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
  </nav>
</body>
</html>
```

##### Result:

![A mobile-first strategy](Assets/Videos/NVIDIA_Overlay_2Kikjrue5p.gif)

### Mobile-First Typography:

**Mobile-first typography** means starting with text styles that are easy to read on small screens, then adjusting them for larger screens with media queries.

We use it because mobile users need **clear, legible fonts** that work well on small displays. If text is too small, et becomes hard to read, and if it's too large on desktop, it can look awkward.

#### Setting up the Mobile-First Typography:

Set up your bas font-size for mobile:

```css
/* Mobile-first styles */
body {
  font-size: 16px; /* base size for mobile */
}

h1 {
  font-size: 1.5rem;
}
```

Then, utilize media queries to adjust for larger screens:

```css
/* Larger screens */
@media (min-width: 768px) {
  body {
    font-size: 18px;
  }
  
  h1 {
    font-size: 2rem;
  }
}
```

#### Example of Usage:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Mobile-First Typography</title>
  <style>
    /* ===== Mobile-First Styles ===== */
    :root {
      --base-font-size: 16px;
      --base-heading-font-size: 24px;
    }

    body {
      font-size: var(--base-font-size);
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      line-height: 1.5;
      background-color: #f0f8ff;
      color: #333;
    }

    header {
      background: url('https://upload.wikimedia.org/wikipedia/commons/a/af/Female_polar_bear_%28Ursus_maritimus%29_with_cub%2C_Svalbard.jpg')
                  center/cover no-repeat;
      color: white;
      text-align: center;
      padding: 50px 20px;
    }

    header h1 {
      font-size: var(--base-heading-font-size);
      margin: 0;
    }

    .subtitle {
      margin-top: 10px;
      font-size: 1rem;
      opacity: 0.9;
    }

    main {
      padding: 20px;
    }

    h2 {
      color: #2c6e91;
      font-size: 1.25rem;
    }

    p { font-size: var(--base-font-size); }

    ul {
      padding-left: 20px;
    }

    li {
      margin-bottom: 10px;
    }

    footer {
      background-color: #2c6e91;
      color: white;
      text-align: center;
      padding: 15px;
      font-size: 0.9rem;
    }

    /* ===== Larger Screens ===== */
    @media (min-width: 768px) {
      header h1 { font-size: 36px; }
      p { font-size: 20px; }
    }

  </style>
</head>
<body>
  <header>
    <h1>Polar Bears – Kings of the Arctic</h1>
    <p class="subtitle">Discover the life of the world's largest land carnivore</p>
  </header>

  <main>
    <section>
      <h2>About Polar Bears</h2>
      <p>
        Polar bears are magnificent animals that live in the Arctic region. 
        They are excellent swimmers, using their large paws to paddle through icy waters 
        in search of seals, their main source of food. These bears have thick layers of 
        fat and dense fur to keep them warm in extreme cold.
      </p>
    </section>

    <section>
      <h2>Interesting Facts</h2>
      <ul>
        <li>Polar bears can weigh up to 700 kg (1,500 lbs).</li>
        <li>They have black skin under their white fur to absorb heat.</li>
        <li>Polar bears can swim for days without resting.</li>
        <li>They are listed as vulnerable due to climate change.</li>
      </ul>
    </section>

    <section>
      <h2>Protecting Polar Bears</h2>
      <p>
        Climate change and melting sea ice threaten polar bear habitats. 
        Protecting these amazing creatures requires global efforts to 
        reduce greenhouse gas emissions and preserve their Arctic environment.
      </p>
    </section>
  </main>

  <footer>
    <p>&copy; 2025 Arctic Wildlife. All rights reserved.</p>
  </footer>
</body>
</html>
```

##### Result:

![Mobile-first Typography](Assets/Videos/chrome_h1tzMIaBIl.gif)