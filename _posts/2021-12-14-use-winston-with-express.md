## Use winston with Express

In this post I'll show you how to use winston with Express. Winston is a logging library for Node.js and it's used in many projects.

---

### Prerequisites.

Installed programs: (the versions are only in my case)

- Nodejs (https://nodejs.org/en/): v14.17.6
- npm: 6.14.15

### 1. Setup winston in your project.

From the command line you'll need to install winston with the following command:

```bash
    npm install winston #In my case I used version 3.3.3
```

### 2. Create a logger and run express.

Add the following code to your server.js file:

```js
const winston = require("winston");
const { splat, combine, timestamp, printf } = winston.format;

//Format logs
const customFormat = printf(({ timestamp, level, message, meta }) => {
  return `{"level":"${level}","time":"${Intl.DateTimeFormat("es-ES", {
    dateStyle: "short",
    timeStyle: "long",
  }).format(new Date(timestamp))}","content":${JSON.stringify(message)}}`;
});

//Create the logger
const logger = winston.createLogger({
  format: combine(timestamp(), splat(), customFormat),
  transports: [new winston.transports.Console()],
});

```

You'll see something like this:

```
{"level":"info","time":"14/12/21 20:01:30 CET","content":"Server running on port 3000"}
``` 

#### Example repository:

[winston-with-express](https://github.com/santiagogm1995/winston-with-express.git).

See you in the next post. :D