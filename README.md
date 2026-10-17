# engineering

How I want software built in my projects. Give it to anyone, person or
model, who works on them.

It follows David Farley's *Modern Software Engineering*. Software is
something you learn your way through, so work in small steps and get
feedback and evidence along the way. And code only stays easy to change if
you manage its complexity. The rules below are how I apply that.

## Evidence

Evidence decides, not opinion. If you think something is wrong, a plan, a
review comment or what I asked for, say so and discuss it. Then get
evidence: a test, a measurement, a small experiment. The other person may
be thinking on a different layer, so the discussion matters too.

If you don't know something for sure, say "not right now", or find out.
Don't pass a guess off as an answer.

## Talking before you act

When you get a task or an instruction, say what you understood and what you
plan to do before you do it. Do this even when you agree. You can skip it
once a team works together very smoothly.

If a detail is left open, like the wording of a message or the name of an
endpoint, decide it yourself and follow the code around it. Ask only when
you're really unsure.

## Issues and done

An issue is a best guess made before the work starts. Nobody can think
everything through in advance. If the work shows the issue is wrong, for
example the login it asks for turns out to be insecure, or something can't
be done, stop and raise it. Don't build it to the letter.

A task is done when:

- the tests pass, including new ones for the change
- it was checked by hand, where that's possible
- it was reviewed, and the obvious bugs are fixed
- the linters pass and CI is green

The acceptance criteria count too, but they don't decide on their own.

## Scope

If you find the same bug next to the one you're fixing, fix it too, in its
own commit. A related bug is a judgment call. It depends on the size of the
codebase, how much code is affected and how bad the bug is. Raise the rest
by saying it, like at a standup.

If you find a design problem, fix it right away, as its own change. A
database query for each item in a list is one. It usually means the
interface only offers "get one".

## Reading code

Don't read a codebase to get oriented. Read the part you hook into. It
should be easy to find, because the structure is good or the issue names
it. Assume the rest looks like what you saw. To add a field, read one
model, not all of the database code. Read more only when you need it: the
code next to yours, something special like a JSON type, or a test that
fails for a reason you didn't expect.

Code that looks alike isn't always the same thing. Assuming it is helps you
decide what to read. It's no reason to merge it.

## Design

Build what's needed now, not what might be needed later. Code is cheap to
change once a second case shows what it needs. Think ahead only where a
decision is expensive to undo, like stored data or an API that others
depend on.

Wait for a pattern before you abstract it. One case doesn't show which
pattern is real.

Use a library when more code benefits from it, when the code would be
complex, or when the domain is easy to get wrong, like time or parsing.
Pick one that's well established: maintained, with a compatible license, a
reasonable size and few dependencies of its own.

## Tests

A test fails before you write the code that makes it pass. The exception is
a pin, a test that locks down behaviour that already works. A good test:

- follows arrange, act, assert, if it's a unit test
- tests one thing
- stands on its own and doesn't affect other tests
- is small enough that, when it fails, you can tell whether the test or the
  code is wrong

A flaky test is a bug. Fix it, because it breaks CI for everyone.

## Errors

Anything that "should never happen" will happen, so handle it. Whether it's
a normal outcome with a proper answer, or a bug with a clear error, depends
on the case.

## Sensitive changes

For changes to logins, permissions or user data, write more tests, think
about how the change could be abused, and have it reviewed for security.

## Reviews

If you think a review comment is wrong, find evidence, or make a judgment
call when that's too hard or it's a matter of style. Then either fix it or
answer it. If an automated reviewer keeps making the same mistake, change
its settings in the same commit.

## Reporting back

When you're done, say that it's done, where to look, and what was weird or
unexpected. What else belongs in it depends on the work.

If a task turns out much harder than expected, say why. Don't explain the
estimate. Explain the complexity nobody saw, so the team learns about its
code.

## Rules

There's no rule without exception. When you make one, say so, for example
in the commit message.

## When an AI does the work

- Don't open issues on your own. In a public repository, an issue is
  published. Say it in the conversation instead.
- Don't estimate how long something takes. Keep working until it's done,
  then say in a message what turned out harder. Stop and raise it right
  away only if it's critical or the task has become very different from
  what was asked.
