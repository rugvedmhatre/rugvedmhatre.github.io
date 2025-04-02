---
title: "Book Notes: Debugging"
date: 2025-03-11T06:30:00+05:30
toc: true
toc_label: "Notes"
category: book-notes
excerpt: Notes on "Debugging" by David J. Agans
seo_title: Debugging Notes
seo_description: Notes on "Debugging" by David J. Agans
---

_These are my notes on the "Debugging" book by David J. Agans._

# Introduction

These notes tell you how to find out what's wrong with your system, quick. Finding bugs the quickest helps you get quality products to your customers quicker.

**How does this work?**

- When it takes long time to find a bug, it is because we neglect some essential, fundamental rule; once we apply the rule, we quickly find the problem.
- People who excel at quick debugging inherently understand and apply these rules.

This book takes the "obvious" principles and helps you to remember them, understand their benefits, and know how to apply them.

The rules can be useful to engineers, programmers, technicians, consultants, etc. The rules are universal techniques that can help you to figure out any problem on any machine in any language using whatever tools you have.

This book is very focused on finding the causes of bugs and fixing them. It is not about quality development processes (that aim at preventing bugs in the first place). It is also not about test coverage analysis, test automation, or other QA techniques.

It is more than just troubleshooting. Debugging usually means figuring out why a design doesn't work as planned. Troubleshooting usually means figuring out what's broken in a particular copy of a product when the product's design is known to be good. The techniques in this book apply to both debugging and troubleshooting.

# The Rules

1. **Understand the system**
2. **Make it fail**
3. **Quit thinking and look**
4. **Divide and Conquer**
5. **Change one thing at a time**
6. **Keep an audit trail**
7. **Check the Plug**
8. **Get a Fresh View**
9. **If you didn't fix it, it ain't fixed**

## Understand the System

- Read the manual
- Read everything in depth
- Know the fundamentals
- Know the road map
- Understand your tools
- Look up the details

## Make it Fail

_There are three main reasons to make it fail: so that you can look at it, so you can get a clue about the cause, and so you can tell when it's fixed._

- Do it again: Look at what you did and do it again. Write down each step as you go. Then follow your own written procedure to make sure it really causes the error.
- Start at the beginning: Try to start the sequence from a known state, such as a freshly rebooted system.
- Stimulate the failure: When the failure sequence requires a lot of manual steps, write an automated process. For example, if your network software gets errors under high-traffic conditions, run a network-loading tool to simulate the load, and thus stimulate the failure.
- But don't simulate the failure: The book recommends to simulating the conditions that generate the error, and not simulating the failure mechanism.
- Find the uncontrolled condition that makes it intermittent
- Record everything and find the signature of intermittent bugs
- Don't trust statistics too much: When you capture enough information, you can identify things that are always associated with the bug or never associated with the bug. Those are the things to look at as you focus on likely causes of the problem.
- Know that "that" can happen: Don't make assumptions about the system, and discard the error.
- Never throw away a debugging tool: Sometimes one test tool can be reused in other debugging situations.

## Quit Thinking and Look

- See the failure: Make sure you see what's actually going wrong. Looking is usually much quicker than the
  guesswork shortcut, because the shortcut often leads nowhere.
- See the details: "Keep looking until the failure you can see has a limited number of possible causes to examine."
- Build instrumentation in: You should think about debugging right from the start of the design process. Make sure that instrumentation is part of the product requirements.
- Add instrumentation on: If you didn't or couldn't build instrumentation in, at the very least, add it on.
- Don't be afraid to dive in: If there's a bug in the code, you're going to have to rebuild the software in order to fix it. Therefore, you should be willing to rebuild the software in order to find the bug in the first place.
- Watch out for Heisenberg: You can't get an accurate measurement, because the test instrumentation affects the system under test.
- Guess only to focus the search: You should confirm your guess is correct by seeing the failure before you go about trying to fix the failure.

## Divide and Conquer

- Narrow the search with successive approximation (like binary search):
  - Get the range of the search
  - Determine which side of the bug you are on
- Use easy to spot test patterns
- Start with the bad
- Fix the bugs you know about
- Fix the noise first

## Change One Thing at a Time

- Isolate the key factor
- Grab the brass bar with both hands: What this means is, to overcome the temptations to start "fixing" things as soon as you see some errors. It is always better to wait (i.e. grab the brass bar with both hands) and analyze all problems to see exactly what is going on and "fix" one thing at a time.
- Change one test at time
- Compare it with a good one
- Determine what you changed since the last time it worked

## Keep an Audit Trail

- Write down what you did, in what order, and what happened as a result
- Understand that any detail could be the important one
- Correlate events
- Understand that audit trails for design are also good for testing
- Write it Down!

## Check the Plug

- Question your assumptions
- Start at the beginning
- Test the tool

## Get a Fresh View

- Ask for fresh insights
- Tap expertise
- Listen to the voice of experience
- Know that help is all around you
- Don't be proud: Don't be afraid to ask for help
- Report symptoms, not theories
- Realize that you don't have to be sure

## If You Didn't Fix It, It Ain't Fixed

- Check that it's really fixed
- Check that it's really your fix that fixed it
- Know that it never just goes away by itself
- Fix the cause
- Fix the process

# References

1. Agans, David J.. Debugging: The 9 Indispensable Rules for Finding Even the Most Elusive Software and Hardware Problems. United States, AMACOM, 2002.
