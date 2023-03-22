## USER
How can I make a list of all links on a page, which where created using javascript, and look like ##.text-sm.text-gray-100.gap-2.flex-col.flex

## ASSISTANT
To create a list of all links on a page created using JavaScript and having the specified class names, you can use a combination of JavaScript and the browser's Developer Tools. Here's a step-by-step guide to achieve this:

1. Open the web page containing the links you want to extract in a browser like Chrome, Firefox, or Edge.
2. Open the Developer Tools by right-clicking on the page and selecting "Inspect" or pressing `Ctrl` + `Shift` + `I` (Windows/Linux) or `Cmd` + `Opt` + `I` (Mac).
3. Click the "Console" tab in the Developer Tools to access the JavaScript console.
4. In the console, enter the following JavaScript code and press `Enter`:

```javascript
const links = [...document.querySelectorAll('.text-sm.text-gray-100.gap-2.flex-col.flex a')].map(a => a.href);
console.log(links);
```

This code will search for all `a` elements with the specified class names, extract their `href` attribute, and store them in an array called `links`. The `console.log()` function will then print the array in the console.

5. You'll see the list of links printed in the console. You can copy this list by right-clicking on it and selecting "Copy Object" or "Store as Global Variable" and then copying it from the newly created variable.

Note that if the links are generated dynamically and added to the page after it initially loads, you may need to wait for the JavaScript to execute before running the code above. You can use the `setTimeout()` function to wait for a specified period before executing the code:

```javascript
setTimeout(() => {
  const links = [...document.querySelectorAll('.text-sm.text-gray-100.gap-2.flex-col.flex a')].map(a => a.href);
  console.log(links);
}, 5000); // Adjust the waiting time (in milliseconds) if needed
```

This code will wait for 5 seconds (5000 milliseconds) before executing the link extraction script. You can adjust the waiting time as needed.