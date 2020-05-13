# ApiGrupp
Grupparbete Api

### HTTP Protocol Basics
##### Request response model:
```sh
Request message
Resources identified using a Universal Resource Identifier (URI)
Request Method
Headers, Body, query
Response 
Response code
Headers och Body. 
```
## 

### HTTP status codes
##### 1xx - Informational 
##### 2xx - Success - 201 Created 
##### 3xx - Redirection
##### 4xx - Client error - 404 - Page not found
##### 5xx - Server error 
## 

Vi använder oss av http://api.softhouse.rocks 
| Method | what it dose |
| ------ | ------ |
| GET |- /posts..........List of Posts |
| POST |– Sänder någon form av information till servern, utöver själva förfrågan, vanligen motsvarande en webblankett. Detta används dels då förfrågan ändrar information på servern, såsom då man gör en bokning, dels då innehållet väntas vara större än vad som är lämpligt att hantera som en webbadress (eller annars olämpligt, såsom lösenord). |
| PATCH |– Uppdaterar objecktet och dess innehåll till det som skickas med, här kan du uppdatera enstaka värden.|
| DELETE |– Raderar den utpekade filen. Detta kommando används sällan och många webbservrar har inget stöd för det. |
| PUT | – ändrar hela objektet till det som skickas med, här måste du skicka med alla värden i objektet. |
| HEAD | – Ber servern att skicka information om den utpekade resursen, men utan att skicka själva innehållet i filen. |
| CONNECT |– Används med proxy-servrar som kan fungera som SSL-tunnlar. |

| ------ | ------ |
| GET |  - /posts..........List of Posts. |
| GET |   -/posts/{postId} Get a Post specified resource.|
| POST |  - /posts..........Creat a new Post Ex Webb form.|
| PUT |   -/posts/{postId} Replace a Post.|
| PATCH|  -/posts/{postID} Update a Post.|
| DELETE | -/posts/{postId} Delete a Post. |

### Endpoints Example
 ##### 1. GET     https://name.com/api/users
 ##### 2. GET     https://name.com/api/users/1 or https://name.com/api/users/details/1
 ##### 3. POST    https://name.com/api/users
 ##### 4. PUT     https://name.com/api/users/1 or https://name.com/api/users/uppdate/1
 ##### 5. DELETE  https://name.com/api/users/1 or https://name.com/api/users/delete/1
## 

### Authentication github´s API developer/github.com
1. curl -H "Authentication: token OAUTH-TOKEN"https//api.github.com sending in the header
2. curl https://api.github.com/?access_token=OAUTH-TOKEN in URI
3. curl 'https://api.github.com/users/whatever?client_id=xxxx&client_secret=yyyy'
## 

#### -i, --include       Include protocol headers in the output (H/F)
#### -H, --header LINE   Pass custom header LINE to server (H)
#### -X  --request COMMAND  Specify request command to use


#### Request: -> 
curl -X GET "https://api.softhouse.rocks/posts?userId=1" -H  "accept: application/json" | jq

#### Respons: 
https://api.softhouse.rocks/posts?userId=1

#### Response headers:
content-type: application/json; charset=utf-8 
(when the server responds, it sends information back).


#### Part of a Respons
{
    "_id": "5ea03f2b3075e40021162a5e",
    "body": "Griljerar och briljerar",
    "title": "Rostbiff och isterband ",
    "userId": 1,
    "id": 846,
    "__v": 0
  },
  {
    "_id": "5ea143518e9e2e7dc0da6f8a",
    "id": 1,
    "__v": 0,
    "body": "get fed",
    "title": "replaced kid",
    "userId": 1
  },
  {
    "_id": "5ea146fb3636b200261814ce",
    "body": "Fresh as morning dew",
    "title": "Hi, World",
    "userId": 1,
    "id": 849,
    "__v": 0
  },
  {
    "_id": "5ea147253636b200261814cf",
    "body": "Fresh as morning dew",
    "title": "Hi, World",
    "userId": 1,
    "id": 850,
    "__v": 0
  }
]
#### POST creat a new Post. 
##### Object
##### Post{
##### title	string
##### body	string
##### userId	integer
}

## 
curl -i -H "Content-Type:application/json" http://api.softhouse.rocks/posts/1

## Request response model:
#### HTTP/1.1 200 OK - Statuscode 200 OK.
#### X-Powered-By: Express - It tells the browser that the application is powered by Express (should you wish to look at that in chrome dev tools). Express is a server side framework. https://www.reddit.com/r/node/comments/3k9ij6/does_anyone_know_what_the_xpoweredby_express_is/
#### Access-Control-Allow-Origin: * - The Access-Control-Allow-Origin response header indicates whether the response can be shared with requesting code from the given origin. For requests without credentials, the literal value "*" can be specified, as a wildcard; the value tells browsers to allow requesting code from any origin to access the resource. Attempting to use the wildcard with credentials will result in an error.
#### Content-Type: application/json; charset=utf-8 - Content-type: application/json; charset=utf-8 designates the content to be in JSON format, encoded in the UTF-8 character encoding.
#### Content-Length: 316 - Is used to indicate the size of the entire body. The content-length is the size of the compressed message body, in "octets". 
#### ETag: W/"13c-iqD6A3ivz4dRZ1d/uIZLXBts6BU" - The ETag or entity tag is part of HTTP, the protocol for the World Wide Web. It is one of several mechanisms that HTTP provides for Web cache validation. 
#### Date: Tue, 21 Apr 2020 08:28:50 GMT Date
#### Via: 1.1 google - The Via general header is added by proxies, both forward and reverse proxies, and can appear in the request headers and the response headers. It is used for tracking message forwards, avoiding request loops, and identifying the protocol capabilities of senders along the request/response chain.
##

