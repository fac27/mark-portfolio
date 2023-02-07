![image](https://user-images.githubusercontent.com/32879360/217068775-1f55fa60-5146-4d50-ad08-32dcf8d5a3ba.png)

## 1. Structure a site using semantic HTML to aid accessibility
This project involved using semantic HTML elements to structure the site and take advantage of default browser behaviour as well as accessibility tools.
```html
  <main class="stack-medium width-medium center">
        <h1>CarlMarks</h1>
        <section id="section-introduction" class="section-landing justified">
            <h2>The revolutionary web development agency</h2>
            <div class="line-height__expanded stack-small">
                <p>
                    Welcome to the CarlMarks Web Development Agency.
                </p>
```

## 2. Ensure a web page is readable for screen readers
In addition to semantic HTML, the project made estensive use of ARIA properties and states in order to optimise its screen reader performance. A slide-accessibility menu was included whose visibility was managed so that it would work well with screen readers and keyboard navigation.
```javascript
// Set up visibility of slide out menu items for screen reader and tab index
function openAccessibilityMenu(event) {
  event.preventDefault();

  if (event.code === "Enter") {
    a11yTrigger.checked = !a11yTrigger.checked;

    // Set tabIndex to 0 if menu active otherwise set to -1 to avoid tabbing into menu
    // Make menu items visible to screen reader if menu shown
    a11yLinks.forEach((link) => {
      link.tabIndex = (a11yTrigger.checked) ? 0 : -1;
      link.ariaHidden = (a11yTrigger.checked) ? "false" : "true";
    });
  }
}
```

## 3. Ensure our UI has sufficient colour contrast so that everyone can perceive it comfortably
The slide-out accessibility menu includes options to change the page theme to light, dark, colour or monochrome. This was to allow for users to select enhanced contrast according to their accessibility requirements. In all themes, contrast ratios exceed 4.5:1 and so are [WCAG compliant](https://wcag.com/designers/1-4-3-color-contrast/). This [short video](https://user-images.githubusercontent.com/32879360/217236427-cd9b5288-9bac-48cb-9fcd-69655913bffe.webm) demonstrates switching themes.

## 4. Use various tools to check that our website meets accessibility criteria
The site is checked for accessibility criteria compliance using the Chrome browser's Lighthouse tool and received a 100% score.

## 5. Use CSS media queries to ensure our content is always presented effectively on screens of different sizes
Media queries are used sparingly where necessary to adapt the screen layout for different screen sizes.
```css
@media only screen and (min-width: 768px) {
    .width-small {
        max-width: 20rem;
    }

    .width-medium {
        max-width: 40rem;
    }

    .width-large {
        max-width: 60rem;
    }

    .contact-form {
        width: 30%;
        min-width: 24rem;
    }

}
```
## 6. Demonstrate a mobile-first approach to building a website
The site makes use of default layouts for mobile screens and adapts this as viewport size increases.
```css
/* 
Set all 'width-<size>' CSS classes to 95% of screen width by default
e.g. .width-small, .width-medium, .width-large ...
*/
[class*="width-"] {
    max-width: 95%;
}
```
## 7. Use CSS variables to apply repeated colours to HTML elements
Extensive use of CSS variables was made to apply display themes and font sizes to the page. This enabled easy integration with the accessibility menu and would allow future contributors to add more themes.
```css
/* Set up page theme colour variables */
[data-theme="colour"] {
    --main-bg-colour: rgb(62, 68, 80);
    --main-text-colour: #fff;
    --main-bg-colour-opacity-zero: rgba(62, 68, 80, 0);
    --team-text-colour: #000;
    --team-bg-colour1: rgb(171, 212, 226);
    --team-bg-colour2: rgb(255, 155, 155);
    --team-bg-colour3: rgb(195, 255, 195);
    --form-bg-colour: rgb(191, 182, 199);
    --form-text-colour: #000;
    --form-invalid-colour: #F00;
}

[data-theme="dark"] {
    --main-bg-colour: #000;
    --main-text-colour: #fff;
    --main-bg-colour-opacity-zero: rgba(0, 0, 0, 0);
    --team-text-colour: rgb(255, 255, 255);
    --team-bg-colour1: rgb(55, 69, 73);
    --team-bg-colour2: rgb(107, 64, 64);
    --team-bg-colour3: rgb(65, 85, 65);
    --form-bg-colour: rgb(97, 90, 102);
    --form-text-colour: #fff;
    --form-invalid-colour: #F00;
}
```
## 8. Use CSS Flexbox to style children in a single-direction layout (ie a row or a column)
The site uses simple flexbox layout to achieve a responsive layout.
```css
header {
    z-index: 1;
    display: flex;
    align-items: flex-start;
    position: fixed;
    justify-content: space-around;
    width: 100%;
    padding-top: 20px;
    top: 0;
    background: rgb(0, 0, 0);
    background: linear-gradient(180deg, var(--main-bg-colour) 0%, var(--main-bg-colour), var(--main-bg-colour-opacity-zero) 100%);
    height: 25vh;
}
```
## 9. Use CSS Grid to style children in two-direction layout
The 'Meet the team' section uses a simple grid layout.
```css
.team-grid-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    grid-gap: 0.5rem;
    width: 100%;
}
```
## 10. Ensure our Git commit history tells a coherent story

## 11. Use the appropriate input types in HTML forms for gathering different types of information
