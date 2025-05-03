# **Chapter 1 - A Pragmatic Approach** 👨‍💻

## **☑️ The Essence of Good Design**

> *Good Design is Easier To Change to Change Than Bad Design*

### **📝 ETC is a Value, Not a Rule**

You may need to spend a week or so deliberatily asking yourself **"Did the thing I just did make the overall system easier or harder to change?"**. Do this when you save a file, do this when you write a test, do this when you fix a bug.

*Note the situation in your engineering day book: the choices you have, and some guesses about change. Later when the code has to change you will be able to look back and give yourself a feedback.*

## **😈 DRY - The Evils of Duplication**

*Every Piece of Knowledge must have a single, unambiguous, authoritative, representation within a system.*

> *DRY - Don't Repeat Yourself*

If you have the same thing expressed twice, then you have to remember to change the others. Also, when you will forget, your program will be brought to it's knees by contradiction.

### **DRY is More Than Code**

DRY is about duplication of knowledge, of **intent**. it's about expressing the same thing in two different places, possibly in two different ways.

> *Make it Easy to Reuse*