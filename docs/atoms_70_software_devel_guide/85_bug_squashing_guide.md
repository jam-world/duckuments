# Bug squashing guide {#bug-squashing status=draft}

This unit describes how to debug your programs.

Do read this accurately top-to-bottom. If you think this is too long and too verbose to read and you are in a hurry anyway: that is probably the attitude that introduced the bug.

## Historical notes

First, count your blessings. You are lucky to live in the present. Once, there were actual bugs in your computer ([](#fig:actual-bug)).

<div figure-id="fig:actual-bug">
    <img src='actual_bug.jpg' style='width: 80%'/>
    <figcaption>
        "First actual case of bug being found."
        Read the story <a href="http://americanhistory.si.edu/collections/search/object/nmah_334663">here</a>.
    </figcaption>
</div>

## The basic truths of bug squashing {#bug-squashing-basic-truths}

### Truth: it is most likely something simple

The first truth is the following:

> It is always something simple.

People tend to make up complicated stories in their head about what is happening.
One reason they do that is because when you are frustrated, it is better to imagine
to battle against an imaginary dragon, rather than a little invisible Leprechaun who
is playing tricks on you.

Especially in an easy environment like Linux/ROS/Python with coarse process-level parallelization, there is really little space for weird bugs to creep in.
If you were using parallel C++ code, you would see lots of [heisenbugs][heisenbugs]).
Here, the reason is always something simple.

[heisenbugs]: XXX

### Truth: the fault is likely yours

The second truth is the following:

> While there are bugs in the system, it is more likely there is a bug in your code
> or in your environment.



## What could it be? {#bug-squashing-what-could-it-be}

### 20%: Environment errors

Any problem that has to do with libraries not importing, commands not existing, or similar, are because the environment is not set up correctly. Biggest culprit: forgetting "source environment.sh" before doing anything, or rushing through the setup steps ignoring the things that failed.

### 10%: Permission errors

Permission errors are most likely because people randomly used "sudo", thus creating root-owned files where they shouldn't be.

### 9%: Bugs with the Duckietown software

...

### 1%: Bug with ROS or other system library

...

### 10%: Problems with configuration files

Make sure that you have pulled duckiefleet, and pushed your changes.

Finally, given the questions we had so far, I can give you the prior distribution of mistakes:

### 50%: Programming mistakes

Of these, 80% is something that would be obvious by looking at the stack trace and your code and could be easily fixed.

## How to find the bug by yourself {#bug-squashing-asking-for-help}

### Step 0: Is it late? Go to bed. {#bug-squashing-go-to-bed}

If it is later than 10pm, just go to bed, and look at it tomorrow.

After 10pm, bugs are introduced, rather than removed.

### Step 1: Are you in a hurry? Do it another time. {#bug-squashing-dont-hurry}

Bug squashing requires a clear mind.

If you are in a hurry, it's better you do this another time; otherwise, you will not find the bug and you will only grow more frustrated.

### Step 2: Make sure your environment is sane using `what-the-duck`  {#bug-squashing-sane environment}

Finding a bug is a process of elimination of causes one-by-one, until you find the real culprit. Most of the problems come ultimately from the fact that your environment is not set up correctly.

We have a diagnostics program called `what-the-duck` that checks many things about the environment.

See: [](#what-the-duck)


So, first of all, run `what-the-duck`. Then, fix the errors that `what-the-duck` shows you.

The tool also produces a report about your system which you should attach to any request for help.

### Step 3: ...

TODO: to write


## How to ask for help?


I notice many people just writing: "I get this error: ...  How can I fix it?". This is not the best way to get help. If you don't include the code and stack trace, it's hard to impossible to help you.

The best way to get help is the following:

Gold standard: Provide exact instructions on how to reproduce the error ("Check out this branch; run this command; I expect this; instead I get that"). This makes it easy for an instructor or TA to debug your problem in 30 seconds, give you the fix, and probably fix it for everybody else if it is a common problem.

Silver standard: Copy the relevant code to a Gist (gist.github.com) including the error stack trace. Because we have no way to reproduce the error, this starts a conversation which is basically guesswork. So you get half answers after a few hours.



## How to give help {#bug-squashing-giving-help}


### Step 1: Ask for the output of `what-the-duck`

If there are errors reported, the students should fix those before worrying about their current problem. Maybe you or they don't see the connection, but the connection might be there.

Also, in general, errors in the environment *will* cause other problems later on.

### Step 2: Consider whether there are enough details to provide an informed answer

The worst thing you can do is guess work -- this causes confusion.


I encourage the TAs to *not* answer any nontrivial question that is not at least at the silver standard. It is a waste of resources, it will likely not help, and it actually contributes to the confusion, with people starting to try random things until something works without understanding why things work, and ultimately creating a culture of superstitions.
