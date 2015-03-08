# Alice 

[![Build Status](https://travis-ci.org/justinas/alice.svg?branch=master)](https://travis-ci.org/justinas/alice)

Alice provides a convenient way to chain 
your httprouter middleware functions and the app handler.

In short, it transforms

    Middleware1(Middleware2(Middleware3(App)))

to

    alice.New(Middleware1, Middleware2, Middleware3).Then(App).

### Why?

None of the other middleware chaining solutions
behaves exactly like Alice.
Alice is as minimal as it gets:
in essence, it's just a for loop that does the wrapping for you.

Check out [this blog post](http://justinas.org/alice-painless-middleware-chaining-for-go/)
for explanation how Alice is different from other chaining solutions.

### Usage

Your middleware constructors should have the form of

    func (httprouter.Handle) httprouter.Handle

Note that Alice makes **no guarantees** for
how one or another piece of  middleware will behave.
It executes all middleware sequentially so that if a
piece of middleware were to stop the chain,
the request will not reach the inner handlers.
This is intentional behavior.

Alice works with Go 1.0 and higher,
but running tests requires at least Go 1.1.

### Contributing

0. Find an issue that bugs you / open a new one.
1. Discuss.
2. Branch off, commit, test.
3. Make a pull request / attach the commits to the issue.
