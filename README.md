[goos-book]: http://www.growing-object-oriented-software.com/
[Nat Pryce]: http://www.natpryce.com/
[Steve Freeman]: http://www.higherorderlogic.com/
[goos-ruby]: https://github.com/tom025/goos
[solid_principles]: http://en.wikipedia.org/wiki/SOLID_(object-oriented_design)
[jruby]: http://jruby.org/
[smack]: http://www.igniterealtime.org/projects/smack/
[sse]: http://en.wikipedia.org/wiki/Server-sent_events
[puma]: https:github.com/puma/puma
[cucumber]: https://github.com/cucumber/cucumber
[rspec]: https://github.com/rspec/rspec
[capybara]: https://github.com/jnicklas/capybara
[selenium]: https://github.com/SeleniumHQ/selenium

# GOOS Rails #

This project is an investigation into how a goos style of architecture and
development fits in a rails project.

[Goos(Growing Object Oriented Software Guided by Tests)][goos-book] is a book by
[Nat Pryce][] and [Steve Freeman][].

## Introduction ##

I read the goos book a while ago and wanted to follow the code examples. Being
a ruby programmer I thought it would be a useful exercise to [port the code
examples over to JRuby][goos-ruby]. I had a lot of ideas
for my professional work after completing the book that turned out to be very
useful. This is an attempt to share some of those ideas.

I am a fan of Rails but not of the *Rails Way* of development, I feel like we can
do better as a community with the design of our Rails applications.

One of the biggest problems I see in the ruby community at the moment is the
large number of unwieldy monolithic rails applications that are difficult to
maintain due to high coupling and low cohesion. I believe that there are number
of different techniques that are already well documented that can help keep a
medium to large rails application to remain healthy. Such as:

  * Dependency Injection.
  * The [_SOLID_][solid_principles] principles. Most notably the
  _Dependency Inversion Principle_.
  * A ports and adapters style of architecture.

The _Rails Way_ is a very well understood style of developing Rails
applications amongst the ruby community. It's main advantages are its
predictability and it's simplicity. However I find that the simplicity quickly
succumbs to complexity in all but the some of more trivial problem domains. Not
only that, once the _Rails Way_ has become an established pattern in the project
it becomes very difficult to refactor to a better design. It also produces code
that is difficult to test so coverage may suffer as a result as well.

## The Problem ##

The problem is the same one from the book.

A company of auctioneers have commissioned a new application to help with the
bidding on items in a auction house. The auction house has a interface using an
XMPP protocol. The auctioneers want a system that integrates with the auction
house that can automatically bid for items upto a set threshold and report the
status of each auction.

## The Implementation ##

I have decided to use [JRuby][jruby] so that I can use the
[XMPP client library(smack)][smack] from the book that is written in Java.

The UI is a web browser and the auction events are sent to the browser using
[Server Sent Events(SSEs)][sse].

The application server used is [puma][], as it a good fit for long running
concurrent requests

The testing frameworks used are [cucumber][] and [rspec][] using [capybara][]
and [selenium][] for testing through the browser.
