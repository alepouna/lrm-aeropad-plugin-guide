# AeroPad Template
   
Welcome to this AeroPad Plguin Template & guide. This guide, is meant to teach you how to create a simple plugin that fetches some data from LRM.

This template assumes you are a beginner developer, with little to no experience. It's designed to show you how to get started with simple programming, and write a super simple plugin for the AeroPad.  you want to invest more time and have the will to learn even more HTML, CSS & JS, than what this guide offers, I strongly advocate for https://www.w3schools.com/. 

This guide is best viewed on GitHub. You can find it here: https://github.com/alepouna/lrm-aeropad-plugin-guide - *For contributors, check the comment below this line when reading this file*
<!--
If you are reading this on GitHub:
Due to personal issues with GitHub, I will not be reviewing comments, issues or PRs on the GitHub repo. Feel free to instead file issues, PRs, etc. on GitLab: https://gitlab.com/alepounas-guides/lrm-aeropad-example-plugin

For GitLab contributors: 
I will be manually updating any changes from GitLab to GitHub, until I either find or create a solution that syncs them with actions or something. 

To those wondering why use both? 
1. Like mentioned earlier, I don't wish to use GitHub anymore due to personal issues, ask me over a beer. 
2. GitHub has a much nicer UI for showing the markdown files (such as tips, notes, etc.) compared to GitLab. 
--> 

## The Basics

First and formost, I want to introduce what we are working with here. 

The AeroPad is essentially a webserver, that loads plugins (webapps) and displays them to your browser. This gives you A LOT of flexibility in what you can do and create, but also a few limitations, thankfully, most of them are browser related.

Each AeroPad plugin, requires a few files, for starters a file called `lrm-plugin.json`. We will talk about this later on this guide. It also requires a file called `index.html` which will load the 'primary' HTML file of our plugin. 
> [!TIP]
> HTML stands for 'HyperText Markup Language' and is the standard markup language for documents designed to be displayed in a web browser. 

It will also require an image file, that will be used in the 'AeroPad' dashboard to show your app to the world.  

Other than these basic requirements, we can go as "ham" as we want with our plugin, but since it's a web application, we will require two more things in our skillset: 
1. CSS - Cascading Style Sheets - Allows us to make our 'HTML' document pretty.
2. JS - JavaScript - Allows us to make our HTML document interact with the browser and user actions.

> [!NOTE]  
> As mentioned earlier, if you need to learn more about either of the above and HTML, check out https://www.w3schools.com/

Our CSS and JS file names do not matter, as they are imported from inside the HTML file. This means we can name them and organize them as we like. 

You may notice in this plugin among other, most css and js files end in `.min.js` or `.min.css`. The 'min' stands for 'minimized'. If you open these files, they look like garbled mess, but this is something we call "minification". This allows developers to make pretty JS or CSS files as minimized as possible, in order to optimize and save storage and bandwidth from loading these files. They have usually no difference in the end, but one looks pretty to humans, but also takes more space.

In this template (and most of my websites & plugins), I utilize 'frameworks' for both CSS and JS, in order to make my life easier. 

> [!TIP]
> A framework is a template or toolkit that helps programmers build software more easily by providing ready-made tools and structures to work with. It's like using pre-made parts to build something instead of starting from scratch.

Now you may think this is all too much, but frameworks as designed to make our life easy, while you do not have to learn a specific framework, I strongly recommend picking up one, as in the end, you will be the one writting less code! 

For my template app, I've decided to use Tailwind for the design. Tailwind allows you to rapidly build modern websites without ever leaving HTML. Using Tailwind, personally allows me to benefit from not having to write any CSS, and focus more on the actual design and the Javascript! I don't want to get too deep into the details, but thankfully Tailwind has an extremely comprehensive and simple guide and documentation page, so if you want to follow my steps, do check it out here: https://tailwindcss.com/

> [!NOTE]
> Tailwind can be both 'compiled' (aka generate the CSS files and load them in your HTML) or be used by importing the 'Play CDN' CSS. Tailwind recommends the 'Play CDN' for development purposes only, and me too, however if you are just starting, its fine to use the Play CDN to start out. 

