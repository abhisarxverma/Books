# **Chapter 3️⃣ - The Basic Tools**

## **🐚 Shell Games**

Benefit of GUI IDE Interfaces - ***WYSIWYG*** *What you see if what you get*
Disadvantage of GUI IDE Interfaces - ***WYSIAYG*** *What you see is all you get*

>👉  **Use the Power of command Shells**

Gain familiarity with the shell, and you'll find your productivity soaring.

## **A shell of you own**

*As the woodworkers customize their workspace, the programmers should customize their shell*

Common changes:
1. *Setting color themes*
2. *Configuring a prompt* - Prompt that shows when your shell is ready for you to type command and use it.
3. *Aliases and shell functions* - Turn commands that you use a lot into simple aliases
4. *Comand completion* - Take the Tab autocompletion to much further for full commands.

*You are gonna spend a lot of time in shell, make it your home.*

## **Power Editing 🖋️**

Use as many editors you want, but work towards fluency in each

> **👉 Achieve Editor Fluency**

*Just by making your editing 4% more faster and if you edit for 20 hours a week, you can get an extra week.*

In Fluency, your thoughts will flow and your programming will benefit.

### **What does "Fluent" Mean?**

Challenges that you will do, you will be fast editor:

- When editing text, move and make selections by character, word, line, and paragraph.
- When editing code, move by various syntactic units (matching delimiters, functions, modules,...).
- Reindent code following changes.
- Comment and uncomment blocks of code with a single command.
- Undo and redo changes.
- Split the editor window into multiple panels, and navigate between them.
- Navigate to a particular line number.
- Sort selected lines.
- Search for both string and regular expressions, and repeat previous searches.
- Temporarily create multiple cursors based on a selection or on a pattern match, and edit the text at each in parallel.
- Display compilation errors in the current project.
- Run the current projects's tests.

### **Moving towards Fluency**

You cannot know all the commands in a IDE, but everytime you find yourself doing something repetitive, you must ask yourself "There must be a better way for this".

Once you discover a new feature, consciously look for opportunities to use the new superpower cause at start you will not remember that you have new superpower.

### **Growing your editor**

Dig into your editor's extension language.Work out how to use it to automate some of the repetitive things you do. Often you'll just need a line or two of code.

Sometimes you might take it further still, and you'll find yourself writing a full blown extension. If so, publish it: If you had a need rot it, other people will too.

## **Version Control**

### **It starts at source**
With a properly configured source code control system, you can always go back to a *previous version* of your software.

> **👉 Always use Version Control**

### **Branching out**
You can create a branch at any point in your project's history, and any work you do in that branch will be isolated from all other branches. Multiple people can even by working on a branch; ina way, branches are like little clone projects.

## **🪰 Debugging**

### **Psychology of debugging**

> **👉 Fix the problem not the blame**

It doesn't really matter whether the bug is your fault or someone else's. It is still your problem.

### **A debugging mindset**

Before you start debugging. It's important to adopt the right mindset, turn off many of the defenses you use each day to protect your ego, tune out any project pressures you may be under, and get yourself comfortable.

> **👉 Don't Panic**

Don't waste a single neuron on the train of thought that begins "but that can't happen". Resist the urge to fix just the symptoms you see. Always try to discover the root cause of a problem, not just this particular appearance of it.

### **Where to start**

- Before you start to look for the bug, make sure that you are working on code that built cleanly - without warnings.
- You can't afford to waste time debugging the coincidences, you first need to be accurate in your observation.
- You may actually need to watch the user to get the sufficient level of detail.

### **🐞 Debugging strategies**

**Reproducing Bugs**

The best way to start fixing a bug is to make it reproducible.

But we want more than a but that can be reproduced by following some long series of steps; we want a bug that can be reproduced with a single command.

> **👉 Failing Test Before Fixing Code**

### **😐 Coder in a Strange Land**

> **👉 Read the Damn Error Message**

What if it's not the crash? What if it's just a bad result?

Keeping pen and paper nearby to jot down the notes while tracing the problem is very helpful cause you don't lose the trace of where you started the chase. You could lose a lot of time by getting back to start if you don't know.

