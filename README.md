# Y2 2019 Summer: Forms in Flask

Welcome to forms in Flask! (Note that this comes after
[routing with Flask](https://github.com/meet-projects/y2s18-routing).)
Please read all the instructions so you don't get lost halfway
through, but definitely feel free to ask for help if you get stuck.
Good luck, and have fun!

## Setup

Before you start coding, make sure you fork and clone the repository
for this lab:
```
cd ~/Desktop
git clone https://github.com/YOUR_GITHUB_USERNAME/y2s19-flask-forms.git
```

## Warm-up Exercises

### Part 1: HTTP Methods

In `app.py`, add a route `/add` to return the `add.html` template.
Name the method `add_student_route()`.

Edit your `add_student_route()` method for the route to `/add` so that
it takes both GET and POST requests.

If a GET request comes in, return the `add.html` template like before,
but if a POST request comes in, print the string `'Received POST request!'`
and then return the same template.



### Part 2: Creating a Form

In the `add.html` template, between the `<form>` tags, add two `<input>`
tags, one with `name="student_name"` and one with `name="student_year"`.

You can add in a `placeholder` attribute so that the input boxes will tell the user what to write:
`<input type="text" placeholder="Write Name" name="student_name">


### Part 3: POSTing Forms

Now we need to add to the POST method of the `/add` route we have created
in `app.py`. If the request is a POST request, we want to use the form data to add a new student to the database. Afterwards, you can still return the same template as before.

*Hint*: Look at the `add_student()` method in `databases.py`.

*Hint*: The `name` of the form element corresponds to the value of that
element in `request.form`. 

## Independent Lab: Deleting an entry


### Part 1

In `student.html`, add a `<form>` tag that has one `<input>` element
with `type="submit"` and `value="delete"`. Edit the form element
so that when submitted, it makes a POST to `/delete/<student_id>`, where
the `student_id` is of the article currently being viewed. 

*Hint*: You will need to add an `action` attribute to `<form>` so that it directs to the right URL. For example, if we wanted the form to take us to the home page, in the `form` tag we would write: `<form action="/delete/<student_id>`

### Part 2

In `app.py`, create a new route to `/delete/<int:student_id>` that
only accepts POST requests.

### Part 3

In the new route, use the database function `delete_student_id` to
delete the student entry with the given `student_id`.

### Part 4

Then redirect the user back to the home page by returning the home page
using one of the Flask functions we've learned.
*Hint*: You can do this by returning `redirect(url_for(*where you want to go*))`

### Part 5

You can now make your website look prettier using CSS and additional
templating, as you've learned in the past few days.

## Lab Bonus: Updating an entry

### Part 1

For this part, you'll need to create a new template called `edit.html`.
Make sure you place it in the `templates` folder!

### Part 2

Add a form to this new template for editing a student's `finished_lab`
status. What information is necessary to edit the database entry?

### Part 3

In `app.py`, add a new route to `/edit/<int:student_id>`. When a GET
request is made to this route, it should return the template we just made.
When a POST request is made to this route, it should make a database call
to update the given entry and then return the student's page.

### Part 4

In `student.html`, add a link to the new route for editing. You should
now be able to navigate the website and add new students, delete students,
and update whether individual students have completed their labs.

## Additional bonuses

1. Add any links between pages that you think are missing.

1. Add a way to search for student by name, using GET query string parameters.

2. Figure out a way to add a photo to each student's page.
