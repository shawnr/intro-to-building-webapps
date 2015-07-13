# Evolving Approaches to Web Development
Over the years, web development has evolved. As a teacher, I feel like watching students learn HTML, CSS and Javscript looks a lot like reviewing the history of the Web. As a world, we have learned how to build websites and webapps.

Along the way we've come up with ideas that have helped us build better websites and webapps at the time. However, it's important as developers that we do not become complacent. There is always a new challenge, a new approach, and a new role to serve. How we are working in this book is the result of this continued evolution of web development.

## The challenge of progressive enhancement
The generation of Javascript libraries that birthed tools like jQuery in the mid-2000s was an era built around "progressive enhancement" (and, sometimes, progressive enhancement's less appealing cousin, "graceful degradation"). Developers could not be sure that all users would have browsers supporting Javascript, and if they did standards adoption among browser makers could be spotty, so the Javascript might not work. Because of this, developers had to always guard against breakage.

To help with this, tools like jQuery were made to enhance the vanilla HTML and CSS that would normally be delivered to the page. Properly done, pages could be created that were totally usable in a traditional, "click and refresh", way if the Javascript failed to load. But if the Javascript succeeded at loading, then pages would come alive with background updates, fancy interfaces, and more.

This approach is still worthwhile, and for many purposes it may still be a great idea to think about a project from a progressive enhancement point of view. For example, if you are building a site that is dedicated to showing off specific content, or providing access to media files, there is a lot that can be conveyed in traditional HTML. That content can be loaded and accessible to a wide range of devices, then Javascript, which is very reliable these days, can enhance the content to provide modern features.

But there are limitations to progressive enhancement. For example, what if you have a web application, and this application relies on the interaction of the user with Javascript to have any value? We aren't imaginging a site that wants to show you a video; imagine instead a site that wants to help you make a video. What is the value of a "static" or "traditional" page in that context? Probably not much.

## What webapps want
Dynamic webapps have a whole different set of considerations. If Javascript is not enabled, then the entire app is going to be unusable. So why bother having robust fallback content? (Other than a helpful error message, of course.)

Other issues come up when you build webapps:

* With jQuery, we could make a quick call to see if, for example, piece of content was favorited, or to send a new favorite to the server in the background. But what if we want to build an app where all of the screens have access to the data for objects in the system, and where we keep all that data synchronized across multiple views? This becomes very complex using only jQuery or similar solutions. We need a better way of **managing and modeling data** for use in our app.
* With progressive enhancement, we could enhance pages by making tab layouts or other custom effects. But what if we want to provide consistent headers and footers? What about slide-out menus that are the same across multiple views? These are the sorts of interface elements that exist in applications, but not so much in content-based websites. We need a better way to handle **templating views** so we can better manage our interface.
* Since we do not want to make a page request to the server on each click, we cannot rely on standard links to be interpreted by a web server to move our users around our webapp. This provides us with a challenge of knowing which views to show our users as they move through our application. We require a **routes mechanism** that can be used to define specific "locations" inside our webapp.

These are just a few of the major challenges we face when we try to build more app-like websites, and the old methods just don't work.

Fortunately, developers are never short of "new methods", and we are amid a boon of what are commonly known as "Single Page Application Frameworks". Webapps (also often known as "Single Page Applications (SPAs)") are the way developers are thinking these days, and developers have many different approaches to solving all of these challenges.