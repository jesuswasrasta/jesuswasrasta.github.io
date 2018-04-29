---
id: 1105
title: A Dapper fork for .NET 2.0
date: 2015-03-19T14:23:48+00:00
author: Ferdinando Santacroce
layout: post
permalink: /development/a-dapper-fork-for-net-2-0.html
categories:
  - Development
  - Software
tags:
  - .net
  - C#
  - dapper
  - orm
---
![I do not always use ORM, but when I do, I use Dapper.]({{ site.baseurl }}/images/I-do-not-always-use-ORM.jpg "I do not always use ORM, but when I do, I use Dapper.")  

I do not always use ORM, but when I do, I use Dapper.

<!--more-->

Jokes apart, I've been a lucky guy during these years: I had to work with relational databases, but they was usually not too complicated to handle.
  
I've not even think about using fat-ass <a title="Object-relational mapping from Wikipedia" href="http://en.wikipedia.org/wiki/Object-relational_mapping" target="_blank">ORMs</a> like <a title="NHibernate" href="http://nhibernate.info/" target="_blank">NHibernate</a> or so, first because lack of time to invest (not my fault, at least) and second because <a title="Object-relational impedance mismatch" href="http://en.wikipedia.org/wiki/Object-relational_impedance_mismatch" target="_blank">I never got them completely</a>.
  
Ok, we know, mapping objects properties with columns sounds great, but when things start to becoming more complicated, the effort to make this kind of ORMs to perform decently is the same, if not more, than write your own custom data layer by hand, using pure SQL.

But for small projects, for databases where you can easily design "a table for every class" or so, using ORMs can make you save some time.
  
When I found myself in a situation like this, couple of years ago, I started to dig the web looking for some small ORMs for .NET; what I want was a tiny piece of code to embed in my also tiny application, to be able then to persist some data on a SQLite database.
  
<a title="The Sorry State of .NET ORMs" href="http://www.codeguru.com/columns/dotnet/the-sorry-state-of-.net-orms.html" target="_blank">The web is full of Micro ORMs</a>, even if they are no longer a buzzword today; when people started to point out the complexity of big stack ORMs, some willing developers started to craft some other kind of them, more easy to understand and manage, and less difficult to maintain and deploy.
  
Unfortunately at the time I was on stuck with .NET 2.0, so most them was unsuitable for me, as they pretended at least .NET 3.5.

Fortunately on of the most appreciated .NET micro ORM out there is <a title="Dapper from StackExchange" href="https://github.com/StackExchange/dapper-dot-net" target="_blank">Dapper</a>, from <a title="Stack Exchange" href="http://stackexchange.com/" target="_blank">Stack Exchage</a> fellows; even it did not have a .NET 2.0 version, but porting the 3.5 one to .NET 2.0 was not too difficult, especially thanks to the great <a title="LinqBridge" href="https://code.google.com/p/linqbridge/" target="_blank">LinqBridge</a> library (that in fact is a port of Linq for .NET 2.0).

So I ported it, and it is still in use today for some projects I'm responsible where I work.
  
If someone else is in my (very sad) situation, where you can't migrate even to .NET 3.5 because of lazy Windows XP users, on <a title="Ferdinando Santacroce on GitHub" href="https://github.com/jesuswasrasta" target="_blank">my GitHub account</a> you can take a look at <a title="Dapper for .NET 2.0" href="https://github.com/jesuswasrasta/dapper-dot-net/tree/net-20" target="_blank">Dapper for .NET 2.0</a>.

Bye :)
  
Nando