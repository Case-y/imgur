<<<<<<< HEAD
# imgur-voice
Javascript workshop for Cal Hacks and Hackers @ Berkeley

[imgur-voice](https://carpetfizz.github.io/imgur-voice/) takes advantage of `webkitSpeechRecognition` in Google Chrome to search [imgur.com](http://imgur.com/)

## Obtaining an imgur Client ID
In this workshop we will be accessing imgur's API (Application Programming Interface) to fetch images based on a search parameter. To do this, we must obtain a Client ID from imgur.com. Popular APIs do this to combat spam and ensure the authenticity of its consumers.

1. Create an account on [imgur.com](http://imgur.com/)
2. Register your application by filling out this [form](https://api.imgur.com/oauth2/addclient). 
   * Application Name: `YourNameImgurVoice`
   * Authorization Type: `Anonymous usage without user authorization`
   * Authorization Callback URL: `https://localhost:8000` (This one doesn't really matter. Enter any valid URL)
3. Find your Client ID by going to [apps](https://imgur.com/account/settings/apps). Make sure you're logged in!
4. Now we just need to put our unique Client ID into our code. Change the line that says `	imgurRequest.setRequestHeader("Authorization", "Client-ID your_client_id");` by replacing `your_client_id` with the one you just generated.

Alternatively, use the client_id provided in class. 

## Starter Code 

We've provided some starter code to help you get started. It includes HTML and some Javascript to handle speech recognition. You will primarily be working with index.js 


## Running the server 

To launch your website, run your this command in your project directory: 

`python3 -m http.server 8000` 

Then open Chrome to `http://localhost:8000`

Try it out. What happens when you click the button? 

## Tools before getting started

- Javascript Developer Console. 

	Chrome > View > Developer > JS Console 

- console.log(...)

	Let's you print output to the console from your code. 

All you have to do to run a new version of your code is save the javascript file and refresh your browser. 

## Step 1 - Buttons should do things.

Work on the `toggleListen()` function. 

This function should check if the `isListening` variable is True/False. 
It should then either start or stop `recognition` by calling the approriate method. For example, to start recognition - `recognition.start()`. 
You should also change the text of the button be different after hitting the button. 
To do so, set `listenButton.innerHTML` to some string.

Once you are done with this you should be able to see what voice recognition returns.  

## Step 2 - Search Imgur For the Phrase

To search imgur - we can use the imgur API 

	- Create XHR request
	- When the request is ready, check if it's successful
	- Retrieve the data from the response
	- Send the data to the success handler

Here's how you make `AJAX` Req in Javascript. Try pasting it into your console. 


```
var xhr = new XMLHttpRequest();

xhr.onreadystatechange = function () {
	if (xhr.readyState === 4 && xhr.status === 200) {
		console.log(xhr.response.data);
	}
}; 

xhr.open('GET', 'http://api.openweathermap.org/data/2.5/weather?q=Berkeley&appid=2de143494c0b295cca9337e1e96b00e0'); 
xhr.responseType = 'json';
xhr.send();

```

For imgur - it will be something similiar except before we send - we have to authenticate ourself. 

	`xhr.setRequestHeader("Authorization", "Client-ID a672a0e950c3b87");`

For imgur - the URL to perfrom a get method is `"https://api.imgur.com/3/gallery/search?q="` followed by your query. An example would be `"https://api.imgur.com/3/gallery/search?q=cats"`

If the response data has something, `xhr.response.data.length > 0` - call the `successHandler` function with the data. Otherwise - change the text of `successText` to tell the user that we didn't find any results. 


## Step 3 - Add the results to the page. 

Once we get data in `successHandler`, we have to add pictures to the page. successHandler has to loop through the responses and add them to the page. 

To add images to the page you can use the appendChild method - which adds an element to the page. 

```
var image = new Image()
image.src= "http://cs61a.org/assets/images/john-denero.jpg";
imageContainer.appendChild(image);
```

Look at the comments to see what needs to be done to successHandler. 

## Step 4 - Try it out. 

Check it out! 

If you used git & github - you can deploy it to github pages and get a URL to share with friends. 
Aproximate instructions:

1. Commit your changes `git commit -am 'Your message here'`
2. Push to master `git push origin master`
3. Push to the gh-pages branch `git push origin gh-pages:`









=======
# imgur
>>>>>>> 2e0907a2975d7eeb68c041a18581ebe45d551995
