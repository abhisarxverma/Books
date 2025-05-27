# 📖 **Chapter 5 — Bend or Break**

## 🔄 **Decoupling**

To build **flexible, change-friendly software**, you must ensure individual components are **loosely coupled** — meaning they should depend on as few other components as possible.

### 🚨 Symptoms of Tight Coupling

* 🔁 Strange dependencies between unrelated modules or libraries
* 🧩 "Simple" changes that unexpectedly break other parts of the system
* 😰 Developers afraid to touch the code — unsure what might break
* 🧑‍💼 Meetings with *everyone* because no one knows who a change might affect

---

## 🚂 **Train Wrecks**

Here's an example of code that knows *too much* 👇

```java
public void applyDiscount(customer, order_id, discount) {
    totals = customer
              .orders
              .find(order_id)
              .getTotals();
              
    totals.getTotal = totals.grandTotal - discount;
    totals.discount = discount;
}
```

### 😬 What's wrong here?

* We're digging into the internals of the `customer` object
* Then searching for the order manually
* Then accessing and modifying the totals directly

📛 This **violates encapsulation** and makes it hard to change the code in the future without breaking things.

---

## 🗣️ **Tell, Don't Ask**

> “Don’t ask an object about its state and then make decisions. Instead, *tell* it what to do.”

When you inspect and act on another object's data, you scatter knowledge of that object’s internal design throughout your codebase 😵‍💫

---

## ✅ Step-by-step Fix

### 🛠️ **Fix #1**

```java
public void applyDiscount(customer, order_id, discount) {
    customer
        .orders
        .findOrder(order_id)
        .getTotals()
        .applyDiscount(discount);
}
```

Better — but we're still asking the customer for its `orders` and doing a manual search. Let's go further. 🔍

---

### 🛠️ **Fix #2**

```java
public void applyDiscount(customer, order_id, discount) {
    customer
        .findOrder(order_id)
        .getTotals()
        .applyDiscount(discount);
}
```

We're improving! But we're still accessing the `totals` object — again, too much internal knowledge.

---

### 🛠️ **Final Fix (Cleanest)**

```java
public void applyDiscount(customer, order_id, discount) {
    customer
        .findOrder(order_id)
        .applyDiscount(discount);
}
```

🎉 Now the logic is clean and respects encapsulation. We're telling each object **what to do**, not **how** to do it.

---

## 🧠 Final Thought

Every application has core concepts — in this case, **customers** and **orders**. These are *first-class citizens* in your design. It’s okay (even expected!) to **expose meaningful APIs** for them.

👉 Hide internal details, but don't bury real concepts.
Design software that can **bend without breaking**. 💡

---

## **😈 The Evils of Globalization**

Globally accessible data is insidious source of coupling between application componenets.

> 👉 **Avoid Global Data**

> 👉 **If it's Imporatant Enought to Be Gloabl, Wrap it in  an API**

### **Again it's All About Change**

Coupled code is hard to change, alterations in one place ca have secondary effects elsewhere in the code, and often in hard-to-find places.

Keeping your code shy, having it only deal with things it directly knows about, will help keep your applications decoupled, and that will make them more amenable to change.

## **Juggling the Real World**

This section is all about writing responsive applications.

### **Events**

Availability of Information, maybe from outside world, maybe from inside world like search finishes,  or fetching the next element in the list.

Writing applications that respond to events, and adjust what they do based on those events, those applications will work better in the real world.

**Four Strateties to write interactive applications without coupling -**

### **Finite State Machines**

### 🚦 What is a Finite State Machine (FSM)?

A **Finite State Machine** is a computational model made up of:

* **States** – distinct conditions or modes (e.g., *idle*, *running*, *paused*)
* **Transitions** – changes between states triggered by events or conditions
* **Events/Inputs** – things that cause transitions (e.g., button press, timeout)
* **Actions** – operations performed during transitions or when entering/exiting a state

FSMs are great for systems where the behavior depends on **current status** and **incoming events**.

---

### 🧭 Why Use FSMs?

> "Complex behavior emerges from simple rules."

FSMs help developers:

* **Model real-world scenarios** in a clear, structured way
* Avoid messy if-else or switch-case logic 🧩
* Make the code **predictable**, **testable**, and **maintainable** 🧼

FSMs are commonly used in:

* UI workflows
* Game states
* Protocol handling
* Embedded systems

---

### 📊 Representing FSMs: Tables & Diagrams

#### ✅ **State Transition Table**

| Current State | Event         | Next State | Action       |
| ------------- | ------------- | ---------- | ------------ |
| Idle          | Start Button  | Running    | Start Timer  |
| Running       | Pause Button  | Paused     | Stop Timer   |
| Paused        | Resume Button | Running    | Resume Timer |
| Running       | Stop Button   | Idle       | Reset Timer  |

* This tabular format makes behavior **explicit** and easy to update.

#### 🔄 **State Transition Diagram**

A visual **flowchart** can help map out FSMs:

```
 [Idle]
   ↓ Start
[Running] ←──── Resume ──── [Paused]
   ↓ Stop                 ↑
 [Idle]              Pause
```

* Diagrams are excellent for **communication** between developers and stakeholders 🧑‍💻🧑‍🎨

---

### 🎯 Pragmatic Advice from the Authors:

* **Model with FSMs first** — it helps clarify the problem before jumping into code.
* Think in **transitions**, not just states.
* Use tools like state tables or diagrams to visualize logic early on.

---

### ✨ Final Takeaway

> "Finite State Machines bring order to behavioral chaos."

FSMs let you **think clearly** about stateful systems, **avoid bugs**, and **document behavior** naturally. They're a simple but powerful mental model for building smarter, more reliable software systems. 🔧⚙️

---
