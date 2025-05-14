# **4️⃣ Chatper 4 - Pragmatic Paranoia**

> **👉 You Can't Write Perfect Software.**

Accept it As an axiom of life. Embrace it. Celebrate it.

Programmers 👯 generally, stay defensive from the other people's mistakes, and validate everything and do everything they can to check everything and perform operations, and generally feel pretty good 😊 about themselves.

But Pragmatic programmers 🧑‍🦰 take a step further. They don't trust themselves, either. Knowing that no one writes perfect code,including themselves, pragmatic programmers build in defenses 🧱 against their own mistakes.

## **Design By Contract 📝**

> Nothing astonishes men so much as common sense and plain dealing. - *Ralph Waldo Emerson, Essays*

### **DBC**

Every function and method in a software sustem does something, Before it starts that something, the function may have expectations of the state of the world, and it may be able to make a statement about the state of the world when it concludes.

- *☑️ Preconditions* - The Routine's requirements
- *☑️ Postconditions* - The State of the world when the Routine is done.
- *☑️ Class Invariants* - A class ensures that this condition is always true from the perspective of a caller.

**The contract between a routine and any potential caller can thus be read as** - 
If all the routine's preconditions are met by the caller, the routine shall guarantee that all postconditions and invariants will be true when it completes.

