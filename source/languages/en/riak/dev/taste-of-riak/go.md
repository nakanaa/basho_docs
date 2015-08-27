---
title: "Taste of Riak: Go"
project: riak
version: 1.4.0+
document: guide
toc: true
audience: beginner
keywords: [developers, client, go]
---

If you haven't set up a Riak Node and started it, please visit the
[[Prerequisites|Taste of Riak: Prerequisites]] first and ensure you have
[a working installation of Go](http://golang.org/doc/install).

## Client Setup

First install the [Riak Go client](https://github.com/basho/riak-go-client):

```bash
go get github.com/basho/riak-go-client
```

<< Do we still want to use this taste_of_riak.go thing?: >>

Next, create the following directory structure in your `GOPATH` and download [taste_of_riak.go](https://github.com/basho/basho_docs/raw/master/source/data/taste_of_riak.go):

```bash
$ mkdir -p $GOPATH/src/basho.com/tasteofriak
$ cp ~/taste_of_riak.go $GOPATH/src/basho.com/tasteofriak
```

You can now compile and run this via the command line:

```bash
$ cd $GOPATH/src/basho.com/tasteofriak
$ go install
$ $GOPATH/bin/tasteofriak
```

Running it should return:

```
Creating objects...
Reading objects...
1
true
two
true
Deleting objects...
Creating, reading, and deleting complex objects...
3
true
```

If you are using a single local Riak node, use the following to create a
new client instance, assuming that the node is running on `localhost`
port 8087:

```go
...
```

...

## Creating Objects

First, let’s create a few objects and a bucket to keep them in.

```go
...
```

In this first example we have stored the integer 1 with the lookup key
of `one`. Next, let’s store a simple string value of `two` with a
matching key.

```go
...
```

Finally, let’s store a bit of JSON. You will probably
recognize the pattern by now:

```go
...
```

## Reading Objects

Now that we have a few objects stored, let’s retrieve them and make sure
they contain the values we expect.

Requesting the objects by key:

```go
...
```

Converting to JSON to compare a string key to a symbol
key:

```go
...
```

## Updating Objects

While some data may be static, other forms of data need to be
updated. 

Let’s update some values:

```go
...
```

## Deleting Objects

As a last step, we’ll demonstrate how to delete data. You’ll see that
the delete message can be called either against the bucket or the
object.

```go
...
```

## Working With Complex Objects

Since the world is a little more complicated than simple integers and
bits of strings, let’s see how we can work with more complex objects.

Take, for example, this <<Go struct/data>> that encapsulates some knowledge about
a book:

```go
book = {
    :isbn => '1111979723',
    :title => 'Moby Dick',
    :author => 'Herman Melville',
    :body => 'Call me Ishmael. Some years ago...',
    :copies_owned => 3
}
```

All right, so we have some information about our Moby Dick collection
that we want to save. Storing this to Riak should look familiar by now:

```go
...
```

If we fetch our book back and print the data:

```go
...
```

The result is:

```
...
```

Now, let’s delete the book:

```go
...
```

## Next Steps

More complex use cases can be composed from these initial create, read,
update, and delete (CRUD) operations. [[In the next chapter|Taste of
Riak: Querying]] we look at how to store and query more complicated and
interconnected data.

