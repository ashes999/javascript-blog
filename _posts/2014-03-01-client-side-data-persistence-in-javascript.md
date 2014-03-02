---
layout: post
title: "Client Side Data Persistence in Javascript"
description: ""
category: 
tags: []
---
{% include JB/setup %}

Your client-side JS application needs to save some data across invocations of the application -- maybe a user login, or some game data. How can you do this, *without* any server code?

Cookies come to mind, but cookies are limited to 4kb each (x20 cookies = 80kb max). That may not be enough.

As of 2013, there are two prominent options: HTML5 Web Storage and IndexedDB.

### HTML5 Web Storage
HTML5 Web Storage is an old standard. It works [across almost all browsers](http://caniuse.com/namevalue-storage) (including older ones). It allows you to save up to 5MB (at least) on the client-side, and sports a really simple API:

{% highlight javascript %}
localStorage.userName = 'ashes999'; // saved
delete localStorage.userName; // gone
{% endhighlight %}

There are two main limitations with this:

- **5MB of Data:** It may not be enough depending on what you're storing. And the exact amount, although guaranteed to be at least 5MB, varies from browser to browser.
- **The data is shared across the whole domain:** All applications on the same domain share the 5MB limit; so if you have, say, a hosted games portal, you're forcing those games to share the 5MB of data.

For the last reason in particular, I decided to look further at IndexedDb.

### IndexedDb

IndexedDB is a similar to Web Storage (it's an object database). It sports some additional benefits:

- Transactional (like relational databases)
- No storage size limit

Unfortunately, it also suffers from two drawbacks:

- The API is somewhat more complicated to use
- It [requires a recent browser](http://caniuse.com/indexeddb) (and doesn't work on mobile browsers yet, other than Android OS 4.4).

### Which Option to Choose?

I suggest you go with HTML5 Web Storage, *unless you're hosting multiple apps on a single domain.* In that case, I suggest you use IndexedDb. There's a particularly usable wrapper called [PouchDB](http://pouchdb.com/), with some other benefits (eg. can synchronize to a web-hosted DB via a RESTful API).

My other recommendation is to *use in-memory storage, but warn the user that their data won't be saved.* Given how easy it is to upgrade browsers, it shouldn't be a problem do so; plus, users can test-drive your application (without inter-session persistence) and see how it works out for them.
