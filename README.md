# API Documentation

## Configuration

*Endpoint Development*

```
http://digital-extension.dev.konabackend.com
```

## Create new Customer

Example
```
POST /customers
Content-Type: application/json
X-TOUCHPOINT-TOKEN: 91bc44b5-2bde-a04b-6e4b-1253b00231e6

{
  "hash": "string",
  "firstName": "string",
  "lastName": "string",
  "email": "string",
  "birthday": "string",
  "country": "string",
  "language": "string",
  "gender": "string",
  "title": "string",
  "jobTitle": "string",
  "weiboId": "string",
  "identifyNumber": "string",
  "luxuarytrue": "string",
  "type": "string",
  "address": {
    "line1": "string",
    "line2": "string",
    "line3": "string",
    "line4": "string",
    "postCode": "string",
    "city": "string",
    "country": "string"
  },
  "phone": {
    "mobile": "string",
    "personal": "string",
    "professional": "string"
  }
}
```



### Integration example

http://jsfiddle.net/gjh5xzfo/1/

<iframe width="100%" height="300" src="//jsfiddle.net/gjh5xzfo/1/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

## Customer Login with email and password hash


*X-TOUCHPOINT-TOKEN* is the Touchpoint token

Example
```
POST /customers/login
Content-Type: application/json
X-TOUCHPOINT-TOKEN: 91bc44b5-2bde-a04b-6e4b-1253b00231e6

{ 
    "email" : "santiago@konacloud.io", 
    "hash" : "test" 
}
```

### Integration example

http://jsfiddle.net/gng3o5sm/5/

<iframe width="100%" height="300" src="//jsfiddle.net/gng3o5sm/5/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>



## Customer Facebook login

*X-FACEBOOK-TOKEN* is the Facebook access token

Example
```
POST /customers/login-with-facebook HTTP/1.1
Content-Type: application/json
X-TOUCHPOINT-TOKEN: 91bc44b5-2bde-a04b-6e4b-1253b00231e6
X-FACEBOOK-TOKEN: CAACEdEose0cBACKhtEKEa13dDACB30yd6E8JavLaEv61OovqTIQcvw0jXjNwAimi0rf8AGLHAxRZAq8WXiPp30ooC3MWElwLgcyuaIZAf0Nba7QypVJtVLGyp2SUN3wCIJeGKiKdrOsXCA0inx28iUCL7DTeF9X2JYuUjlF37JUOvfY0IQZCZCo0lsKwOAJraq17UuTZAnnqAMNrSp2hs
Cache-Control: no-cache

{}
```

### Integration example

http://jsfiddle.net/5uuwqdzd/4/

<iframe width="100%" height="300" src="//jsfiddle.net//5uuwqdzd/4/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

## Customer update profile

Example
```
PUT /customers HTTP/1.1
Content-Type: application/json
X-TOUCHPOINT-TOKEN: 91bc44b5-2bde-a04b-6e4b-1253b00231e6
X-CUSTOMER-DIGITAL-EXTENSION-TOKEN: OpENRcnBByUWi/8Fcj/TxeWpupWM6mLracPHbezoHvI=
Cache-Control: no-cache

{ "jobTitle" : "Software Architect", "title" : "Ing", "hash" : "1234567" }
```

### Integration example

http://jsfiddle.net/4gLLgw4s/1/

<iframe width="100%" height="300" src="//jsfiddle.net/4gLLgw4s/1/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

## Fire Interaction

Example
```
POST /customers/interaction/5633a9b08ee14028271581f0
Content-Type: application/json
X-TOUCHPOINT-TOKEN: 91bc44b5-2bde-a04b-6e4b-1253b00231e6
X-CUSTOMER-DIGITAL-EXTENSION-TOKEN: OpENRcnBByUWi/8Fcj/TxeWpupWM6mLracPHbezoHvI=
Cache-Control: no-cache

{ "test" : "hola" }

```
### Integration example


http://jsfiddle.net/4gLLgw4s/7/

<iframe width="100%" height="300" src="//jsfiddle.net/4gLLgw4s/7/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>



```
