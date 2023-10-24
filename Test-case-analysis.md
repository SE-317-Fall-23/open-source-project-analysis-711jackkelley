# Assignment Submission

## Project Selected: Express

## I. Introduction
In this section, I will be giving a description and an analysis of two test cases from open-source project Express. The two test cases I've selected are app.route.js and app.engine.js

## II. Test Case 1: app.route.js
### A. Description
This test case is meant to validate various uses and functionalities of the app.route function
### B. Gherkin Syntax (if applicable)

### C. Test Steps
1. Create an instance of app, create an api route "/foo" with a get method that sends "get, and a post method that sends "post". Send a post request to "/foo" and validate the response is "post".
2. Create same endpoint as above with an all method that calls next(). Send a post request to "/foo" and validate the response is "post.
3. Create an instance of app, create an api route "/:foo" with a get method that sends the name of the requested end point. Send a get request to "/:foo" and validate the response is "test".
4. Create an instance of app, create an api route "/:foo" with no methods. Send a get request to "/:foo" and validate the response is 404.
### D. Code Segments Under Test
```Java
express();
app.route();
request();
res.send();
```
### E. Initial State
Uninstantiated Express app
### F. Transition
1. Create an endpoint in the app "/foo" and set the get and post methods
2. Create an endpoint in the app "/foo" and set the all, get and post methods
3. Create an endpoint in the app "/:foo" and set the get method
4. Create an endpoint in the app "/:foo"
### G. Expected State
1. Calling the post method should return "post", and calling the get method should return "get"
2. Calling the post method should return "post", calling the get method should return "get" and calling the all method should do both.
3. Calling the get method at endpoint "/test" should return "test".
4. Calling any method at endpoint "/:foo" should return 404, more specifically it shouldn't error out.

## III. Test Case 2: app.response.js
### A. Description
This test case is meant to validate various uses and functionalities of the response class
### B. Gherkin Syntax (if applicable)

### C. Test Steps
1. Create an instance of app, set app's response.shout() function to send the input string as uppercase, set app to respond with the result of shout('hey'), make a get request at "/" and validate the response is "HEY".
2. Create an instance of app1, create an instance of app2, set app1's response function to send the input string as uppercase, set app1 to respond with the result of shout('foo'), set app2 to respond with the result of shout('foo'), make a get request at "/" for app1 and validate the response is 200, make a get request at "/" for app2 and validate the response is 500.
3.  Create an instance of app1, create an instance of app2, set app1's response function to send the input string as uppercase, set app2 as a sub of app1, set app1 to respond with the result of shout('foo'), set app2 to respond with the result of shout('foo'), make a get request at "/" for app1 and validate the response is 200, make a get request at "/" for app2 and validate the response is 200.
4.  Create an instance of app1, create an instance of app2, set app1's response function to send the input string as uppercase, set app2's response function to append '!' to the input string, set app2 as a sub of app1, set app1 to respond with the result of shout('foo'), set app2 to respond with the result of shout('foo'), make a get request at "/" for app1 and validate the response is "FOO", make a get request at "/" for app2 and validate the response is "foo!".
5.  Create an instance of app1, create an instance of app2, set app1's response at endpoint "/sub/foo" to send the input string as uppercase, set app2's response function to append '!' to the input string, set app2 as a sub of app1, set app1 to respond with the result of shout('foo'), set app2 to respond with the result of shout('foo'), make a get request at "/sub" for app1 and validate the response is "foo!", make a get request at "/sub/foo" for app1 and validate the response is "FOO".
### D. Code Segments Under Test
- Identify specific code segments or functions that are being tested in this case.
```Java
express()
after()
res.shout()
app.use()
request()
```
### E. Initial State
1. Uninstantiated app
2. Uninstantiated app1 and app2
3. Uninstantiated app1 and app2
4. Uninstantiated app1 and app2
5. Uninstantiated app1 and app2
### F. Transition
1. Set the apps response.shout() function to send the input string as uppercase, and set the endpoint to use the response.shout() function with the string "hey".
2. Set app1's response.shout() function to send the input string as uppercase, set app1's endpoint to use the response.shout() function with the string "foo", set app2's endpoint to use the response.shout() function with string "foo".
3. Set app1's response.shout() function to send the input string as uppercase, set app2 as a sub of app1, set app1's endpoint to use the response.shout() function with the string "foo", set app2's endpoint to use the response.shout() function with string "foo".
4. Set app1's response.shout() function to send the input string as uppercase, set app2's response.shout() function to send the input string with a '!' appended, set app2 as a sub of app1, set app1's endpoint to use the response.shout() function with the string "foo", set app2's endpoint to use the response.shout() function with string "foo".
5. Set app1's response.shout() function to send the input string as uppercase, set app2's response.shout() function to send the input string with a '!' appended, set app2 as a sub of app1, set app1 at endpoint "/sub/foo" to use the response.shout() function with the string "foo", set app2's endpoint to use the response.shout() function with string "foo".
### G. Expected State
1. The shout() function changes the input string to uppercase, returning "HEY"
2. The shout() function for app1 changes the input string to uppercase, returning "FOO". The shout() function for app2 should return a 500 response, as updating app1's response.shout() shouldn't affect app2's response.shout().
3. The shout() function for app1 changes the input string to uppercase, returning "FOO". The shout() function for app2 should also return "FOO", as app2 being a sub of app1 should default to the response of app1.
4. The shout() function for app1 changes the input string to uppercase, returning "FOO". The shout() function for app2 should return "foo!", as app2 had it's own response.shout() function set and it should override the default (app1) when set.
5. The shout() function for app1 at "/sub" should return "foo!", as app2 is the sub endpoint, and the shout() function for app1 at "/sub/foo" changes the input string to uppercase, returning "FOO", because the function for "sub/foo" at app1 was set to return an uppercase string. This test ensures that the child doens't pollute the parent (meaning that endpoints starting with "sub" for app1 shouldn't be overridden by app2 just because it is a sub of app1).

