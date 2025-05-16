# **4️⃣ Chatper 4 - Pragmatic Paranoia**

> **👉 You Can't Write Perfect Software.**

Accept it As an axiom of life. Embrace it. Celebrate it.

Programmers 👯 generally, stay defensive from the other people's mistakes, and validate everything and do everything they can to check everything and perform operations, and generally feel pretty good 😊 about themselves.

But Pragmatic programmers 🧑‍🦰 take a step further. They don't trust themselves, either. Knowing that no one writes perfect code,including themselves, pragmatic programmers build in defenses 🧱 against their own mistakes.

## **📝 Design By Contract**

> Nothing astonishes men so much as common sense and plain dealing. - *Ralph Waldo Emerson, Essays*

### **DBC**

Design by Contract is a way to write programs where each part of the code has a contract — like a deal or an agreement. 🎯

It includes:

- ✅ Preconditions – what must be true before something runs
- ✅ Postconditions – what must be true after it runs
- 🔐 Invariants – rules that must always be true

**💡 Real-Life Example:** Imagine you’re using an ATM 💳

- ☑️ Precondition - You must insert your card and enter the correct PIN.
- ☑️ Postcondition - After withdrawing, your money should be less by the withdrawn amount
- ☑️ Invariant - Your account should never have negative balance

The ATM (your program) follows these rules/contracts to behave properly.

> **👉 Design With Contracts**

### **Implementing DBC**

Simply enumerating what the input doman range is, what the boundary conditions are, and what the routine rpmises to deliver - or, more importantly, what it doesn't promise to deliver - before you write the code is a huge leap forward in writing better stftware.

DBC is, after all, a design technique. Even without automated checking, you can put the contract in the code as comments or in the unit tests and still get a very real benefit.

**🅰️ Assertions**

Languages like Eiffel support DbC natively. But in most languages like Python, Java, or C#, you can manually write checks (assertions) to implement contracts. 

### **💥 DBC and Crashing Early**

Crashing early means the program stops immediately when something is wrong, instead of continuing with bad data.

This is actually smart! 🤓

**🧠 Why?**
If something is broken, crashing early:

- ❗ Stops further damage
- 🐞 Makes bugs easier to find
- 🔧 Helps you fix the problem faster

📌 Example:
```python
if user_age < 0:
    raise ValueError("❌ Age can't be negative")
```
It's better to crash now, than let negative age go deep into your system and cause weird bugs later.

### **✅ Semantic Invariants**

A semantic invariant is a rule that defines what must always be true for your program or data to stay correct.

🔁 Why Are Semantic Invariants Important?

    - Prevent bugs 🐞
    - Make code easier to understand ✅
    - Ensure your program is always in a valid state ⛑️

🧠 Easy Analogy: In a Bank Account System:

**Invariant** : “The account balance should never go below 0.”

This rule must always be true. If a withdrawal tries to break that rule, the program should stop it.