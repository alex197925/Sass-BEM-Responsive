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