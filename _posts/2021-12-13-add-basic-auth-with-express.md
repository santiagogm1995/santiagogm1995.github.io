## Add basic auth with Express

In this post I'll show you how to add basic auth to your application. 

---

### Prerequisites.

Setup with my personal versions:

- Nodejs (https://nodejs.org/en/): v14.17.6
- npm: 6.14.15

#### Script code:

Firt we need to install the dependencies:

```sh
    npm install express #version 4.17.1
    npm install express-basic-auth #version 1.2.1
```

Add the following code to your server.js file:

```js
const app = express();
const express = require("express");
app.use(
  basicAuth({
    users: { admin: "admin" },
  })
);
```

And that's it. Now you can access your application with basic auth.

See you in the next post. :D