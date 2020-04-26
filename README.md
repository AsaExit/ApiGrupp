# ApiGrupp
Grupp arbete Api

##### 
HTTP Protocol Basics
Request response model:
Request message
Resources identified using a Universal Resource Identifier (URI)
Request Method
Headers, Body, query
Response 
Response code
Headers och Body


###HTTP status codes
##### HTTP/1.1 200 OK  
##### 300 - Redirect
##### 400/404 - Page not found
##### 500 - Authentication 
SKRIV MER HÄR

### Vi använder oss av http://api.softhouse.rocks 
##### 
1. GET    /posts..........List of Posts 
##### 
2. GET    /posts/{postId} Get a Post specified resource
##### 
3. POST   /posts..........Creat a new Post Ex Webb form
##### 
4. PUT    /posts/{postId} Replace a Post
##### 
5. PATCH  /posts/{postID} Update a Post
##### 
6. DELETE /posts/{postId} Delete a Post

### Endpoints Example

 1. GET     https://name.com/api/users
 2. GET     https://name.com/api/users/1 or https://name.com/api/users/details/1
 3. POST    https://name.com/api/users
 4. PUT     https://name.com/api/users/1 or https://name.com/api/users/uppdate/1
 5. DELETE  https://name.com/api/users/1 or https://name.com/api/users/delete/1


### Authentication github´s API developer/github.com
1. curl -H "Authentication: token OAUTH-TOKEN"https//api.github.com sending in the header
2. curl https://api.github.com/?access_token=OAUTH-TOKEN in URI
3. curl 'https://api.github.com/users/whatever?client_id=xxxx&client_secret=yyyy'

#### -i, --include       Include protocol headers in the output (H/F)
#### -H, --header LINE   Pass custom header LINE to server (H)
#### -X  --request COMMAND  Specify request command to use

##### Request: -> 
curl -X GET "https://api.softhouse.rocks/posts?userId=1" -H  "accept: application/json" | jq
curl -X GET "http://localhost:3000/posts?userId=1" -H  "accept: application/json"

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
#### Object
Post{
title	string
body	string
userId	integer
 
}
##### 
curl -X POST "https://api.softhouse.rocks/posts" -H  "accept: application/json" -H  "Content-Type: application/json" -d "{\"title\":\"SweetApi\",\"body\":\"Rostbiff\",\"userId\":3}"

// Result: 
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   148  100    99  100    49   1042    515 --:--:-- --:--:-- --:--:--  1574{"_id":"5ea154f3f7e5830021385834","body":"Rostbiff","title":"SweetApi","userId":3,"id":853,"__v":0}

Next get: To see result:curl -X GET "https://api.softhouse.rocks/posts?userId=3" -H  "accept: application/json" | jq
 {
    "_id": "5ea15467f7e5830021385833",
    "body": "Rostbiff",
    "title": "SweetApi",
    "userId": 3,
    "id": 852,
    "__v": 0
  },


## Request Method
#### -i, --include       Include protocol headers in the output (H/F)
#### -H, --header LINE   Pass custom header LINE to server (H)

## 
curl -i -H "Content-Type:application/json" http://api.softhouse.rocks/posts/1

## Request response model:
HTTP/1.1 200 OK     
X-Powered-By: Express
Access-Control-Allow-Origin: *
Content-Type: application/json; charset=utf-8
Content-Length: 316
ETag: W/"13c-iqD6A3ivz4dRZ1d/uIZLXBts6BU"
Date: Tue, 21 Apr 2020 08:28:50 GMT
Via: 1.1 google

## Statuskoden var framgångsrik, 200. 
## It's a header. It doesn't tell the browser anything except that the application is powered by Express (should you wish to look at that in chrome dev tools). Express is a server side framework. https://www.reddit.com/r/node/comments/3k9ij6/does_anyone_know_what_the_xpoweredby_express_is/
## SKRIV MER HÄR 
## SKRIV MER HÄR 
## Content-Length: 316 posts. Is used to indicate the size of the entire body. The content-length is the size of the compressed message body, in "octets". 
## The ETag or entity tag is part of HTTP, the protocol for the World Wide Web. It is one of several mechanisms that HTTP provides for Web cache validation. 
## SKRIV MER HÄR 
## SKRIV MER HÄR 


## 
curl -H "Content-Type:application/json" http://api.softhouse.rocks/posts/1 | jq 

% Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   316  100   316    0     0   2538      0 --:--:-- --:--:-- --:--:--  2548
{
  "_id": "5e806d9f42fbde006b6b9ecf",
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto",
  "__v": 0
}


