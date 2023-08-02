Express Routers 

Routers are a nice way to keep your code organized on an Express server. As more and more routes are added to our application, things can get messy or complicated. If we take a look at our `app.js`:

<!-- show code -->

it would be cleaner and easier to work with if we sectioned off our routes into a separate file, this is the purpose of Express router.

This also follows the **Model View Controller** structure, by extracting our routes out into a controller folder, we will look into that a little more towards the end.

Lets begin setting up our router, inside our project directory we need to create a new folder that will store all of our controllers.

```bash 
mkdir controllers
```

Inside this new `controllers` directory let's create a file to store all your previous `/pizza` routes:

```bash
touch pizza_controller.js
```

This new `pizza_controller.js` will hold all of our `/pizza` routes, so any changes or updates should be done only in this file. Let open this file and begin adding the necessary express methods to get our router functionality:

***pizza_controller.js***
```javascript
const express = require('express'); 
const router = express.Router()
```

The second line is very important, as it is what will create our router (i.e. the "controller"). Finally let's make our router exportable. 

***pizza_controller.js***
```javascript
const express = require('express'); 
const router = express.Router()

module.exports = router
```
We need our router to be exportable because we will be importing it to our `app.js` in replacement of the current routes. 

Lets take a look at our `app.js` and any routes that have to do with `/pizzas` should be moved to our `pizza_controller`