# Sass-BEM-Responsive

## Sass Partials
* Sass keeps the CSS code DRY (Don't Repeat Yourself). One way to write DRY code is to keep related code in separate files.
 1. Create in folder SCSS folder global. Inside of this folder create file _boilerplate.scss
 - add basic style:
```typescript
html {
  box-sizing: border-box;
  font-size: 100%;
}

body {
  margin: 0;
  padding: 0;
}

*, *::before, *::after {
  box-sizing: inherit;
}
```
- The inherit keyword specifies that a property should inherit its value from its parent element.

  The inherit keyword can be used for any CSS property, and on any HTML element.

2. Create _typography.scss file.Add basic style for h1, h2, h3 p tags and links

```typescript

h1, h2, h3 {
  font-weight: 700;
  line-height: 1.1;
  margin-top: 0;
}

p {
  margin-top: 0;
}

a, a:visited, a:active {
  text-decoration: none;
}
```
3. Create file _index.scss. Import boilerplate, typography files inside of _index.scss
```typescript
@forward "boilerplate";
@forward "typography";
```
* The @forward rule loads a Sass stylesheet and makes its mixins, functions, and variables available when your stylesheet is loaded with the @use rule. It makes it possible to organize Sass libraries across many files, while allowing their users to load a single entrypoint file.

3. Forward all styles to the style.scss and use them
```typescript
@forward "globals";
```

## Variables
* Variables are a way to store information that you can re-use later.

With Sass, you can store information in variables, like:

strings
numbers,
colors,
booleans,
lists,
nulls.
1. Create _color.scss file and update _index.scss
2. Make variables.. 

````typescript
:root {
  --background-color: hsl(0, 0%, 11%);
  --text-color: hsl(0, 0%, 100%);
}
````
3. Use variables
```typescript
body {
  margin: 0;
  padding: 0;
  font-family: Arial, Helvetica, sans-serif;
  background-color: var(--background-color);
  color: var(--text-color);
}
```
# Using Google Font
1. Create new folder call util, inside create _fonts.scss and _index.scss
* Add font links to index.html file.
2. In _fonts.scss create variable and put font name.
````typescript
$font: 'Open Sans', sans-serif;
````
3. Forward variable to util->_index.scss file
```typescript
@forward "fonts";
```
4. To use font in _boilerplate.scss, importing 
```typescript
@use '../util' as u;
```
and using in body tag.
```typescript
body {
  margin: 0;
  padding: 0;
  font-family: u.$font;
  background-color: var(--background-color);
  color: var(--text-color);
}
```

### SASS AND BEM

1. BEM -  Block-Element-Modifier
* [Link text Here](https://sparkbox.com/foundry/bem_by_example)

````typescript
<div class="grid">
    <main class="grid__main">
        <h1>Hello</h1>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Alias assumenda aut distinctio, dolorum
            exercitationem
            facilis laborum minima molestias perspiciatis, provident repudiandae, vero. Nesciunt nihil sequi totam
            veniam!
            Adipisci aliquid architecto at deleniti, repellat vel vero. Dolore enim exercitationem fuga in, labore
            nostrum
            perferendis quae quod temporibus velit. Accusantium aspernatur aut commodi, culpa debitis delectus dolor
            eius
            enim eos esse, expedita facere facilis fugit hic illo incidunt ipsam maxime nam neque, nihil praesentium
            quia
            reprehenderit similique sint tempore totam veritatis voluptates!</p>
    </main>
    <aside class="grid__sidebar">
        <h2>More info</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Atque ducimus ea eligendi fuga inventore laboriosam
            maxime, possimus! Consequatur dignissimos dolore est expedita explicabo hic id ipsam, itaque officiis optio
            quidem rem saepe sequi, sit sunt! Consequatur impedit possimus quam recusandae unde. Accusantium deleniti
            dignissimos dolorem, dolores earum ipsa itaque iure necessitatibus odio perferendis placeat quam, quasi
            reprehenderit saepe velit vitae?</p>
    </aside>
</div>
````

## Responsive Design
- Use media queries
Set rule for screen min-width: 900px;
```typescript
@media (min-width: 900px) {
  grid-template-columns: 2fr 1fr;
}
```