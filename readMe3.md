# Middleware 

## Middleware

Middleware plays a crucial role in web development, particularly in frameworks like Express. It refers to a series of functions that execute in the request-response cycle. Essentially, middleware functions run in the middle of our request, which is why they are called middleware.

In our current pizza application, we are already using some middleware in our app.js. You can spot them by looking for the app.use() method.

```javascript
app.use(express.json())
app.use(express.urlencoded({extended:true}))

```
These middleware functions help parse our incoming data, operating between the request and response. 

We are also using middleware to set up paths to our controller:

```javascript 
app.use('/pizzas',pizzaController)
```
So, we have already experienced how useful middleware is.

## What is Express middleware ?

Express middleware is a callback function that has access to the request object (`req`), response object (`res`), and sometimes the next middleware callback (`next`). These middleware functions are invoked between the time the server receives the request and sends the response.

Middleware functions can executes any javascript operation inside the callback function. Such as:
- Read and modify the `req` and `res` objects.
- Read and write to a file or database.
- Send HTTP request to other servers.
  
However, middleware must either end the request-response cycle with a method like `res.send()` or call the next middleware callback with `next()`. This method ensures your middleware pipeline moves on to the next middleware or route in line. Without it, the pipeline will stop.


## why is it useful 

Middleware functions are incredibly useful as they can perform tasks like logging, authentication, error handling, data parsing, compression, and caching. Middleware enhances application functionality, modularize code, and enables code reuse across different parts of the application.

## Another Example 

Lets add another piece of middleware for a route not found error
