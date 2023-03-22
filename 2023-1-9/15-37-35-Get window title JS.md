## USER
Get the window title in javascript

## ASSISTANT
To get the window title in JavaScript, you can use the `document.title` property.

Here is an example:

```
console.log(document.title);  // prints the window title
```

You can also use the `document.title` property to set the window title:

```
document.title = 'My New Title';  // sets the window title to 'My New Title'
```


## USER
How I get the url, too?

## ASSISTANT
To get the current URL of the page in JavaScript, you can use the `window.location.href` property.

Here is an example:

```
console.log(window.location.href);  // prints the current URL
```

You can also use the `window.location` object to get other parts of the URL, such as the protocol (`window.location.protocol`), hostname (`window.location.hostname`), and pathname (`window.location.pathname`).

For example:

```
console.log(window.location.protocol);  // prints the protocol (e.g. 'https:')
console.log(window.location.hostname);  // prints the hostname (e.g. 'www.example.com')
console.log(window.location.pathname);  // prints the pathname (e.g. '/path/to/page.html')
```

You can also use the `window.location` object to navigate to a new page. For example:

```
window.location = 'https://www.example.com';  // navigates to the specified URL
```
