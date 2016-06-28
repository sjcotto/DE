# API Documentation

## Configuration

*Endpoint Development*

```
http://digital-extension.dev.konabackend.com
```

## Create new Customer

** Required headers **

- X-TOUCHPOINT-TOKEN

### Request
```
POST /consumers
Content-Type: application/json
X-TOUCHPOINT-TOKEN: 91bc44b5-2bde-a04b-6e4b-1253b00231e6

{
  "hash": "123456",
  "firstName": "Consumer 2 name",
  "lastName": "Consumer last name",
  "email": "c6@email.com",
  "birthday": "1989-06-20",
  "languageCode": "es",
  "gender": "M",
  "title": "Ingeniero",
  "jobTitle": "Ingeniero",
  "type" : "CI",
  "identifyNumber": "4492569",
  "luxuarytrue" : "true",
  "type": "CI",
  "countryCode": "uy",
  "address": {
    "line1": "Benito blanco 780",
    "postCode": "11220",
    "city": "Montevideo",
    "state": "Montevideo"
  },
  "phone": {
    "mobile": "123",
    "personal": "456",
    "professional": "789"
  },
  "optInBrand" : true
}
```

The boolean optInBrand indicates that the consumer accepted the brand

### Response

#### Success

- HTTP STATUS CODE: 200

- BODY

```
{
    "_id": "56421ef5b0e835dcde17bbcb",
...
```


#### Error messages

** Body error messages **

The body response has the following format

```js
{
  "message" : "hash is required",
  "code": 20,
  "field" : "hash"
}
```


| HTTP STATUS CODE | MESSAGE                                           | FIELD     |
|------------------|---------------------------------------------------|-----------|
| 400              | hash is required                                  | hash      |
| 400              | hash invalid, the mínimum length is 6             | hash      |
| 400              | firstName is required                             | firstName |
| 400              | email is required                                 | email     |
| 400              | birthday is required                              | birthday  |
| 400              | gender is required                                | gender    |
| 400              | Invalid gender, accepted values are 'M' or 'F'    | gender    |
| 400              | Invalid birthday, accepted format is 'yyyy-mm-dd' | birthday  |

** Invalid headers **

| HTTP STATUS CODE | MESSAGE                                           | FIELD              | CODE |
|------------------|---------------------------------------------------|--------------------|------|
| 400              | X-TOUCHPOINT-TOKEN Header is required             | X-TOUCHPOINT-TOKEN | 10   |
| 400              | Invalid X-TOUCHPOINT-TOKEN                        | X-TOUCHPOINT-TOKEN | 11   |


### JS Integration example

http://jsfiddle.net/gjh5xzfo/1/

<iframe width="100%" height="300" src="//jsfiddle.net/gjh5xzfo/1/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

## Customer Login with email and password hash

** Required headers **

- X-TOUCHPOINT-TOKEN

### Request
```
POST /consumers/login
Content-Type: application/json
X-TOUCHPOINT-TOKEN: 91bc44b5-2bde-a04b-6e4b-1253b00231e6

{ 
    "email" : "santiago@konacloud.io", 
    "hash" : "test" 
}
```

### Response

#### Success

- HTTP STATUS CODE: 200
- BODY

```
{
    "token": "VhcD2ACEZTMX4V5azM/HM3E1kNl9WYbrjCAA9a/YZsE="
}
```

#### Error messages

** Body error messages **

The body response has the following format

```js
{
  "message" : "hash is required",
  "code": 20,
  "field" : "hash"
}
```


| HTTP STATUS CODE | MESSAGE                                           | FIELD     |
|------------------|---------------------------------------------------|-----------|
| 400              | hash is required                                  | hash      |
| 400              | hash invalid, the mínimum length is 6             | hash      |
| 400              | email is required                                 | email     |


** Invalid headers **

| HTTP STATUS CODE | MESSAGE                                           | FIELD              | CODE |
|------------------|---------------------------------------------------|--------------------|------|
| 400              | X-TOUCHPOINT-TOKEN Header is required             | X-TOUCHPOINT-TOKEN | 10   |
| 400              | Invalid X-TOUCHPOINT-TOKEN                        | X-TOUCHPOINT-TOKEN | 11   |
| 400              | Customer email not found                          | email              | 20   |
| 400              | Customer email not found on Touchpoint            | email              | 21   |
| 400              | Invalid User or Password                          | email              | 22   |

### JS Integration example

