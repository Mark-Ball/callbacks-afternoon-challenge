# Callbacks afternoon challenge

The objective of the challenge was to use a callback. One function (parseRandomUser) would contain the logic to parse the JSON retrieved from a second function (getRandomUser).

Then getRandomUser would be called using parseRandomUser as a callback. In this simple implementation, the user's title, first name, and last name are retrieved from the JSON and printed to the console.

## Error handling

A try-catch block was implemented to handle errors in case the API call failed. This block was written in the function which is called by the .onload.

The block can be tested by introducing a typo into the randomuser API URL. Line 23 will still run if there is an error due to the try-catch, otherwise it would not run.

## Render the response to the browser instead of the console

To do this we first set an empty p tag which will hold our response. We give this p tag an id so we can reference it more easily.
```
<p id="randomUser"></p>
```

Next we use the DOM to inject our response, in this case we are printing the random user's title, firstname, and last name.
```
document.querySelector("p#randomUser").innerHTML = `${ans.name.title} ${ans.name.first} ${ans.name.last}`;
```