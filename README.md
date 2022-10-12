# Putting it All Together: Client-Server Communication

## Learning Goals

- Understand how to communicate between client and server using fetch, and how
  the server will process the request based on the URL, HTTP verb, and request
  body
- Debug common problems that occur as part of the request-response cycle

## Introduction

Just like the last lesson, we've got code for a React frontend and Rails API
backend set up. This time though, it's up to you to use your debugging skills to
find and fix the errors!

To get the backend set up, run:

```console
$ bundle install
$ rails db:migrate db:seed
$ rails s
```

Then, in a new terminal, run the frontend:

```console
$ npm install --prefix client
$ npm start --prefix client
```

Confirm both applications are up and running by visiting
[`localhost:4000`](http://localhost:4000) and viewing the list of toys in your
React application.

## Deliverables

In this application, we have the following features:

- Display a list of all the toys
- Add a new toy when the toy form is submitted
- Update the number of likes for a toy
- Donate a toy to Goodwill (and delete it from our database)

The code is in place for all these features on our frontend, but there are some
problems with our API! We're able to display all the toys, but the other three
features are broken.

Use your debugging tools to find and fix these issues.

There are no tests for this lesson, so you'll need to do your debugging in the
browser and using the Rails server logs and `byebug`.

**Note**: You shouldn't need to modify any of the React code to get the
application working. You should only need to change the code for the Rails API.

As you work on debugging these issues, use the space in this README file to take
notes about your debugging process. Being a strong debugger is all about
developing a process, and it's helpful to document your steps as part of
developing your own process.

## Your Notes Here

- Add a new toy when the toy form is submitted

  - How I debugged:
  First atttempted to sumbit a toy with the form and took note of what happened in the console.
  Got a 500 error meaning there was a error within the server so I checked what the server logs had to say and there was a NameError in the toy controller, on the create method. The Toy class was spelt as Toys.
  After updating the controller and submitting a toy I got a 201 and the toy was submitted successfully.

- Update the number of likes for a toy

  - How I debugged:
  When liking a toy I would get an unpermitted parameter inthe console so first course of action was to permit it. After that I was still getting the same error in the browsers console and on reloading of the page the like update was indeed succesful. The next course of action for me was to look at what react was receiving back from the server. The server wasnt sending anything back so I had it send back the updated object and that fixed the issue as thats what is was attempting to didsplay

- Donate a toy to Goodwill (and delete it from our database)

  - How I debugged: 
  In the browsers console I was getting a 404 meaning there was no route to be found. Taking a look in the routes i saw there was no "DESTROY" route. After adding one in the donate button worked as expected
