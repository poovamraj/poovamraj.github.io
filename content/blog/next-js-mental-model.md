---
author: "Poovamraj T T"
title: "How to think in Next.js - Learn the Mental Model"
date: "2021-05-08"
description: "Next.js requires a difference in how to think of a solution for a traditional SPA developer who never worked on a Server Side rendered web page. I tried to summarize on the crucial topics that would help a developer understand Next.js and how to build applications using it."
tags: ["next.js", "react", "server-side rendering"]
ShowToc: false
---

The most important thing when learning a new framework, especially ones which have a new way of doing things is to understand how to think (or design) solutions to a problem.

Next.js claims the major issue it fixes on top of React.js is "Pre Rendering"

## What is Pre Rendering

Historically frameworks like JSP used to render the HTML content of the page on the server-side and send the rendered HTML page to the browser. This is in contrast to the approach used in modern frameworks like React.js where the web page first loads the JS and then it renders all the required HTML elements on the client (read it as the browser) side

The concept of Client-side rendering works well as it completely separates the backend and frontend. But there are certain issues that can arise from client-side rendering.

- Search Engines tend to parse the HTML file and index it. This scraping process is not optimized for sites that do client-side rendering.

- When you are rendering on the client end, whenever an API call is made, the request has to travel all the way from the client who can be in the US to the server which can reside in JAPAN. This can severely slow down the performance. Instead, if we are rendering on the server end, most of the data can be fetched easily as the rendering can happen at the same place as the server.

If you do not have the above 2 use-cases, you can simply use the traditional client-side rendering application. At least, that's what I am doing.

This concept is generally called Server-Side Rendering (SSR)

But Next.js tends to use the word "Pre Rendering". This is to distinguish the two major use cases the framework is used for

- Static Rendering
- Server-Side Rendering

## Static Rendering

When the HTML code is generated as soon as we run the build, This is called static rendering.

Static rendering is useful for Homepages or Blogs where the content of the page doesn't change often (For example - each reload won't have different data like a stock market site).

We can write a "Page" by exporting a JSX component under the pages folder.

For example - writing a js file named 'hello.js' that exports a JSX component under the pages folder will give us a

localhost:3000/hello page

Creating a new folder will add it as a path.

For example - creating a folder named 'blog' under pages folder with a js file named hello that returns a JSX component provides us with

localhost:3000/blog/hello page

It is as simple as writing an HTML file under a webserver and accessing it using its path.

Next.js also provides a feature where the static pages can be rendered dynamically. Let me explain a use case

Let's say you write blogs that are maintained in a Database (actually they are usually maintained in a component called Headless CMS, but for simplicity, let's say a database)

If you want to fetch the content from that database instead of writing the content of the blog directly on the JS file. You can use the method getStaticProps

This will fetch us the content of the blog "WHILE BUILDING THE PROJECT" and pre-render the HTML pages for us

Server-Side Rendering
The HTML code is generated only when the request hits our server for Server-Side Rendering.

This is useful for use cases like Forum or Saas applications That has the potential to change for each request.

The pages (or routing) concept is similar to static rendering. Any js file returning a JSX component inside the pages folder is a separate page (or route)

Each time this route is called on the browser, the Next.js framework tends to render the page and provide a full HTML page as a response.

Any data that needs to be fetched from the backend for rendering this page can be returned using getServerSideProps.

For example - A table with all the stock prices can be rendered each time when a request is made. The required data to fill the stock price can be fetched inside getServerSideProps. Since the rendering can happen at the same location as the backend, the round trip time to make this request will be very very less.

## Dynamic Routing

There can be a use case where all the routes will not be known to us. For example - In the previous blog example I mentioned where the content can be fetched from the DB, Imagine what will happen when a new blog is added to the DB.

We cannot be writing a new page each time a new blog is written right? (i.e) The routes that can be reached can change dynamically based on a different source of data rather than the JS files we created.

For this, we have the concept of Dynamic Rendering. Any file under the pages folder with the name wrapped with brackets like [].js can have a method called getStaticPaths which can be used to return all the possible paths. These paths can also be rendered for each request using an option called blocking which needs to be set in the return value.

## Conclusion

Understanding the mental model of a framework easily helps us solve problems using that framework. While first learning React we all would have faced the issue of understanding the uses of a "state" and a "prop" while now it can be written without a second thought. In a similar way, to learn Next.js, the first thing to learn would be the uses of

- getStaticProps
- getServerSideProps
- getStaticPaths

Next.js provides a lot more great features like <Link/> <Image/> <Head/>. But once the above differences and uses are understood, the rest should be a walk in the park!

I would love to discuss this topic and learn more if you have something to share! 

[Originally Published in Dev.to](https://dev.to/poovamraj/how-to-think-in-next-js-learn-the-mental-model-15gg)