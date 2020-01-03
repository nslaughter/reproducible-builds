# Deterministic Builds in Go

This repo is for experiments to identify non-determinism in Go builds. For now
it contains an experiment to illustrate the concept. In the future I plan to add
tools such as build scripts and specific instructions that will help in
achieving deterministic builds with Go.

If you build Go code for production deployment then keep reading.

# What's a deterministic build?

In short, deterministic builds mean that you can produce the exact same bits in
your build regardless of the build path or the platform you build on. Another
way to say this is that your builds are reproduceable.

If you don't know what it is then your builds certainly aren't deterministic.
The reason is that it makes sense to include machine specific information in
default builds. These are built more often and debuggers often rely on that
information by default.

# Why should I care?

If you're just proving that your code does something or distributing it to
others who will also compile it for themselves then this doesn't mean much. You
can probably get away with telling people minimum compiler versions that you
tested with at most.

If you care about validating your builds, fixing bugs discovered in production,
and generally knowing what's running then you need deterministic builds.

# What can I do with the code in this repo?

When you run the bash script included in this repo it will make subdirectories
that also include the trivial ("Hello, determinism!") Go program. Then it will
build from this in a variety of ways. And finally it calculates the script
calculates the SHA sums for comparison.

When you achieve the same SHAs in two different builds then you're mitigating
potential sources of determinism. WHen you've done that you'll want to write a
test for your build to ensure that you don't regress. As you achieve higher
levels of determinism in your builds you'll have more desirable properties in
your code.

That script is just there to show the results an experiment. But you can use the
concepts to start working on your build tests.
