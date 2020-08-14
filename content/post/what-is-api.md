---
title: "What is an API, JSON or XML?"
date: 2020-08-11T10:00:02+05:30
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
thumbnailImage : img/thumbnail/blog10.png
coverImage: img/thumbnail/blog10.png
coverMeta: out
metaAlignment: center
---

API[^1] or the Application Programming interface is the middlepoint between App[^2] and data or it is a gateway to DataBase.

API governs the access point(s) for the server, that means instead of directly sending request to DataBase, API checks your identity and type of request and pass it through some logic filter and then reflect your request/change to the DataBase.

![How API works](https://images.theconversation.com/files/229545/original/file-20180727-106521-rww37h.png?ixlib=rb-1.1.0&q=45&auto=format&w=754&fit=clip)

From the above diagram you can clearly see that, every request passes through a middleware(API) and then API performs some action/ checks validation and pass your request to DataBase to let it give you your desired response.

So, API in simple terms works as the middleware of the system. Your App communicate with API and API changes/fetch the data from the DataBase.

- Communcation between services
- Database connection

API and App talks in the specific language and it can range form JSON[^3] to YAML to XML to Protobuf. But the most poplularly used language/notation are JSON and XML.

## JSON

- JSON (JavaScript Object Notation) is a lightweight format that is used for data interchanging
- It is based on a subset of JavaScript language (the way objects are built in JavaScript)
- It is easy for humans to read and write
- It is easy for machines to parse and generate
- JSON is a text format that is completely language independent but uses conventions that are familiar to programmers of the C-family of languages, including C, C++, C#, Java, JavaScript, Perl, Python, and many others.

These properties make JSON an ideal data-interchange language.

```JSON
{
  "users":[
    {
      "firstName":"Vince",
      "lastName":"Light"
    },
    {
      "firstName":"Super",
      "lastName":"Nova"
    },
    {
      "firstName":"Will",
      "lastName":"Smith"
    },
    {
      "firstName":"Peter",
      "lastName":"Patrik"
    }
  ]
}

```

## XML

- XML (Extensible Markup Language) is a markup language similar to HTML, but without predefined tags to use.
- This is a powerful way to store data in a format that can be stored, searched, and shared.
- Most importantly, since the fundamental format of XML is standardized, if you share or transmit XML across systems or platforms, either locally or over the internet, the recipient can still parse the data due to the standardized XML syntax.

```XML
<Users>
 <User firstName="Vince" lastName="Light" />
 <User firstName="Vince" lastName="Light" />
 <User firstName="Vince" lastName="Light" />
 <User firstName="Vince" lastName="Light" />
</Users>
```

## Reasons to choose JSON over XML

- JSON requires less tags than XML. XML items must be wrapped in open and close tags whereas JSON you just name the tag once
- JSON is easy and quicker to read
- JSON can use arrays
- Because JSON is transportation-independent, you can just bypass the XMLHttpRequest object for getting your data.

## Reasons to choose XML over JSON

- XML is supported by many more desktop applications than JSON
- Easy to take XML and apply XSLT to make XHTML.
- XML is often a complement to HTML
- RSS is one of the popular user of XML

Both, XML and JSON are tough competetors and are widely used. But looking at the popularity of JSON, readabilty and its speed, it is considered to be the first choice of many developers.

---

### References

- [UNSW Sydney](https://images.theconversation.com/files/229545/original/file-20180727-106521-rww37h.png?ixlib=rb-1.1.0&q=45&auto=format&w=754&fit=clip)

- [Differnce between JSON & XML](https://www.geeksforgeeks.org/difference-between-json-and-xml/)

- [JSON.org](https://www.json.org/json-en.html)

- [MDN/XML](https://developer.mozilla.org/en-US/docs/Web/XML/XML_introduction)

---

[^1]: This blog specifically focus on Web-API. But a simple package exporting functions will also work like API. So, API in all is wide topic to talk to.

[^2]: Here, App is to as web application &rarr; An app is a Web application that does something – e.g., a Weblog system, a database of public records or a small poll app. A project is a collection of configuration and apps for a particular website. A project can contain multiple apps. An app can be in multiple projects. We are referring/we will be referring app as the client and API as the server.

[^3]: Read more about JSON and Syntax rules here at &rarr; [w3schools/JSON](https://www.w3schools.com/whatis/whatis_json.asp) and [JSON.org](https://www.json.org/json-en.html)
