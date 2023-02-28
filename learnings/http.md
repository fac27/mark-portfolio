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
### 7. Use the filter array method to create a new array with certain values removed

### 8. Access DOM nodes using a variety of selectors

### 9. Add and remove DOM nodes to change the content on the page

### 10. Toggle the classes applied to DOM nodes to change their CSS properties

### 11. Use consistent layout and spacing

### 12. Follow a spacing guideline to give our app a consistent feel

### 13. Debug client side JS in our web browser

### 14. Use console.log() to help us debug our code