## GET 
#### curl -H GET  http://api.softhouse.rocks/users/3 | jq
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   271  100   271    0     0    872      0 --:--:-- --:--:-- --:--:--   871
{
  "address": {
    "geo": {
      "lat": -68.6102,
      "lng": -47.0653
    },
    "street": "Douglas Extension",
    "suite": "Suite 847",
    "city": "McKenziehaven",
    "zipcode": "59590-4157"
  },
  "_id": "5e806d9f42fbde006b6b9ec7",
  "id": 3,
  "name": "Clementine Bauch",
  "username": "Samantha",
  "email": "Nathan@yesenia.net",
  "__v": 0
}

#### curl -X GET "https://api.softhouse.rocks/posts?userId=1" -H "accept: application/json"


#### curl -X GET "https://api.softhouse.rocks/posts?userId=1" -H "accept: application/json" | JQ
{
    "_id": "5ea068b63636b200261814cd",
    "body": "Fresh as morning dew",
    "title": "Hi,Karlstadd",
    "userId": 1,
    "id": 847,
    "__v": 0
  }


## POST
1. curl -X POST "https://api.softhouse.rocks/posts" -H  "accept: application/json" -H  "Content-Type: application/json" -d "{\"title\":\"SweetApi\",\"body\":\"Rostbiff\",\"userId\":3}"

// Result: 
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   148  100    99  100    49   1042    515 --:--:-- --:--:-- --:--:--  1574{"_id":"5ea154f3f7e5830021385834","body":"Rostbiff","title":"SweetApi","userId":3,"id":853,"__v":0}

2. Next get: To see result:curl -X GET "https://api.softhouse.rocks/posts?userId=3" -H  "accept: application/json" | jq
 {
    "_id": "5ea15467f7e5830021385833",
    "body": "Rostbiff",
    "title": "SweetApi",
    "userId": 3,
    "id": 852,
    "__v": 0
  },
  


##
$ curl -i -X POST -H "Content-Type:application/json" http://api.softhouse.rocks/posts -d '{"title":"Hi,Karlstadd", "body":"Fresh as morning dew", "userId": "1"}'
HTTP/1.1 201 Created
X-Powered-By: Express
Access-Control-Allow-Origin: *
Content-Type: application/json; charset=utf-8
Content-Length: 115
ETag: W/"73-sc6cjswQKZbxNrK9Hty0Yb8Od8Q"
Date: Wed, 22 Apr 2020 15:54:30 GMT
Via: 1.1 google

{"_id":"5ea068b63636b200261814cd","body":"Fresh as morning dew","title":"Hi,Karlstadd","userId":1,"id":847,"__v":0}


## PUT 
curl -X PUT "https://api.softhouse.rocks/posts/847" -H "accept: application/json" -H "Content-Type: application/json" -d "{\"title\":\"Hi,malmo\",\"body\":\"Fresh as morning dew\",\"userId\":1}"

 {
    "_id": "5ea068b63636b200261814cd",
    "body": "Fresh as morning dew",
    "title": "Hi,malmo",
    "userId": 1,
    "id": 847,
    "__v": 0
  }
  

## PATCH
### curl -X PATCH "https://api.softhouse.rocks/posts/846" -H "accept: application/json" -H "Content-Type: application/json" -d "{\"title\":\"Rostbiff och isterband \",\"body\":\"Griljerar och briljerar\",\"userId\":1}"
 {
    "_id": "5ea03f2b3075e40021162a5e",
    "body": "Griljerar och briljerar",
    "title": "Rostbiff och isterband ",
    "userId": 1,
    "id": 846,
    "__v": 0
  }
  

## PATCH 
TO PATCH A POST.

1. FIRST, GET A LIST OF POSTS: 
curl http://api.softhouse.rocks/POSTS | JQ

RESPONSE/response body: 
{
    "_id": "5ea154f3f7e5830021385834",
    "body": "Hur mar du",
    "title": "Hejsan",
    "userId": 3,
    "id": 853,
    "__v": 0
  }


2. NEXT STEP, TO PATCH A POST: 
curl -X PATCH "https://api.softhouse.rocks/posts/853" -H "accept: application/json" -H "Content-Type: application/json" -d "{\"title\":\"Unicorn Dust\",\"body\":\"Is pink\",\"userId\":3}"


RESPONSE: 
{"n":1,"nModified":0,"opTime":{"ts":"6819927566581760001","t":157},"electionId":"7fffffff000000000000009d","ok":1,"operationTime":"6819927566581760001","$clusterTime":{"clusterTime":"6819927566581760001","signature":{"hash":"AAAAAAAAAAAAAAAAAAAAAAAAAAA=","keyId":0}}}

3. TO CHECK CHANGE:
curl -X GET "https://api.softhouse.rocks/posts?userId=3" -H "accept: application/json" | jq

RESPONSE:
  {
    "_id": "5ea154f3f7e5830021385834",
    "body": "Is pink",
    "title": "Unicorn Dust",
    "userId": 3,
    "id": 853,
    "__v": 0
  }
  
## DELETE 
TO DELETE A POST
1. FIRST, GET A LIST OF POSTS, THEN PICK ONE
curl http://api.softhouse.rocks/POSTS | JQ

RESPONSE (PICKED POST 853): 
  {
    "_id": "5ea154f3f7e5830021385834",
    "body": "Is pink",
    "title": "Unicorn Dust",
    "userId": 3,
    "id": 853,
    "__v": 0
  }
  
  2. TO DELETE POST 853
  curl -X DELETE "https://api.softhouse.rocks/posts/853" -H "accept: application/json"
  
  3. CHECK TO SEE IF DELETED:
  curl -X GET "https://api.softhouse.roc" -H "accept: application/json"|jq
  
  id 853 is missing! wohoo
