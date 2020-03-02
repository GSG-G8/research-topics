# Sessions

## What is a "Cookie" ?
A cookie is a small piece of text stored on a user's computer by their browser. Common uses for cookies are authentication, storing of site preferences, shopping cart items, and server session identification.

Each time the users' web browser interacts with a web server it will pass the cookie information to the web server. Only the cookies stored by the browser that relate to the domain in the requested URL will be sent to the server. This means that cookies that relate to www.example.com will not be sent to www.exampledomain.com. ([Lasso](http://www.lassosoft.com/Tutorial-Understanding-Cookies-and-Sessions))


## What is a "Session" ?
A session can be defined as a server-side storage of information that is desired to persist throughout the user's interaction with the web site or web application. 

Instead of storing large and constantly changing information via cookies in the user's browser, only a unique identifier is stored on the client side (called a "session id"). This session id is passed to the web server every time the browser makes an HTTP request. The web application pairs this session id with it's internal database and retrieves the stored variables for use by the requested page. ([Lasso](http://www.lassosoft.com/Tutorial-Understanding-Cookies-and-Sessions))

### what are the different ways of managing sessions in express?

By default Express requests are sequential and no request can be linked to each other. There is no way to know if this request comes from a client that already performed a request previously.
Users cannot be identified unless using some kind of mechanism that makes it possible.
That’s what sessions are.

ther are two way to manage cookies in express
1. cookie-session
2. express-session

## cookie-session
This is npm module  stores the session data on the client within a cookie.
### features
* does not require any database / resources on the server side. 
* cookie-session can simplify certain load-balanced scenarios.
* cookie-session can be used to store a “light” session and include an identifier to look up a database-backed secondary store to reduce database lookups.

dis-advantage:
* total session data cannot exceed the browser’s max cookie size.

### Install
This is a Node.js module available through the npm registry. Installation is done using the npm install command:

```
$ npm install cookie-session
```



## express-session
* express-session is more abstract, it supports different session stores (like files, DB, cache and whatnot). 

 * express-session store the session id in a cookie, and keep the data server-side. The client will receive the session id in a cookie, and will send it along with every HTTP request.

### install
```
npm install express-session
```

### syntax
This is a middleware, so you install it in Express using
``` javascript
const express = require('express')
const session = require('express-session')

const app = express()
app.use(session({
  'secret': '343ji43j4n3jn4jk3n'
}))
```
After this is done, all the requests to the app routes are now using sessions.

secret is the only required parameter, but there are many more you can use. It should be a randomly unique string for your application.

The session is attached to the request, so you can access it using req.session here:
``` javascript
app.get('/', (req, res, next) => {
  req.session.name = 'test'
console.log(req.session.name) // 'test'
}
```
## 

## Session Express Example by express-session npm :
[Express-Session npm Documentation](https://www.npmjs.com/package/express-session)

Install express-session npm
```
$ npm install express-session
```

---
Required
```
var session = require('express-session')
```
### NOTE :+1: 
Since version 1.5.0, the cookie-parser middleware no longer needs to be used for this module to work. 

### Options 


| flag | description
| -------- | -------- 
| cookie   | { path: '/', httpOnly: true, secure: false, maxAge: null }
| cookie.domain|Domain Set-Cookie attribute. By default, no domain is set, and most clients will consider the cookie to apply to only the current domain.|
|cookie.expires|Date object to be the value for the Expires Set-Cookie
|cookie.httpOnly|boolean value for the HttpOnly Set-Cookie|
|cookie.maxAge|number (in milliseconds) to use when calculating the Expires Set-Cookie|

### example 
```
app.set('trust proxy', 1) // trust first proxy
app.use(session({
  secret: 'name',
  resave: false,
  saveUninitialized: true,
  cookie: { secure: true }
}))
```
example of enabling NODE_ENV in express for testing:
```

var sess = {
  secret: 'keyboard cat',
  cookie: {}
}

if (app.get('env') === 'production') {
  app.set('trust proxy', 1) // trust first proxy
  sess.cookie.secure = true // serve secure cookies
}

app.use(session(sess))
```

### Distroy session

![](https://i.imgur.com/P3z6Mf2.png)
```

req.session.destroy(function(err) {
  // cannot access session here
})
```
### handle lost connections to Redis?
you can handle it by including a "session check":

```
app.use(session(/* setup session here */))
app.use(function(req, res, next) {
  if (!req.session) {
    return next(new Error('oh no')) // handle error
  }
  next() // otherwise continue
})
```
