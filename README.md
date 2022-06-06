# Dispensables

## Learning Goals

- Explain the dispensables pattern

## Introduction

Dispensables happen when your code is bloated with things that don't actually
make it better or aren't actually useful. One thing to always keep in mind is
that simplicity is key to the ability to maintain code and "volume" is usually
not a friend of simplicity, i.e. the more you have to take in when you read
code, the more difficult it is to understand. As with all code smells, this is a
general rule, and less is not _always_ more.

## Comments

Comments can be a very useful feature, but needing a lot of comments for
specific code can be an indication that the code itself is too complex. It's
also worth considering that since comments are completely ignored by the
compiler and therefore by the runtime engine, they can very easily become out of
date.

In general, consider a) simplifying your logic or breaking it down further, b)
naming your methods and variables in expressive ways, and c) making your unit
tests the ultimate expression of the intention of your code.

On this last point, unit tests are a better way to tell your future self, or
your colleagues, what your intention was with your original code because, unlike
comments, unit tests are part of your code base and will break if your code
changes in such a way that your original functionality no longer works.

## Duplicate Code

This is the "copy-pasta" problem. If you find yourself copying code from one
method or one class to another, you likely have functionality that should be
abstracted somewhere else and re-used in those methods. Often, this kind of
repeated code can be extracted to "utility" methods.

## Data Class

If a class is nothing but a container for data fields, it may be that other
classes encapsulate behavior that impact the fields in this class. In this case,
re-consider your abstractions and move the management of the class' data in the
class itself.

## Dead Code

This happens when a variable or method (or an entire class) is no longer used.
This can happen when you re-factor code and make existing functionality
obsolete. Dead code should be removed as soon as you realize (and are confident)
that it is dead code, because the more it ages with the system, the less likely
we are to be confident that it is dead code in the future.

## Lazy Class

This is a more subtle version of the dead code smell, where a class may not be
completely obsolete, but so much of its code has been refactored that it no
longer holds significant functionality. When classes become so small that they
are hardly referred to or used, it might be time to consider getting rid of them
altogether.

## Speculative Generality

Generally speaking, we should write code for functionality that is not currently
required. Yes, we want to create flexible systems, and that's what our patterns
are here to support, but we shouldn't create a lot of complexity for
functionality that we do not currently need.

In our `Photographer` example, we create the `takePhotograph()` method. It's
quite possible, if not very likely, that a photographer will also need to
`reviewPhotograph()`, `chargeBatteries()`, `publishPhotographs()` and perform a
host of other functions. In this example, as in real life, we should not create
those methods until we know they are needed and we know how they should
function.

This is related to 2 basic general principles:

1. Humans are very bad at predicting the future
2. System requirements are difficult to capture and implement

Based on those 2 principles, we should always take extra care to understand our
system's requirements, and we should generally not try to anticipate them before
they are expressed.