http://jsfiddle.net/gng3o5sm/5/

<iframe width="100%" height="300" src="//jsfiddle.net/gng3o5sm/5/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

## Customer Facebook login

** Required headers **

- X-TOUCHPOINT-TOKEN
- X-FACEBOOK-TOKEN

Facebook access token https://developers.facebook.com/docs/facebook-login/access-tokens

### Request
```
POST /consumers/fb-login HTTP/1.1
Content-Type: application/json
X-TOUCHPOINT-TOKEN: 91bc44b5-2bde-a04b-6e4b-1253b00231e6
X-FACEBOOK-TOKEN: CAACEdEose0cBACKhtEKEa13dDACB30yd6E8JavLaEv61OovqTIQcvw0jXjNwAimi0rf8AGLHAxRZAq8WXiPp30ooC3MWElwLgcyuaIZAf0Nba7QypVJtVLGyp2SUN3wCIJeGKiKdrOsXCA0inx28iUCL7DTeF9X2JYuUjlF37JUOvfY0IQZCZCo0lsKwOAJraq17UuTZAnnqAMNrSp2hs
Cache-Control: no-cache

{}
```

### Response

#### Success

- HTTP STATUS CODE: 200
- BODY

```
{
    "token": "VhcD2ACEZTMX4V5azM/HM3E1kNl9WYbrjCAA9a/YZsE="
}
```

#### Error messages

The body response has the following format

```js
{
  "message" : "",
  "code": 20,
  "field" : ""
}
```

** Invalid headers **

| HTTP STATUS CODE | MESSAGE                                           | FIELD              | CODE |
|------------------|---------------------------------------------------|--------------------|------|
| 400              | X-TOUCHPOINT-TOKEN Header is required             | X-TOUCHPOINT-TOKEN | 10   |
| 400              | Invalid X-TOUCHPOINT-TOKEN                        | X-TOUCHPOINT-TOKEN | 11   |
| 400              | X-FACEBOOK-TOKEN Header is required               | X-FACEBOOK-TOKEN   | 25   |
| 500              | [FB error]                                        | X-FACEBOOK-TOKEN   | -    |


### JS Integration example

http://jsfiddle.net/5uuwqdzd/5/

<iframe width="100%" height="300" src="//jsfiddle.net//5uuwqdzd/5/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

## Customer update profile

** Required headers **

- X-TOUCHPOINT-TOKEN
- X-CUSTOMER-DIGITAL-EXTENSION-TOKEN

The X-CUSTOMER-DIGITAL-EXTENSION-TOKEN from the login API body response.

### Request
```
PUT /consumers HTTP/1.1
Content-Type: application/json
X-TOUCHPOINT-TOKEN: 91bc44b5-2bde-a04b-6e4b-1253b00231e6
X-CUSTOMER-DIGITAL-EXTENSION-TOKEN: OpENRcnBByUWi/8Fcj/TxeWpupWM6mLracPHbezoHvI=
Cache-Control: no-cache

{ "jobTitle" : "Software Architect", "title" : "Ing", "hash" : "1234567" }

```

### Response

#### Success

- HTTP STATUS CODE: 200

#### Error messages

** Invalid headers **

| HTTP STATUS CODE | MESSAGE                                           | FIELD              | CODE |
|------------------|---------------------------------------------------|--------------------|------|
| 400              | X-TOUCHPOINT-TOKEN Header is required             | X-TOUCHPOINT-TOKEN | 10   |
| 400              | Invalid X-TOUCHPOINT-TOKEN                        | X-TOUCHPOINT-TOKEN | 11   |
| 400              | X-CUSTOMER-DIGITAL-EXTENSION-TOKEN Header is required | X-CUSTOMER-DIGITAL-EXTENSION-TOKEN   | 23   |
| 400              |Invalid X-CUSTOMER-DIGITAL-EXTENSION-TOKEN | X-CUSTOMER-DIGITAL-EXTENSION-TOKEN | 24   |


### JS Integration example

http://jsfiddle.net/4gLLgw4s/1/

<iframe width="100%" height="300" src="//jsfiddle.net/4gLLgw4s/1/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

## Logout

** Required headers **

- X-TOUCHPOINT-TOKEN
- X-CUSTOMER-DIGITAL-EXTENSION-TOKEN

