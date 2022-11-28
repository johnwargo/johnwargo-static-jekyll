---
layout: post
title:  Domino & BlackBerry Java Applications Part 2.5
date:   2009-09-20 14:37:16
categories: Miscellaneous
---
  
I’ve been getting a lot of questions and comments about the article series (which is great, keep them coming). I got some questions from Brendan yesterday and it was clear that I really didn’t cover a very important part of the stub generation process. It’s not that I missed it; it’s just that I was primarily trying to demonstrate something and didn’t cover all of the background information you would need to use this process with your web services. 

In the example I’ve provided with this article series ([Part 1](index.php/Domino/dbja1.html) and [Part 2](index.php/BlackBerry/dbja2.html)), I’ve deliberately selected a base web service that’s simple enough to be easily consumed using the capabilities provided by JSR 172. Since the specification (yep, it’s not a ‘standard’ as was pointed out last week) was designed for mobile devices, its designers deliberately selected a limited number of data types it would support thinking that it would reduce the potential load on devices and cover a majority of implementations.

When I created the service, I created it with the knowledge that the Sun tools for creating the stub program only supported certain data types and I made sure I used them. The problem arises for those of you who want to build BlackBerry applications that consume web services that were not built with mobile users in mind. Let’s dig into the detail...