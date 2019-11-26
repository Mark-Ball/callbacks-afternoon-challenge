# Callbacks afternoon challenge

The objective of the challenge was to use a callback. One function (parseRandomUser) would contain the logic to parse the JSON retrieved from a second function (getRandomUser).

Then getRandomUser would be called using parseRandomUser as a callback. In this simple implementation, the user's title, first name, and last name are retrieved from the JSON and printed to the console.

## Error handling

A try-catch block was implemented to handle errors in case the API call failed. This block was written in the function which is called by the .onload.

The block can be tested by introducing a typo into the randomuser API URL. Line 29 will still run if there is an error due to the try-catch, otherwise it would not run.

## Render the response to the browser instead of the console

To do this we first set an empty p tag which will hold our response. We give this p tag an id so we can reference it more easily.
```HTML
<p id="randomUser"></p>
```

Next we use the DOM to inject our response, in this case we are printing the random user's title, firstname, and last name.
```Javascript
document.querySelector("p#randomUser").innerHTML = `${ans.name.title} ${ans.name.first} ${ans.name.last}`;
```

## Add a button to get the user

First we add a button our HTML. This wil lbe the only button on the page, so it can be uniquely referenced by its tag. Therefore no need to add an id.
```HTML
<button>Get random user</button>
```

The querySelector and addEventListener methods can be used to cause a click on the button to call the getRandomUser function.

querySelector is used to identify the button so that an eventListener can be added. querySelector takes 1 argument, which is a string of the HTML element it is searching for. This could be a tag, class, id, or pseudoclass as referenced in CSS styling.

addEventListener takes 2 arguments: the type of event and the function which will be called when that event is detected. We use the event "click" for a mouse click and the function we call is getRandomUser, which we have written the logic for already.
```Javascript
document.querySelector("button").addEventListener("click", () => {
getRandomUser(parseRandomUser);
});
```

## Implementing axios

Firstly, we must import a script which gives us access to the axios object. This script must be included in addition to the script tag which runs our other javascript.
```Javascript
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```

A get request using axios is very similar to a ```fetch()```. axios.get is a method which takes one argument, the URL where the request is being sent.
```Javascript
const response = await axios.get("https://randomuser.me/api/");
```