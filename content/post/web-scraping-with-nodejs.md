---
title: "Web Scraping with Nodejs | Building an IMDb Scraper"
date: 2020-06-29T21:53:16+05:30
categories:
- Random discovery
- Web-scraping
tags:
- Nodejs
- techcodemonk
- web-scraping
- IMDb
keywords:
- tech
autoThumbnailImage : false
thumbnailImagePosition : "left"
thumbnailImage: https://www.techcodemonk.in/wp-content/uploads/2020/01/christopher-gower-m_HRfLhgABo-unsplash-1170x610.jpg
coverImage: https://www.techcodemonk.in/wp-content/uploads/2020/01/christopher-gower-m_HRfLhgABo-unsplash-1170x610.jpg
coverMeta: out
metaAlignment: center
---
>NOTE : This post originally appeared on [techcodemonk.in](https://techcodemonk.in), and has been posted here with due permission

In continuation with the blog [Web Scrapping with Python](https://www.techcodemonk.in/2020/01/18/web-scraping-with-python-building-an-imdb-scraper/) by [Kamran](https://www.techcodemonk.in/author/skahmed1420/) which explained briefly about what web scraping is. The blog was focused on Python programming language. However, here in this article we will be expanding our scope and try to write exactly like the last blog but with Nodejs. We will be (again) building an IMDB Scraper but this time with Nodejs.

>CAUTION: Web scraping stands on the border of both legal and illegal actions as web scraping is the technique to extract data from a website (a data may be under a copyright). This blog thus is just for education purpose and we are not using the scraped data for any other purpose.

## Aim

We will be building an IMDB web scraper that will loop through a list of IMDB movie links. From there we will be extracting data such as the title of the movie/show, rating and summary and save the extracted data in a CSV file.

## Dependencies required

As you know there are tons of tools available for a single task at npm but we will be using the most widely used tools that are maintained by an active community.

- [Nodejs](https://nodejs.org/) (not a package but a basic prerequisite)
- [Cheerio](https://www.npmjs.com/package/cheerio) to make the code looks like jQuery (we can perform our task without cheerio also, however, we are more focused on making our code look clean and good)
- [Request](https://www.npmjs.com/package/request) to make http calls that will help us fetch the contents of the website (Note: Request package as what npm says is depreciated from 11th of Feb, 2020)
- [Request-promise](https://www.npmjs.com/package/request-promise) is a request based package which we will be using along with Request package. (You can also use request-promise-native or request-promise-any but keeping the stuff simple we will be using request-promise)
- [Json2csv](https://www.npmjs.com/package/json2csv) to convert our JSON output data to a CSV file. Other packages such as jsonexport or object-to-csv can also be used.

## Extracting data using dev tools

We will first look for the IMDB and try to extract some useful information which we will be using to make our scraper.

![](https://www.techcodemonk.in/wp-content/uploads/2020/06/techcodemonk_blog1-1024x506.png)

Here in the above image, you can clearly see that the title of the movie wrapped under a `div` tag which has a class that is `class="title_wrapper"` which is followed by a child `h1` tag which has the title of the movie.

>NOTE: I am using Firefox browser but you can use any other browser such as Chrome. For inspecting elements and using Firefox dev tools you need to just right click on that element and choose inspect element option or just use ctrl + shift + c on your keyboard.

Let us now use the above information to extract the title of the movie. We will be using browser's console for this and jQuery syntax.

```javascript
$('div[class="title_wrapper"] > h1').text().trim()
```
```javacript
Output: "Joker (2019)"
```

![](https://www.techcodemonk.in/wp-content/uploads/2020/06/techcodemonk_blog2-1024x507.png)

Let us understand the syntax. Here we are calling every `div` tag which has class as "title_wrapper" followed by a child `h1` tag. Later we are extracting **trimmed text** from it. Why trimmed? Because sometimes additional spaces can be there in the text which we do not want in our CSV file. Thus I highly recommend you to use `trim()`, however, the above command can also work without it as we are only focussed on the text.

Similarly, we can extract rating and summary text of the movie by inspecting them and writing the small commands in the console.

```javascript
$('div[class="ratingValue"] > strong > span').text().trim()
```
```javascript
Output: "8.5"
```
```javascript
$('div[class="plot_summary_wrapper"] > div[class="plot_summary "] > div[class="summary_text"]').text().trim()
```
```javascript
Output: "In Gotham City, mentally troubled comedian Arthur Fleck is disregarded and mistreated by society. He then embarks on a downward spiral of revolution and bloody crime. This path brings him face-to-face with his alter-ego: the Joker."
```

It is good to provide as much information to the command (here, in the form classes or ids name) to improve specificity.

Now, since we have gathered the information we required. Let us now move to the actual code part.

## Workflow

request (async) > load response to cheerio > Data-extraction using cheerio > Json2Csv

Pretty simple!

We will first make a request to the website which will return us the html code in response and from that response we will extract our data in the object form and convert it into CSV form.

Let us first initialize our project with `npm init` command. Now make a file named scraper.js (name of your choice it doesn't matter)

Let us first call our dependencies.

```javascript
1 const  rp = require("request-promise")
2 const cheerio = require("cheerio")
3 const json2csv = require("json2csv").Parser
4 const fs = require("fs");
5
6 const movie_URL = "https://www.imdb.com/title/tt7286456/?ref_=hm_fanfav_tt_3_pd_fp1";
7
```

Note that semi-colon after the movie URL, it is placed to separate the variable with unnamed function in the next line. Else you will get a TypeError.

Next, we will initialize an unnamed async function which will be called with the flow of the code and receive our response in the function.

```javascript
8 (async() => {
9     let data = []
10    const response = await rp({
11        uri: movie_URL,
12        headers:{
13            accept:
14            "text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9",
15             "accept-encoding": "gzip, deflate, br",
16             "accept-language": "en-GB,en-US;q=0.9,en;q=0.8"
17         },
18         gzip: true,
19     })
20 })()
```

That unnamed function is a little complicated to understand. For now, grab it like a callback function which has no name and is calling itself like `(async () => {})()`. Under this function, we had declared an empty array in which we will be pushing our data. Then a response which we will be receiving after a request made to the URL. Note that we have added headers and encoding that is gzip here. It can be Json also depending on the website can be changed. This was all done to ensure that our request looks like made from a browser. You can find headers in the header options of the dev tools.

![](https://www.techcodemonk.in/wp-content/uploads/2020/06/techcodemonk_blog3-1024x504.png)

Notice that Accept encoding is of the type gzip and not utf-8 or json thus gzip is separately set to true.

We will now load this response to cheerio and then extract all the data using the commands which we used above in the browser’s console and then we will push this data the array that declared above.

```javascript
20 let $ = cheerio.load(response)
21 let title = $('div[class="title_wrapper"] > h1').text().trim()
22 let rating = $('div[class="ratingValue"] > strong > span').text().trim()
23 let summary = $('div[class="plot_summary_wrapper"] > div[class="plot_summary "] > div[class="summary_text"]').text().trim()
24
25 data.push({
26    title: title,
27    rating: rating,
28     summary: summary
29 })
30 console.log(data)
```
Let us now run our script

```
Output: [{ title: 'Joker (2019)',
        rating: '8.5',
        summary:
        'In Gotham City, mentally troubled comedian Arthur Fleck is disregarded and mistreated by society. He then embarks on a downward spiral of revolution and bloody crime. This path brings him face-to-face with his alter-ego: the Joker.'
        }]
```
Let us now perform our last task that is to convert this data into a CSV file. the code for this is actually very simple.

```javascript
32
33 const j2cp = new json2csv()
34 const csv = j2cp.parse(data) 
36    
35 fs.writeFileSync("./movie.csv", csv, "utf8")
```

And we are done! Run this script and it will generate a movie.csv file after completion. You can use as much input URL data and loop through this function to generate more entries.

The final code will somewhat look like:

```javascript
1 const  rp = require("request-promise")
2 const cheerio = require("cheerio")
3 const json2csv = require("json2csv").Parser
4 const fs = require("fs");
5 
6 const movie_URL = "https://www.imdb.com/title/tt7286456/?ref_=hm_fanfav_tt_3_pd_fp1";
7
8 (async() => {
9     let data = []
10    const response = await rp({
11        uri: movie_URL,
12        headers:{
13            accept:
14            "text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9",
15            "accept-encoding": "gzip, deflate, br",
16            "accept-language": "en-GB,en-US;q=0.9,en;q=0.8"
17        },
18        gzip: true,
19    })
20    let $ = cheerio.load(response)
21    let title = $('div[class="title_wrapper"] > h1').text().trim()
22    let rating = $('div[class="ratingValue"] > strong > span').text().trim()
23    let summary = $('div[class="plot_summary_wrapper"] > div[class="plot_summary "] > div[class="summary_text"]').text().trim()
24
25    data.push({
26        title: title,
27        rating: rating,
28        summary: summary
29    })
30    console.log(data)
31
32    const j2cp = new json2csv()
33    const csv = j2cp.parse(data)
34    
35    fs.writeFileSync("./movie.csv", csv, "utf8")
36 })()
```
Pretty simple! Isn't it?

>NOTE: the above article may seems to be like a copied one but it actually isn't as many bloggers or developers use these famous packages and use the same best practices hence such simple code snippets may looks like the same for multiple people.

You can find the above code in my GitHub repository [here](https://github.com/pnijhara/node-scraper/)
