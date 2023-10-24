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
// express();
// app.route();
// request();
// res.send();
```
### E. Initial State
1. Uninstantiated Express app
### F. Transition
- Explain the actions or events that trigger a change in the system's state.
### G. Expected State
- Clearly outline the expected state or outcome after the test steps have been completed.

## III. Test Case 2: [Name of Test Case]
### A. Description
- Provide a concise overview of the purpose of the second test case.
### B. Gherkin Syntax (if applicable)
- If you choose to use Gherkin syntax, write the Gherkin scenario for this test case.
### C. Test Steps
- Enumerate the sequence of steps or actions involved in this test case.
### D. Code Segments Under Test
- Identify specific code segments or functions that are being tested in this case.
```Java
// Enter code
```
### E. Initial State
- Describe the initial state or conditions of the system or component before executing the test.
### F. Transition
- Explain the actions or events that trigger a change in the system's state.
### G. Expected State
- Clearly outline the expected state or outcome after the test steps have been completed.

