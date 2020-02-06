# Node PG

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Non-blocking PostgreSQL client for Node.js. Pure JavaScript and optional native libpq bindings.

Requirements:
  - nodejs
  - dotenv package
  - pg package

# Installation

```node
$ npm init -y
$ npm i --save dotenv
$ npm i pg
```
  - if you want one liner code just add '&&' per line 
    (command && command)
# Directory Structure
```bash
├── node_modules
│   ├── ...
├── Problems
│   ├── problem1.js
│   ├── problem2.js
│   ├── problem3.js
│   ├── problem4.js
│   ├── problem5.js
│   ├── problem6.js
│   ├── problem7.js
├── .env
├── package
├── package-lock
├── README.md
└── .gitignore
```
# Challenges
| Script | Original Command |
| ------ | ------ |
| magallen-prob1 | node Problems/problem1.js |
| magallen-prob2 | node Problems/problem2.js |
| magallen-prob3 | node Problems/problem3.js |
| magallen-prob4 | node Problems/problem4.js |
| magallen-prob5 | node Problems/problem5.js |
| magallen-prob6 | node Problems/problem6.js |
| magallen-prob7 | node Problems/problem7.js |

To run the challengs
```bash
$ npm run <script>
```

### Possible error 

`${Node:12044}`
```js
(node:12044) DeprecationWarning: Implicit disabling of certificate verification is deprecated and will be removed in pg 8. Specify `rejectUnauthorized: true` to require a valid CA or `rejectUnauthorized: false` to explicitly opt out of MITM protection.
```
`${getaddrinfo}` Undefined 
```js
Error: getaddrinfo ENOTFOUND undefined
    at GetAddrInfoReqWrap.onlookup [as oncomplete] (dns.js:60:26) {
  errno: 'ENOTFOUND',
  code: 'ENOTFOUND',
  syscall: 'getaddrinfo',
  hostname: 'undefined'
 ```

### Solution 

Error Code:`${Node:12044}`
Change 
```js
ssl: true,
```
To
```js
ssl: { rejectUnauthorized: false, },
```

Complete view of solution
```js
    const pool = new Pool({
    user: `${process.env.DB_USER}`,
    host: `${process.env.DB_HOST}`,
    database: `${process.env.DB_DATABASE}`,
    password: `${process.env.DB_PASSWORD}`,
    port: process.env.DB_PORT,
    ssl: { 
        rejectUnauthorized: false, 
    },
})
```

##### Error-Message: getaddrinfo ENOTFOUND undefined
Make sure you add the required module at the top of the script
```js
require('dotenv').config()
```

License
----

MIT


**Free Software, Yeah!!**