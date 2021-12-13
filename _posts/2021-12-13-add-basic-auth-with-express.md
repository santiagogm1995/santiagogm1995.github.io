## Add basic auth with Express

In this post I'll show you how to add basic auth to your application. 

---

### Prerequisites.

Setup with my personal versions:

- Nodejs (https://nodejs.org/en/): v14.17.6
- npm: 6.14.15

#### Script code:

Firt we need to install the dependencies:

```bash
    npm install express #version 4.17.1
    npm install express-basic-auth #version 1.2.1
```

Add the following code to your server.js file:

```javascript
const app = express();
const express = require("express");
app.use(
  basicAuth({
    users: { admin: "admin" },
  })
);
```

#### Test it with Postman:

Error:
<img src="./img/basic.auth-error.png">

Correct:

<img src="./img/basic.auth-okey.png">