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
The slide-out accessibility menu includes options to change the page theme to light, dark, colour or monochrome. This was to allow for users to select enhanced contrast according to their accessibility requirements. In all themes, contrast ratios exceed 4.5:1 and so are [WCAG compliant](https://wcag.com/designers/1-4-3-color-contrast/). This video demonstrates the themes available:
[layout-issue.webm](https://user-images.githubusercontent.com/32879360/217236099-8f90136d-480f-4aac-8109-1d3d7148dc58.webm)

## 4. Use various tools to check that our website meets accessibility criteria

## 5. Use CSS media queries to ensure our content is always presented effectively on screens of different sizes

## 6. Demonstrate a mobile-first approach to building a website

## 7. Use CSS variables to apply repeated colours to HTML elements

## 8. Use CSS Flexbox to style children in a single-direction layout (ie a row or a column)

## 9. Use CSS Grid to style children in two-direction layout

## 10. Ensure our Git commit history tells a coherent story

## 11. Use the appropriate input types in HTML forms for gathering different types of information