### Request
```
POST /consumers/logout
Content-Type: application/json
X-TOUCHPOINT-TOKEN: 91bc44b5-2bde-a04b-6e4b-1253b00231e6
X-CUSTOMER-DIGITAL-EXTENSION-TOKEN: OpENRcnBByUWi/8Fcj/TxeWpupWM6mLracPHbezoHvI=
Cache-Control: no-cache

```
### Response

#### Success

- HTTP STATUS CODE: 200

#### Error messages

** Invalid headers **

| HTTP STATUS CODE | MESSAGE                                           | FIELD              | CODE |
|------------------|---------------------------------------------------|--------------------|------|
| 400              | X-TOUCHPOINT-TOKEN Header is required             | X-TOUCHPOINT-TOKEN | 10   |
| 400              | Invalid X-TOUCHPOINT-TOKEN                        | X-TOUCHPOINT-TOKEN | 11   |
| 400              | X-CUSTOMER-DIGITAL-EXTENSION-TOKEN Header is required | X-CUSTOMER-DIGITAL-EXTENSION-TOKEN   | 23   |
| 400              |Invalid X-CUSTOMER-DIGITAL-EXTENSION-TOKEN | X-CUSTOMER-DIGITAL-EXTENSION-TOKEN | 24   |


## Recovery password

** Required headers **

- X-TOUCHPOINT-TOKEN

### Request
```
POST /consumers/recovery-password
Content-Type: application/json
X-TOUCHPOINT-TOKEN: 91bc44b5-2bde-a04b-6e4b-1253b00231e6
Cache-Control: no-cache

{ email : consumer@email.com}
```
### Response

#### Success

- HTTP STATUS CODE: 200

#### Error messages

** Invalid headers **

| HTTP STATUS CODE | MESSAGE                                           | FIELD              | CODE |
|------------------|---------------------------------------------------|--------------------|------|
| 400              | X-TOUCHPOINT-TOKEN Header is required             | X-TOUCHPOINT-TOKEN | 10   |
| 400              | Invalid X-TOUCHPOINT-TOKEN                        | X-TOUCHPOINT-TOKEN | 11   |

This operation send a email to the email inside payload

## Fire Interaction

** Required headers **

- X-TOUCHPOINT-TOKEN
- X-CUSTOMER-DIGITAL-EXTENSION-TOKEN

** Required URL params **

- Interaction ID

### Request
```
POST /interactions/:id
Content-Type: application/json
X-TOUCHPOINT-TOKEN: 91bc44b5-2bde-a04b-6e4b-1253b00231e6
X-CUSTOMER-DIGITAL-EXTENSION-TOKEN: OpENRcnBByUWi/8Fcj/TxeWpupWM6mLracPHbezoHvI=
Cache-Control: no-cache

{ "test" : "hola" }

```

### Response

#### Success

- HTTP STATUS CODE: 200

#### Error messages

** Invalid headers **

| HTTP STATUS CODE | MESSAGE                                           | FIELD              | CODE |
|------------------|---------------------------------------------------|--------------------|------|
| 400              | X-TOUCHPOINT-TOKEN Header is required             | X-TOUCHPOINT-TOKEN | 10   |
| 400              | Invalid X-TOUCHPOINT-TOKEN                        | X-TOUCHPOINT-TOKEN | 11   |
| 400              | X-CUSTOMER-DIGITAL-EXTENSION-TOKEN Header is required | X-CUSTOMER-DIGITAL-EXTENSION-TOKEN   | 23   |
| 400              |Invalid X-CUSTOMER-DIGITAL-EXTENSION-TOKEN | X-CUSTOMER-DIGITAL-EXTENSION-TOKEN | 24   |


### JS Integration example


http://jsfiddle.net/4gLLgw4s/9/

<iframe width="100%" height="300" src="//jsfiddle.net/4gLLgw4s/9/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>


# Event Management

## Subscribe to Event

### Request for DEV

POST /interactions/570d3c1a854c183b04e4263a HTTP/1.1
Content-Type: application/json
X-TOUCHPOINT-TOKEN: **
X-CUSTOMER-DIGITAL-EXTENSION-TOKEN: **
Cache-Control: no-cache

{ "Evento_Seleccionado" : "EventKey" }

### Request for PROD

POST /interactions/57183f9f52da4b282ff9f1d2 HTTP/1.1
Content-Type: application/json
X-TOUCHPOINT-TOKEN: **
X-CUSTOMER-DIGITAL-EXTENSION-TOKEN: **
Cache-Control: no-cache

{ "Evento_Seleccionado" : "EventKey" }

