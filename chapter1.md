# Chapter the First
## Preliminary Ideas

JavaScript is an implementation of ECMAScript, a standardized browser scripting language that powers all aspects of the WWW. What exactly does JavaScript do? It adds behavior to web pages, it allows you to do things asynchronously, it allows you to store things on the client, in short: JavaScript allows you to program the web.

What are all these words that people use?
- Node: a stand-alone (no browser) JavaScript interpreter (thing that runs your code) built out of Chrome. It's wicked fast and built to do things asynchronously.

- jQuery: jQuery is a library (a bunch of files with code in them like yours) that turns ugly, annoying JavaScript into nice, elegant JavaScript.

```js
// for example:
 $('#my-id').hide();
//is the equivalent of:
var myId = document.getElementById('my-id');
myId.style.display = "none";
```

- Angular JS, Ember JS, Backbone JS: These are front-end Model-View-Controller (MVC) JavaScript frameworks. The point is to make the piles and piles of JavaScript you write into fewer piles through organization and code reuse.

## Programming Principles

Are you an engineer or an artist? Is there a difference at a certain point? Almost any field of study you can imagine has a sub-field called "Computational [field]." So there are all these people out there who are Neuroscientists, Astronomers, Economists, Finance professionals etc. that program for fun and profit: so can you! There are many, many people out there that would love to tell you their opinions on how to code "properly" and the like. Hey, I guess that's what I'm doing but really I'm just relaying the stuff I've seen so far that I've found useful. Here are some acronyms.

- KISS: Keep it simple, stupid. Your goal as a programmer is to translate your idea into code simple. If the code you are writing is growing and growing but not making much progress in accomplishing your goal, you should consider using your delete key liberally. There are an infinite number of ways to code any one thing but only a few of them are any good.

- DRY: Don't Repeat Yourself. If you find yourself typing essentially the same things over and over (or just more than once) then it would be a good opportunity to make a function or a method that encapsulates that procedure.

- Convention over Configuration: A lot of people have been coding for a long time and a few good 'patterns' have emerged. This term is generally reserved for web development (at least to my knowledge) but essentially the idea is to not fight the current on how to name things, where to put files, etc.. That is, just use the defaults: it will seem like magic at first but the first time you encounter an error that occurs from your departure you'll learn the secrets behind the magic pretty quickly. But, like any programming paradigm or idea, there is a counter: in this case, Configuration over Convention. That is, do whatever you want your framework should be agnostic to your naming, organizing etc.. Both of these principles have their place much like the rest of the ideas we're discussing here so just keep them in mind as your journey continues.

- YAGNI: You Ain't Gonna Need It. Here's a good one that throws a bit of a wrench in writing 'elegant' code: with all these modern computers, cloud technology and the like, making small savings/ pouring over code for optimizations will generally not matter. You might think that denormalizing your database will make your application run faster but there are probably some more glaringly obvious changes/ refactoring you could do for a comparable gain in application efficiency. That is, don't worry about it, having so much traffic that your site breaks is a good problem that you can solve later provided you have some data to inform you.

- Horses for Courses (HFC): In truth, this isn't something I learned in the course of programming, I learned it in International Finance at Florida State from a professor by the name of James Cobbe. This lesson had little to do with International Finance (like most good lessons in economics courses) but instead for horse racing. The idea here is that the performance of a horse is correlated with the track on which the horse is running. Mud, clay, grass, turf - each of these scenarios (I have no clue on which courses horse racing occurs) will have a significant impact on which horse will do the best. So, the tools you use (for fun and profit) should be suited for the application. For example, you need to make an application that displays blog posts. Would you write it in Enterprise Java Server Pages, use an Oracle Database, and put it on a cluster of extra large AWS machines? Probably not, that's overkill unless you are managing millions of visitors, millions of blog posts, etc.; just use WordPress or Jekyll. Point is, selecting the right tools for the job isn't always so obvious but it's totally worth some thinking and searching.

- Typing is BAD. This isn't really a subtle philosophical lesson, it's just practical. Every key stroke you make is a step towards carple tunnel, wrist issues, elbow issues, you name it. If this is something you want to do for a living, you'll probably be typing a lot so every little saving in typing is worth it's weight in gold for your longevity as a programmer. It is absolutely worth learning as many shortcuts with the keyboard as possible, not just for a text editor but for your operating system. Learning the command line is super valueable but it's also worth your time to write configurations to make your own shortcuts. Many people are proud of their .vimrc, .bashrc, and .gitconfig files and many of them are available on the internet for you copy and paste. Do it.

- Mice are BAD. The mouse was made to make Graphical User Interfaces (GUIs) easier to navigate. Mice are great, very fancy but entirely unnecessary. You can do everything with a keyboard you can do with a mouse plus more. Every time you take a hand off of the keyboard and on to the mouse, you lose precious time. You may be saying: "psh, come on - how much time could I possibly save?" Whoa there, why so argumentative? Time to math: if you use a mouse every time you are done typing something, say that happens 50 times a day. The motion of moving your hand from the keyboard, placing it on the mouse, moving the mouse, taking your hand back off of it and placing it back on the keyboard takes probably around 2 seconds on average. That's about 100 seconds per day, 500 seconds in a 5 day work week. So you lose 20 minutes a week which is time you will never get back. Feel free to take some measurements and figure it out on your own, hopefully you'll realize that your mouse is almost completely useless.