Now you may "Chief, how can I do all these coding and computer things then?" Well thankfully, you are not going to need much. You will need a program that allows you to edit files, more specialized to programming, so something like Visual Studio Code (get it [here](https://code.visualstudio.com/download)) will be more than enough. After you download VSC (Visual Studio Code), create a folder on your desktop, or anywhere else, and open that folder with VSC.

## Getting Started

The first thing we will need to create, as mentioned earlier, is a file called `lrm-plugin.json`. Open that file in VSC, and paste the following code: 
```json
{
  "name": "",
  "description": "",
  "icon": "",
  "developer": "",
  "url": "",
  "version": "1.0.0",
  "open_mode": "same",
  "remote_app_url": null
}
```

This file tells the Aeropad what to do with our plugin. We will need to fill in some details: 
| Field       | What to enter                                   |
|-------------|-------------------------------------------------|
| name        | The plugin name                                 |
| description | The description of your plugin                  |
| icon        | The file and path to your apps icon             | 
| developer   | Your name or organization                       |
| url         | The URL where people can grab your plugin from  | 
| version     | The current version of your plugin              | 

We will not touch the other values for now, you can read more about them in the LRM AeroPad developer docs. 

> [!IMPORTANT]  
> It's important that any value you enter in these fields you write in this json file is inside quotation marks (""). For example: `name: "Name here"`, if you fail to do this (by doing something like `name: my plugin`) you will invalidate the JSON file and cause issues. You can search for websites that validate JSON online to check your file is a-ok (duckduckgo will [do this](https://duckduckgo.com/?q=json+validator&ia=answer) for you)

Make sure to press "CTRL + S" to save the file ;) 

The next thing you should do, is create an icon for your plugin. You can copy the 'icon.png' provided by this template plugin, change the colors, add your own icon, etc. If you want to create a new one from scratch, make sure the icon is 256x256 and as compressed as possible, to save storage.

> [!NOTE]  
Make sure in the `lrm-plugin.json` file the 'icon' field is matching exactly the name of the icon file you just created. Its recommended you avoid spaces, use `-` or `_` instead. 

Now that we have our LRM configuration file, and our icon, let's create our `index.html`. As the name suggests, this is our 'guiding' file, meaning that the AeroPad will pick this file first. If we want our app to be more complicated and have more than one HTML files, we of course can create those, but we will have to call these from our index file. 

Inside the index file, type `!` which in VSC will prompt you to select the "! Emmet Abbreviation", alternative you can just paste this in this: 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```
This HTML code sets up the basic structure and metadata for our plugin, which tells our browser a few things about our HTML document: 
- The language is english
- The character encoding is UTF-8
- The viewport is responsive to the device width
- The title of the page to be 'Document' 

This information is set in the 'header' section of our document. Following, you will see an empty "body" section. This is where we will fill our page with all our code. 

The first thing we want to enter inside the `<body>` section, is the "LRM AeroPad Standard Back Button". You can find this on the `[LRM Standard Back Button]()` documentation. 

If you have followed everything correctly, our final document should look like this: 
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

<!-- Standard LRM Tablet "Back Button"-->
<span style="position: absolute; top: 0; margin-top: 5px; margin-left: 5px; z-index: 1000;">
    <a href="/plugins/" class="text-light">
        <svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" fill="#FFFFFF"
             class="bi bi-arrow-90deg-left" viewBox="0 0 32 32">
            <path fill-rule="evenodd"
                  d="M1.146 4.854a.5.5 0 0 1 0-.708l4-4a.5.5 0 1 1 .708.708L2.707 4H12.5A2.5 2.5 0 0 1 15 6.5v8a.5.5 0 0 1-1 0v-8A1.5 1.5 0 0 0 12.5 5H2.707l3.147 3.146a.5.5 0 1 1-.708.708l-4-4z"/>
        </svg>
        <i class="bi bi-arrow-90deg-left"></i>
    </a>
</span>
<!-- End Standard LRM Tablet "Back Button"-->
    
</body>
</html>
```

We can now move this folder inside the "ws/plugins" our LRM Installation location (so in my case it's in `C:\Program Files (x86)\Landing Rate Monitor\ws\plugins\EXAMPLE-TEMPLATE`, where 'EXAMPLE-TEMPLATE' should be your plugins name without any spaces)

If you reload the Aeropad, you should now see your plugin! 

[!plugins_page_example.png](/assets/plugins_page_example.png)

If you click on the plugin, you should see a white page, and if you hover on the top left of this white space, you should be able to click on the 'invisible' white arrow and go back to the plugins! 
> [!NOTE]
> The arrow can not be seen because our page and the arrow are both white colored, making them essentially invisible.

## Styling our plugin


### Creating a background

It's time to start styling our plugin, the first thing we want to do, is add Tailwind, as I mentioned earlier, it will make our life designing our document easier, as we won't have to mess with CSS. 

To get started with Tailwind, we want to add this script tag inside our 'head' section: `<script src="https://cdn.tailwindcss.com"></script>`

Once this is done, we can test that it's working by adding a 'div' tag below our LRM Aeropad Tablet back button: 

```html
<div class="relative flex min-h-screen flex-col justify-center overflow-hidden bg-slate-900 py-6 sm:py-12">

</div>
```

Once we refresh the page, it should be dark color. A 'div' tag is an element that stands for 'division' / 'divider'. It doesn't have any semantic meaning on its own but serves as a generic container for other HTML elements.
We can specify properties to this div, one of them being a 'class', which allows us inside to specify style classes.

In this case, according to the Tailwind documentation, we are applying the following: 
`relative`: This class sets the positioning context of the element to relative. It means that any absolutely positioned children of this element will be positioned relative to this container.
`flex`: This class enables flexbox layout for the container. Flexbox is a layout model that allows elements to align and distribute space within a container dynamically.
`min-h-screen`: This class sets the minimum height of the container to the height of the viewport (screen). This ensures that the container takes up at least the full height of the screen.
`flex-col`: This class specifies that the flex container should arrange its items in a column layout. This means the child elements will be stacked vertically.
`justify-center`: This class aligns the flex items along the main axis (which is vertical in a column layout) and centers them vertically within the container.
`overflow-hidden`: This class hides any content that overflows the container's boundaries. It's often used to prevent content from overflowing and disrupting the layout.
`bg-slate-900`: This class sets the background color of the container to a specific color from Tailwind CSS's color palette. In this case, it's using the color slate-900.
`py-6 sm:py-12`: These classes set the padding on the y-axis (top and bottom) of the container. The py-6 class sets padding of size 6 (which is a default spacing unit in Tailwind CSS), and sm:py-12 sets padding of size 12 on small screens and above (sm: indicates the breakpoint).

So in summary, our `div` creates a container that: 
- Is positioned relative to its parent.
- Utilizes flexbox for layout.
- Ensures a minimum height of the viewport.
- Arranges its child elements in a column layout and centers them vertically.
- Hides any content that overflows its boundaries.
- Has a background color of slate-900.
- Applies padding vertically with different sizes based on screen size breakpoints.

### Setting up a 'card'

We will create now a 'card' style div using the following code: 
```html
<div class="relative bg-white px-6 pt-10 pb-8 shadow-xl ring-1 ring-gray-900/5 sm:mx-auto sm:max-w-lg sm:rounded-lg sm:px-10">
</div>
``` 

We will put this inside the previous div. Divs go inside divs, and complicated websites can do this forever! Don't be afraid to organize your elements! 

### Creating text

Now we want to add some text to this card, so we will add the following div and inside it, a `<p>` element
> [!NOTE]
> <p> stands for paragraph. You can use this for 'small' / normal text. 

```html
<div class="divide-y divide-gray-300/50">
    <div class="space-y-6 py-8 text-base leading-7 text-gray-600">
        <p>Hello world</p>
    </div>
</div>
```

This HTML code creates a container div with a vertical divider and a child div with some padding, spacing, font size, line height, and text color applied. Inside this child div, there's a paragraph element with the text "Hello world".

You can refresh the page to see the result for yourself! 

### Preparing for code

To make our life easy, we will use a system HTML uses called IDs. IDs will allow us to later use JavaScript to fetch a specific element. 

We will create another 'paragraph' element in our above div, and we will give it an ID of `lrm-version`, as follows: 

```html
<div class="divide-y divide-gray-300/50">
    <div class="space-y-6 py-8 text-base leading-7 text-gray-600">
        <p>Hello world</p>
        <p id="lrm-version"></p>
    </div>
</div>
```

> [!WARNING]
> The above snippet is to replace the div we already have. If you add it again, you will create a weird duplication of our elements.

## Writting some JavaScript

Now that we have made a basic design, it's to write some code. For the purpose of keeping everything simple, we will keep our code limited in the HTML file using a `<script>` tag below our body element. 

We will start simple, by adding a 'function' called `alert()`, this will cause our browser to show, well, an alert. 

```html
<script>
    alert("Hello world")
</script>
```
> [!NOTE]
> Moving forward, I will skip the script tags, and instead show you the 'raw' JavaScript.

Once you refresh the page, you will see an alert from your browser, saying 'Hello world' !

It is important you remember that unlike HTML, if there is a major issue with your code, the entire file will not load. It is recommended you open the Dev Tools (by pressing F12) and going to the 'Console' tab to monitor for errors and logs from JavaScript. 
If you are in the correct page, you should see a warning about Tailwind, that's perfectly fine. 
> [!TIP]
> We can simulate an error by entering `whateverThisMightbe` in our script tag and refreshing the page. 

In HTML, in order to prevent 'race conditions', sequencing and waiting for DOM* to load properly, we should utilize an event listener called `window.onload`. This will call a function we define, when the DOM has loaded. 
> [!NOTE]  
> DOM stands for Document Object Model. It's a programming interface for web documents. When a web page is loaded into a web browser, the browser creates a model of the page's structure, content, and styling. This model is known as the Document Object Model.

To use the event listener, we will create a function on it as follows (and we will also move the 'alert' function inside our event): 
```js
window.onload = function() {
    alert("Hello world")
}
```

We will now use another function, to call the paragraph DOM we created earlier, by its ID. To do that, we will do: `const p = document.getElementById("lrm-version");`

This will allow us to use `p` and call functions from there. For example, we can do something like `p.innerText = "Hi"`, which will programmatically change our paragraph element to display 'Hi' instead of nothing. 

If you add this code, once you refresh the page, you will see the text 'Hi' below 'Hello world', after you click 'Ok' on the alert.
> [!WARNING]
> JavaScript is both synchronous and asynchronous. Synchronous JS is like doing tasks one after the other, while asynchronous JS allows you to do multiple tasks simultaneously, like flying your aircraft while checking your phone (don't do that!).
> In our example, the code executes sequentially: first, an alert is shown with "Hello world", and then our paragraph is changed to "Hi".
> It is important you remember this, as you may see code that does not run until something happens, or runs early and shows you different results! 

## Connecting to LRM 

Now that we have understood the basics, let's try to fetch some data from LRM. To keep our example simple, we will fetch the version LRM currently is in. To do that, we will probe LRM for this information using the `fetch()` function: 
```js

function probeLRM() {
    fetch('http://127.0.0.1:8320/v1/a')
    .then(response => {
        if (!response.ok) {
        throw new Error('Network response was not ok');
        }
        return response.json();
    })
    .then(data => {
        console.log(data) //Prints the data in the console
        p.innerText = data.lv //Set the LRM version field 
    })
    .catch(error => {
        console.error('There was a problem with the fetch operation:', error);
    });
}
```

As you noticed, we also wrapped this in a function. This mean we can call this function easily on another part of the code. 

The problem we have now: Our code runs only once. This means that the data will only be fetched every time the user refreshes their browser. That isn't really convienent! 

To fix this problem, we can utilize `setInterval()` which is a function that allows us to call other functions every specified set amount of time. 

To do this, we will use `setInterval(probeLRM, 1000)`. This means that the `probeLRM` function will be called every 1000ms - 1 second. 

We will write this function outside our 'probeLRM' function, so in the end we should have something like this in our `<script>` tag: 

```js
window.onload = function() {
    alert("Hello world");

    const p = document.getElementById("sim-status");

    function probeLRM() {
        ...
    }

    setInterval(probeLRM, 1000)
}
```

After you refresh the page, and click to dismiss the alert, a second later, and every second after that, our code will probe LRM and display the currently reported version of LRM.

> [!WARNING] 
> The value we are using (LRM Version), will not change unless you update the LRM client. As such, you will not see any data updates. You can use another value to display, by simply replacing the `p.innerText = data.XXXXXXX` part of the code with the data value you like, as documented in the LRM AeroPad developer documentation! 

## Conclusion

And that's it for our simple guide! We have managed to develop a plugin, do a little bit of designing, and write some code! Feel free to keep experimenting with the template, or go wild and create your own plugin! 

If you enjoyed this guide, be sure to let me know, as I love writing little technical guides for things. If you have any feedback, do send them my way, I would love to hear them. If you are starting out and you have questions, the [FsHub Forums page for developers](https://forums.fshub.io/forum-9.html) is a great place to start! 