**Sensitivity to Input Values**

It may happens that your program works fine with all the test data and survives the first week of production with honor. Then it suddenly crashes when fed with particular dataset.

You can work your way backwards. But sometimes it is easier to start with the data.
- Get a copy of that same dataset.
- Feed that into your local running copy of app.
- Make sure that it crases.
- Binary Chop (Binary search) the data until you find which input values are leading to the crash

### **🪓 The Binary Chop**

> The idea is simple. If you have to find something in a sorted array, you can either search one by one, for which you will go roughly till half the array. But it's faster to user the *divide and conquer approach.

**The Binary Chop**
- Take a value from the middle of the array
- Check if it is the value you are finding, if yes, then you got it.
- Else, Check if it is greater than then value you are finding, if yes, then you will find your value in the left subarray and completely discard the right subarray.
- Else, Check if it is smaller than the value you are finding, if yes, then you will find your value in the right subarray anc completely discard the left subarray.
- Do this until you find your value or there is no subarray on either side to search on which means your number is not in the array.

While trying to do a massive stacktrace, you can apply the same approach to find the which function mangeled the error, you can do a chop in the middle and check if error manifest there, if yes then you need to focus on the frames before, otherwise focus on the frames after.

**Version control use with Binary chop**

If your team has introduced a bug during a set of releases, you can use the same type of technique. Create a test that causes the current release to fail. Then choose a half-way release between now and the last known working version. Run the test again, and decide how to narrow your search.

**Logging and/or Tracing**

*Debuggers* generally focus on the state of the program now.
*Tracing statements* are those little diagnostic messages you print to the screen or to a file that say things such as "got here" and "value of x = 2."
You can use tracing statements to *drill down into the code*.

**Rubber Ducking**

**Explaining the problem to *another person*** you must explicitly state things that you may take for granted when going through the code yourself. By having to verbalize some of these assumptions., **you may suddenly gain new insight into the problem.**

**Process of Elimination**

Some other thing than your code had the bug should not be your **first thought**.Even if the problem does lie with the thir party, you will still have to eliminate your code before submitting the bug report.

> **👉 "select" Isn't Broken**

## **😮 The Element of Surprise**

When faced with a "surprising" failure, you must accept that one or more of your assumtions is wrong.

> **👉 Don't Assume It, Prove it**

When you come across a surprise big, beyond merely fixing it you need to ask some questions:

1. why this failure wan't caught earlier?
2. Are there any other places in the code that may be susceptible to this same bug?
3. If it took long time to fix the bug, ask yourself why?
4. Is the problem being reported a direct result of the underlying bug, or merely a symptom?
5. Is the bug really in the framework you're using? Is it in the OS? Or is it in your code?
6. If you explained this problem in detail to a coworker, what would you say?
7. If the suspect code passes its unit tests, are the tests complete enough? What happens if you run the tests with this data?
8. Do the conditions that caused this bug exist anywhere else in the system? Are there other bugs still in the larval stage, just waiting to hatch?

If the bug is the result of someone's wrong assumption, discuss the problem with the whole team: if one perosn misunderstands, then it's possible many people do.

## **🔤 Text Manipulation**

Learning and using a text manipultaion language, you can quickly hack up utilities and prototype ideas - jobs that might take five or ten times as ong using conventional languages.

> **👉 Learn a Text Manipultion Lanugage**

## **📒 Engineering Daybooks**

**Main benefits of the Daybook -**

- It is more ***reliable than memory***.
- It gives you a place to ***store ideas*** that aren't immediately relevant to the task at hand. That way you can continue to concentrate on what you are doing, knowing that the ***great ideas won't be forgotten***.
- It acts as a kind of ***rubber duck***. When you stop to write something down, your brain may switch grears, almost as if talking so someone - ***a great chance to reflect***.

*Even you can look back at what you were doing years ago, the peoples, the projects, the fun*

> Try keeping an Engineering Daybook. Use paper, not a file or a wiki: there's something special about the act of writing compared to typing.

<div style="display: flex; justify-content: center">
    <h1 style="font-family: "monospace">CHAPTER OVER</h1>
</div>