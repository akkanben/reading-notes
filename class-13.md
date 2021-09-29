# Reading Notes #13 - Local Storage

Native apps have had an advantage over web apps when it comes to storing user preferences or other user specific details. Cookies have been used on the web to store small (4KB) chunks of data but because the cookies are included with each HTTP request it can unnecessarily slow things down. Often cookies are sent in an insecure manner.

Before HTML5 there were many attempt to improve cookies but they all either used third-party plugins, or were specific to a browser. 


## Using HTML5 storage

Before using it, check if the global window object `localStorage` is not null. Local HTML5 storage uses key value pairs and is always stored in strings. If strings are not the type needed then type coercion will be needed.

- `localStorage.getItem('key')`
- `localStorage.setItem('key', 'value')`
- `localStorage.removeItem('key')`
- `localStorage.clear();
- `localStorage['key'] = 'value'`

The 'storage' event can have listeners added to it if you need to track with it changes. The storage event has multiple properties: 'key', 'oldValue', 'newValue', and url.

Most browsers will allow 5Mb of space in local storage. If this is exceeded then "QUOTA_EXCEEDED_ERR" will be the exception thrown.

Web SQL Database and IndexedDB are competing database standards and only work in some browsers and may be useful and cross platform someday, maybe.
