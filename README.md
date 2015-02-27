# JQuery/Ajax Quiz

Write your answer below each question.

### Question 1
(a) What is a click handler?

An event handler function that is bound to a 'click' event on an HTML element.

(b) Where in your JS file should you put it, and WHY?

In the document.ready, so that the HTML will load first, so that the element will be loaded before being bound the event handler.

### Question 2
If you get the error `$ is undefined`, what does that mean and what could you do to fix it?

JQuery must be included in your HTML file.

### Question 3
What should go in the `$(document).ready()` part of your JS file?

Event handler functions.

### Question 4
In an AJAX GET request, what does the argument of the `.done()` callback - in the example below, that would be `data` - represent?

The data being returned from the server - in this case an array of users that came in as JSON and was converted to javascript by JQuery.

```
$.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'GET',
  })
  .done(function(data) {
    console.log("success!")
  });
```
### Question 5
In an AJAX POST request, what does the argument of the `.done()` callback - in the example below, that would be `data` - represent? (Hint: it's not the same as in Question 4.)

The return from the POST request, in this case a javascript object representing the new user we just submitted to POST.

```
  $.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'POST',
    dataType: 'JSON',
    data: { user: { name: "Anna", about: "instructor", email: "hi@gmail.com" } },
  })
  .done(function(data) {
    console.log("success!");
  });
```
### Question 6
Suppose you had the following form in your HTML file. Use jQuery to write a single line of code that takes whatever the user entered in the textbox and saves it to the variable `user_input`.

var user_input = $('#color').val();
  or
var $user_input = $('#color').val();

```
  <form>
    <p>The dress is:</p><input type="text" id="color">
    <input type="submit" value="Submit" id="submit">
  </form>
```

### Question 7
This code looks like it works, but when you run it, you see that the `UserApp.add_all_users()` function executes but `console.log` displays `undefined`. What's wrong with the code?

UserApp.add_all_users(data); should be inside the .done(function(data))

```
UserApp.get_all_users = function() {
  $.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'GET',
  })
  .done(function(data) {
    console.log("success!")
  });
  UserApp.add_all_users(data);
};

UserApp.add_all_users = function(data) {
  console.log(data);
};
```



