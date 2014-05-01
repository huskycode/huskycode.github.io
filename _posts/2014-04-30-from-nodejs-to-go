---
layout: post
title: From nodejs to Golang
tags: [varokas, foresee, golang, nodejs]
comments: true
published: true
description: A quick look back on converting a nodejs project to Go
---
By Varokas

### No more love for nodejs?
It is no secret that I have been playing with the idea of porting [foresee](http://www.huskycode.com/foresee) project
to be in Go. so here's my quick feedback on the work so far.

I always think that Go would radically replace what nodejs is used for today. It is a simple 
and powerful language gearing towards writing system program. One that takes multiple requests 
from the web and churn the response as quick as your io can take it, with help of the "go" routine
and channels. A concept I found very intuitive to understand (vs the classical actor model in scala).

### Type-safe javascript

My personal feeling towards Go is that if you squint hard enough, you might misplace it with Javascript. 
A weird feeling I know, but I think it comes from the fact that Go has no class / extends / implements.

So if I see something like this in javascript.

{% highlight javascript %}
var cache = {
  data: {}
  get: function(key) { return data(key); }
}

{% endhighlight %}

I can readily see myself doing this in Go.

{% highlight go %}
type InMemoryDataStore struct {
  dataByRoom map[string]Data
}

func (mds *InMemoryDataStore) Get(room string) Data {
  return mds.dataByRoom[room]
}
{% endhighlight %}

Not only that I like that the logic is not crammed in a confined space. Type-safety help 
big time as well. With that reason alone TDD is much more pleasant on Go. [Red/Green/Refactor!](https://github.com/huskycode/foresee/commit/e13bbabf733e039757f906b3c4521e564132b653)

### One executable deployment
The goal for foresee project is to make it as easy for the user to download and use it as possible. I 
want people to download this project and open it up for their own. 

That means. No JRE installation. No PATH settings. And now moving to Go, no npm install as well. 

Just one executable.

### Any problems?
Namely these things in brief

* Quality of libraries : most of these are young, and not very well tested.
* Language : With no inheritance and lambda I feel that this will restrict the size of program Go could be. More on that later. 
* Package Management : or lack thereof. Every language now has one (even PHP!). Go has none.

Turns out on of the big communication library I want to use: socket.io is not working very well for me. And it is not
readily testable as well. Before I jump in too deep to figure that out. Lets launch foresee in nodejs for now.
