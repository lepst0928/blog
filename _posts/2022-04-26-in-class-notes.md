---
layout: post
title:04-26 In-Class Notes [4/26/22]
---

# Week 5 Notes - In Class
- to run javascript on the computer, if have editor on computer open with chrome
- using gitpod cannot use browser to open file
- rather need to cert this page thru a webserver
```javascript
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <script>
    console.log("howdy")
  </script>
 
</body>
</html>
```
            (use html and then tab on the second dropdown option)



**Sintra** ruby web application (instead of rails)
- require 'sinatra'
- type gem install sinatra in the command line

> sinatra is like if our entire rails app was in the routes file
edit then shut down server with cntrl C and then restart server again

user **node my_code.js** is similar to ruby my_app.rb
- rails has rails new command (first and ultimate generator) then can use scaffold command
- every rails application is organized basically the same way because of this new command
- node is the most commonly used framework for web apps today (unfortunately)

dev tools - console (cntrl shift I) [on chrome]

> rails v ruby https://chapters.firstdraft.com/chapters/861

(ruby aside) p vs puts
- p is for the developer
- puts is to print cleaner output (it will format it)

- control / to comment/uncomment

'document' refers to the DOM for a specific page for inspecting, etc on already existing pages
	in class example with the first draft chapter

```javascript
JQuery library: <script src="https://code.jquery.com/jquery-3.6.0.min.js" integrity="sha256-/xUj+3OJU5yExlq6GSYGSHk7tPXikynS7ogEvDej/m4=" crossorigin="anonymous"></script>
JQuery is aliased as $()
```

bootstrap also has javascript plug-ins
> AJAX chapter: https://chapters.firstdraft.com/chapters/863

- **use link to helper method and remote:true (for delete comment)**
- **local:false (for new comment)**


*****The same old steps:
>Switch the link/form from HTML to JS with remote: true on link_to or local: false on form_with.
Add format.js to the appropriate respond_to block.
Write a JS response template. This will usually involve:
Using or creating partials to represent the components being rendered via Ajax.
Adding top-level elements with id="" attributes to the partials, if they don’t already have them.
Writing some jQuery to select an existing element in the DOM and insert near it, replace it, etc.
