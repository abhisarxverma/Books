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

## **🫅 Orthogonality**

> *In computing orthogonality refers to the kind of independence or decoupling.*

Two or more things are orthogonal if changes in one do not affect any of the others. In a well designed system you can, the database code will be orthogonal to the user interface: you can change the interface without affecting the database, and swap the databases without changing the interface.

### **Benefits of Orthogonality**

> **Eliminate Effects Between Unrelated Things - We want to design components that are self-contained, independent, and with a single, well-defined purpose. You know that you can change one without having to worry about the rest.**

- **Gain Productivity**
    - *Saves time* - There is no need to keep changing existing code as you add new code, which saves a lot of time and energy.
    - *Promotes reuse* - Easier to combine with other components and reconfigure and reengineer.
    - *More functionality* - Combining orthogonal components, gets more functionality per unit.

- **Reduce Risk**
    - *Isolation* - Diseased sections of the code are isolated, less likely to spread the symptoms to the rest of system.
    - *Less fragile* - Make small changes and fixes to a particular area, and any problems you generate will be restricted to that area.
    - *Better tested* - Easier to design and run tests on orthogoanl components.
    - *Third-party Independence* - You will not be tightly tied to the particular vendo, product or platform. BEcause the interfaces to these third-party components will be isolated.

### **Design**

**Easy test for orthogonality** - Once you have your components mapped out, ask yourself: *If I dramatically change the requirements behind a particular function, how many modules are affected?*. In orthogoanl system, the answer should be 1.

### **Toolkits and Libraries**

*Choose your technologies wisely*. When you bring in a toolkit (or even library from other memebers of your team), ask yourself whether it imposes changes on your code that shouldn't be there.

### **Coding**

Techniques to maintain orthogonality.

- *Keep your code decoupled* - Write shy code.
- *Avoid global data* - Global data increase the risk of non orthogonality.
- *Avoid similar functions*

## **Reversibility**

**The problem is that ciritical decisions aren't reversible.**

The critical decisions are like being written in the sand at the beach, a big wave can come and wipe them out at any time.

> **There are no final decisions**

- Hide third party API's behind your own abstraction layer.
- Break your code into components even if you plan to deploy on a single server

## **TRACER BULLETS**

> *Tracer bullets are loaded at intervals alongside regular ammunaition. When they're fired, their phosphoris ignites and leaves a pytotechnic trail from the gun to whatever they hit. If the tracers are hitting the target, then so are the regular bullets. Soldiers use these tracer rounds to refine their aim: it's pragmatic, real time feedback under actual conditions.*

### **Code that glows in the dark**

> **Use Tracer Bullets to Find the Target**

