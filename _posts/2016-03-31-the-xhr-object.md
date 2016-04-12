---
layout: post
title: "JavaScript - How to use an XHR object"
excerpt: "Utilizing XHR objects in your application."
categories: Programming
tags: [javascript]
date: 2016-03-31
comments: false
---



XMLHttpRequest is an API that provides an easy way to retrieve data from a URL without needing to refresh the entire page.

Below is an example of using JavaScript to display information about a selected object from a dropdown menu. The feature itself is in the sidebar of a CRM dashboard so we need to be able to display the selected client profile without refreshing the entire page. That’s why we’re using XHR.

```js
  var dropdown = document.getElementById("dropdown_select");
  var presentation_area = document.getElementById("current_client");

  dropdown.addEventListener("change", function(event){
        var client_id = dropdown.options[dropdown.selectedIndex].value;

        var client_request = new XMLHttpRequest();

        client_request.open("GET", "/clients/profile/"  + client_id);

        client_request.addEventListener("load", function(request_object){
          presentation_area.innerHTML = request_object.target.response;
        });

        client_request.send();
       
      });

```

### Let’s go through the implementation of this XHR object.

1. First we define the variable that is the target of the event listener and the variable of the location we want our XHR object to display:

   ```js
var dropdown = document.getElementById("dropdown_select");
var presentation_area = document.getElementById("current_client");
```

2. Then we create our event listener. In this case, JavaScript is listening for a change in the selected option of this dropdown menu:

   ```js
dropdown.addEventListener("change", function(event){
```

3. In order for this XHR object to open the correct URL, we need to ensure that all of the correct information is being passed in so that it can match up with the correct route and controller objects. In this case, our route contains a specific client id, so we must get the value that corresponds to the selected option in the dropdown:

   ```js
var client_id = dropdown.options[dropdown.selectedIndex].value;
```

4. After setting these variables and event listeners, we can create our XHR object:

   ```js
var client_request = new XMLHttpRequest();
```

5. Then we tell that object which URL it needs to open when it is actually sent. Since we’ll be displaying a view (rather than submitting a form, for example) we’re using a `”GET”` request. The XHR object will then look in the routes file to find a path that matches “/clients/profile/:id”:

   ```js
client_request.open("GET", "/clients/profile/"  + client_id);
```

6. We also define what actions should be taken when this request’s response is received. To do this, we create an event listener for the `”load”` event. Whatever JavaScript we add into the callback for this event listener will execute when the response is received.

    ```js
client_request.addEventListener("load", function(request_object){
```

7. And then we tell that XHR object *what* content to display and *where* to display it. The `request_object` contains all of the data in the view as well as data *about* the request, like what time is was sent.  Here, we’ll be displaying the targeted response of the `request_object` view inside the HTML of the presentation area variable that we defined earlier:

   ```js
presentation_area.innerHTML = request_object.target.response;
```

8. And finally, we send the request:

    ```js
client_request.send();
```
