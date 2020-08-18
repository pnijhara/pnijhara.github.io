---
title: "HTTP Methods and Status Code"
date: 2020-08-18T13:56:18+05:30
categories:
- Tech
- Python
tags:
- Python
- FastAPI	
- Backend	
- Best Practices
keywords:
- FastAPI
- Python
autoThumbnailImage : false
thumbnailImagePosition : "left"
thumbnailImage : img/thumbnail/blog11.png
coverImage: img/thumbnail/blog11.png
image: img/thumbnail/blog11.png
coverMeta: out
metaAlignment: center
---

Before we begin coding, we must know basics about internet, specifically communication with API. We already covered our basics about APIs in the previous blog on ["What is API, JSON or XML?"](https://pnijhara.github.io/2020/08/what-is-an-api-json-or-xml/). It is now time to cover HTTP.

Communication between clients and server (which is our API) is done by HTTP(Hyper Text Transfer Protocol) requests and response. Every time client wants to perform some action on Database, it sends HTTP request to server and server in back respond by HTTP response.
blog
![Request and response](http://vidyakv.files.wordpress.com/2011/12/cs-120-3-3341.png)

From the above diagram it is clear that server responds only if client makes a request.

HTTP is a communication protocol. There can be other protocols such as SMTP, FTP etc. Read more them about [here](https://en.wikipedia.org/wiki/Lists_of_network_protocols)

HTTP has some parts which are actively used in Backend Development.

1. **Methods**: GET, PUT, POST, DELETE, etc. Best practice is to use these standard types. You can create your own types but it not recommended. We'll talk about HTTP methods in detail below.

2. **Headers**: Every HTTP request contains headers. HTTP headers let the client and the server pass additional information with an HTTP request or response. An HTTP header consists of its case-insensitive name followed by a colon (:), then by its value. Whitespace before the value is ignored. HTTP helps in:
    - Authentication
    - Caching
    - Client Hints
    - Connection Management
    - Cookie Handling and much more

    This is how Request-headers look like

    ![Request-headers](/img/blog11-pic1.png)

    And this is how a Response-header look like

    ![Response-header](/img/blog11-pic2.png)

3. **Payload**: The payload is the part of that response that is communicating directly to you. In REST APIs this is usually some JSON formatted data. The payload is the part of that response that is communicating directly to you. In REST APIs this is usually some JSON formatted data.

## HTTP Methods

REST APIs enable you to develop any kind of web application having all possible CRUD (create, retrieve, update, delete) operations. REST guidelines suggest using a specific HTTP method on a particular type of call made to the server (though technically it is possible to violate this guideline, yet again it is highly discouraged).

Let us understand the different HTTP methods with the help of following table:

|   GET    |    POST    |   DELETE    |     UPDATE      |       PATCH    |
| --- | --- | ------ | ------ | ----- |
| No payload | Has Payload | No payload | Has Payload | Has Payload |
| To fetch data | To insert data | To delete data | To update data | To update som part of data |
| Does not change database | Change database | Change database | Change database | Change database |

We'll cover these methods practically in upcoming blogs.

## HTTP Status Code

Whenever server respond to client, it also respond with a status code so that the client can understand the status of the code.

- 1** : Informative
- 2** : Success
- 3** : Redirection
- 4** : Client Error
- 5** : Server Error

Read about all the HTTP status codes in [Wikipedia's article on HTTP status code](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)

---

## References

- [MDN Headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers)
- [restfulapi.net/http-methods](https://restfulapi.net/http-methods/)
- [Wikipedia's article on HTTP status code](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)
