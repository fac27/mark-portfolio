## Home Finder - An API call project
![Home Finder](https://user-images.githubusercontent.com/32879360/221849621-79c2fc0d-2cb2-4787-964a-d84f4fb29815.gif)

### 1. Write code that executes asynchronously
This project involved making a number of API calls which return JSON data asynchronously. These were handled within asynchronous calls...
```JavaScript
export const getBasicInfo = (postcode) => {
  return fetch(`https://api.postcodes.io/postcodes/${postcode}`)
    .then((response) => {
    // ...
    }
```

### 2. Use callbacks to access values that aren’t available synchronously
The project made extensive use of arrow functions as callbacks which were called when the API calls returned their payload.

### 3. Use promises to access values that aren’t available synchronously
Promises were chained together to decode and display data from the API calls...
```JavaScript
.then((json) => {
        userInfoContainer.style.display = 'none';
        crimeDataJson.push(json);
        crimeDataJson = crimeDataJson.flat(2);
        this.#createCrimeDataFromJson(crimeDataJson);
      });
```
### 4. Use the fetch method to make HTTP requests and receive responses
The JavaScript fetch() function was used throughout...

```JavaScript
export const getLongAndLat = (postcode) => {
  return fetch(`https://api.postcodes.io/postcodes/${postcode}`)
    .then((response) => {
      if (response.ok) {
        return response.json().then((data) => ({
          latitude: data.result.latitude,
          longitude: data.result.longitude,
        }));
      } else {
        throw new Error(response.status);
      }
    })
    .catch((error) => console.log(error));
};
```
### 5. Configure the options argument of the fetch method to make GET and POST requests
Options for API calls were encoded into query strings for all of the simple APIs used. None required authentication credentials.

### 6. Use the map array method to create a new array containing new values
Crime data is served up a month at a time by the crime data API. This app bundled 12 months of fetches into an array and then iterated through each call using the Arrap.map() function. This enabled the app to update the user with a progress bar as each month's data was received:

![image](https://user-images.githubusercontent.com/32879360/221853282-55076bae-154f-45f0-9fda-fc57a0f5f4b7.png)

```JavaScript
allQueryStrings.map((qs) =>
        fetch(qs)
          .then((response) => {
            if (response.ok) {
              progressBar.value = Math.floor(
                (++fetchNumber / totalFetches) * 100
              );
              
              progressBar.textContent = `${progressBar.value}%`;
              p.textContent = `Fetching crime data (${progressBar.value}%)`;
              return response.json();
            }
          }).catch((error) => {
            console.error("OH NO! This happened when fetching crime data:\n" + error);
            userInfoContainer.style.display = 'none';
          })
      )
 ```
### 7. Use the reduce array method to create a new array with certain values removed
The project used the Array.reduce() method to summarise crime data according to any categories such as 'crime type' or 'data of crime':
```JavaScript
const summary = allCrimes.reduce((tally, allCrimes) => {
      if (tally[allCrimes[field]]) {
        tally[allCrimes[field]] += 1;
      } else {
        tally[allCrimes[field]] = 1;
      }

      return tally;
    }, {});
    return summary;
```
### 8. Access DOM nodes using a variety of selectors
Access to DOM nodes was used extensively to update data on the page.
```JavaScript
const crimeInfoOutput = document.querySelector('#output__crime');
const crimeChartOverlay = document.querySelector('#crime__chart--large');
```
### 9. Add and remove DOM nodes to change the content on the page
This was also used extensively within the project...
```JavaScript
  const pieChartHeading = document.createElement('h3');
  pieChartHeading.textContent = pieChartTitle;
  const barChartHeading = document.createElement('h3');
  barChartHeading.textContent = barChartTitle;
  const pieChartDescription = document.createElement('p');
  pieChartDescription.id = 'pie-desc';
  pieChartDescription.className = 'screen-reader-only';
  pieChartDescription.innerText = getPieChartDescription(crimes);
  
  // ...
  
  crimeInfoOutput.append(crimeInfoDiv);
  crimeInfoOutput.append(barChartHeading);
  crimeInfoOutput.append(barChart);
  crimeInfoOutput.append(barChartDescription);
  crimeInfoOutput.append(pieChartHeading);
  crimeInfoOutput.append(pieChart);
  crimeInfoOutput.append(pieChartDescription);
```
### 10. Toggle the classes applied to DOM nodes to change their CSS properties
This was used for example in enabling the user to click on a data chart graphic to zoom it to full screen...
```JavaScript
function toggleChartToFullScreen(image) {
  crimeChartOverlay.style.backgroundImage = 'url(' + image.src + ')';
  crimeChartOverlay.style.display = 'block';
}
```
### 11. Use consistent layout and spacing
The site was constructed with a mobile-first design methodology. It was optimised for small screens and then enhanced for larger viewports...
```css
/* Set all 'width-<size>' CSS classes to 90% of viewport width by default
e.g. .width-small, .width-medium, .width-large ... */
[class*='width-'] {
  max-width: 90vw;
}

/* Override screen width mobile-first settings for larger viewports */
@media only screen and (min-width: 821px) {
  .width-small {
    max-width: 20rem;
  }

  .width-medium {
    max-width: 40rem;
  }

  .width-large {
    max-width: 60rem;
  }
```

### 12. Follow a spacing guideline to give our app a consistent feel
Some use was made of css layout primitives to aid consistent and structured styling...
```css
.stack-s > * + * {
  margin-top: 0.5rem;
}

.stack-m > * + * {
  margin-top: 1.5rem;
}

.stack-xl > * + * {
  margin-top: 4rem;
}
```
### 13. Debug client side JS in our web browser
In-browser debugging was employed throughout development, for example to peek into JS object data.

### 14. Use console.log() to help us debug our code
Debugging through the following methods was used...
console.log()
console.table()
console.error()
