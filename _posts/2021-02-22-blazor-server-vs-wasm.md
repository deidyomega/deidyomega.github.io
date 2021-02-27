---
layout: post
title: Blazor Server and Blazor Web Assembly 
tags:
  - coding
comments: true
---

tldr: Blazor Server has no value over current Microsoft offerings, Blazor WebASM is amazing, but due to its large download/startup time isn't likely worth using.

## Blazor Server

Blazor Server, is a C# server communicating with the client using SignalR.  For real time offerings, there are a lot of better ways to handle this process.  For not real time offerings (like a "normal" webapp), there is no advantage to this approach when compared to MVC.  As far as I can tell.  My fear is, if you were to make a SignalR offering, and it was successful, you now have to deal with scaling an application which EACH CLIENT must STAY connected.  Its quite a bad system imho.  Just use asp.net mvc.

## Blazor Web Assembly

Blazor WASM, is C# compiled to WASM, then ran on the client.  I really see a future with this technology.  However at its current state, its only useful in a few situations:

1. If you have a C# library you want to run on a client, as a PWA.
2. You are writing an app that will be opened infrequently but used often.  (Maybe a video game.  Once it loads, people will be on the page for a while)
3. You are a developer who cant be bothered to learn javascript.

There is a potential future with this technology.  I could see MS bundling the C# runtime in MS Edge, thereby removing the entire download step of all the code minus your custom application logic.  This should reduce startup time significatenly.   Then for enterprise applications where people may spend 8 hours a day on the app, I could see this being a viable approach.  At that point, edge or the browser really just become an update mechinism to your application.

However outside of enterprise app developement, I dont see this being viable for many situations. ( Games not included )