## 
curl -H GET  http://api.softhouse.rocks/users/3

{"address":{"geo":{"lat":-68.6102,"lng":-47.0653},"street":"Douglas Extension","suite":"Suite 847","city":"McKenziehaven","zipcode":"59590-4157"},"_id":"5e806d9f42fbde006b6b9ec7","id":3,"name":"Clementine Bauch","username":"Samantha","email":"Nathan@yesenia.net","__v":0}Sofias-MacBook-Pro:ApiGrupp sofiajunell$ curl -H GET  http://api.softhouse.rocks/users/3


## 
$ curl -H "Content-Type:application/json" http://api.softhouse.rocks/posts/userId1 | jq 
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   171  100   171    0     0   1327      0 --:--:-- --:--:-- --:--:--  1335
{
  "message": "Cast to number failed for value \"NaN\" at path \"id\" for model \"Post\"",
  "name": "CastError",
  "stringValue": "\"NaN\"",
  "kind": "number",
  "value": null,
  "path": "id"
}


## 
### curl -H GET  http://api.softhouse.rocks/users/3 | jq
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


## curl -X GET "https://api.softhouse.rocks/posts?userId=1" -H "accept: application/json"




## curl -X GET "https://api.softhouse.rocks/posts?userId=1" -H "accept: application/json" | JQ
{
    "_id": "5ea068b63636b200261814cd",
    "body": "Fresh as morning dew",
    "title": "Hi,Karlstadd",
    "userId": 1,
    "id": 847,
    "__v": 0
  }




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
1. TO PATCH A POST.

FIRST, GET A LIST OF POSTS: 
$ curl http://api.softhouse.rocks/POSTS | JQ

RESPONSE/response body: 

]
NEXT STEP, TO PATCH A POST: 
curl -X PATCH "https://api.softhouse.rocks/posts/853" -H "accept: application/json" -H "Content-Type: application/json" -d "{\"title\":\"Hejsan\",\"body\":\"Hur mar du\",\"userId\":3}"
RESPONSE: 
{"n":1,"nModified":0,"opTime":{"ts":"6819234831306588161","t":149},"electionId":"7fffffff0000000000000095","ok":1,"operationTime":"6819234831306588161","$clusterTime":{"clusterTime":"6819234831306588161","signature":{"hash":"AAAAAAAAAAAAAAAAAAAAAAAAAAA=","keyId":0}}}
TO CHECK CHANGE:
curl http://api.softhouse.rocks/POSTS | JQ
RESPONSE:
{
    "_id": "5ea154f3f7e5830021385834",
    "body": "Hur mar du",
    "title": "Hejsan",
    "userId": 3,
    "id": 853,
    "__v": 0
  }
  ______________________________________________________________-
2. TO GET AND PATCH A SPECIFIC POST 
FIRST, GET A SPECIFIC POST:

curl -X GET "https://api.softhouse.rocks/posts?userId=1337" -H "accept: application/json"|JQ

RESPONSE:
% Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   113  100   113    0     0    330      0 --:--:-- --:--:-- --:--:--   330
[
  {
    "_id": "5ea141aff7e5830021385831",
    "body": "also executes",
    "title": "does execute",
    "userId": 1337,
    "id": 848,
    "__v": 0
  }
]
SECOND, PATCH THE POST: 
curl -X PATCH "https://api.softhouse.rocks/posts/1337" -H "accept: application/json" -H "Content-Type: application/json" -d "{\"title\":\"Unicorn\",\"body\":\"Dust\",\"userId\":100}
To check if pached: 


## DELETE 


## DELETE
curl -X DELETE "https://api.softhouse.rocks/posts/847" -H "accept: application/json"
## id 847 is missing! wohoo

## POST 

$ curl -i -X POST -H "Content-Type:application/json" http://api.softhouse.rocks/posts -d '{"title":"Hi, World", "body":"Fresh as morning dew", "userId": "1"}'
HTTP/1.1 201 Created
X-Powered-By: Express
Access-Control-Allow-Origin: *
Content-Type: application/json; charset=utf-8
Content-Length: 112
ETag: W/"70-02iSTKio5MeFXsyJ8v235hz/hlE"
Date: Wed, 22 Apr 2020 12:57:15 GMT
Via: 1.1 google

{"_id":"5ea03f2b3075e40021162a5e","body":"Fresh as morning dew","title":"Hi, World","userId":1,"id":846,"__v":0}
