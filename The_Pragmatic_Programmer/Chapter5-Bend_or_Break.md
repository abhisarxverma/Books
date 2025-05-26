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

## **The Evils of Globalization**

Globally accessible data is insidious source of coupling between application componenets.

> 👉 **Avoid Global Data**

> 👉 **If it's Imporatant Enought to Be Gloabl, Wrap it in  an API**

### **Again it's All About Change**

Coupled code is hard to change, alterations in one place ca have secondary effects elsewhere in the code, and often in hard-to-find places.

Keeping your code shy, having it only deal with things it directly knows about, will help keep your applications decoupled, and that will make them more amenable to change.
