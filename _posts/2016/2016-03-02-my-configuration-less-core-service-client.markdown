---
layout: "post"
title: "My Configuration-less Core Service Client"
date: "2016-03-02 11:24"
category: tridion
permalink: /tridion/config-less-core-service/
---
Often I have the need to create a Tridion Core Service client and connect with a content manager to retrieve information or make modifications. This is usually for some kind of one (or few) time query, update or maybe a quick PoC to see if something is even feasible or not. I prefer to do this is in a lightweight IDE (LINQPad) with a pre-saved query so that I can get into the code quickly without needing to set up a solution or project etc. in Visual Studio.

Usually, when you create a Core Service client, there's a bunch of WCF configuration needed in your app.config to set up the binding and endpoint. In my case however, I want to get up and running quickly, I want to keep my LINQPad query as portable and self-contained as possible and I'm happy to keep my (minimal) configuration in the code.

To this end, I re-use the following function to create a Core Service client by just passing in the URL of my content manager, a username and a password. I have this saved in a C# Program type query so that I can just open LINQPad, select it in the "My Queries" pane and start writing code within seconds.

<script src="https://gist.github.com/DavidForster/a35f4824a8d9f59f0cba.js"></script>

Of course, if the code starts to become more complex then I'll switch over to Visual Studio (with ReSharper) but for rapid prototyping, a short query or a quick update this works beautifully for me.
