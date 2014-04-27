---
layout: post
title: Factory pattern in golang
description: "factory pattern in golang"
tags: [varokas, golang, pattern]
comments: true
---
By varokas

### Initializing a struct
While trying to convert the foresee project to use Go. I found myself in need to be able to create 
a Go struct with an initial value. Sort of a "constructor" in Java. 

{% highlight go %}
type Data struct {
  votes map[string]int
}
{% endhighlight %}

Now if we simply just creating the Data struct using Data{}. we will get an error saying that votes
is nil. 

### Factory Method
I create a method to return Data Struct to make sure that the struct is properly initialized when use.

{% highlight go %}
CreateData() Data {
  return Data{make(map[string]int)}
}
{% endhighlight %}

Stil have no good way to prevent people from creating the struct directly (private constructors!!). But
this seems to be working fine for now.

