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

### 🔍 The Observer Pattern

The Observer Pattern is a behavioral design pattern that establishes a one-to-many relationship between objects. When the Subject (Observable) 🧐 changes, it notifies its Observers (Subscribers) 👀 automatically!

**💡 Think of it like a YouTube channel:**

The Channel (Observable) posts a new video.

Subscribers (Observers) instantly get notified! 🔔

**⚙️ How Does it Work?**

***1️⃣ Observable 🏛️***

This is the main object being watched.

It maintains a list of subscribers and alerts them when changes happen.

***2️⃣ Observers 👀***

These are dependent objects that want updates when something changes.

They subscribe to the Observable to receive notifications.

***3️⃣ Notification Mechanism 🔔***

When the Observable changes, it loops through its subscribers and sends updates.

### 📢 Publish/Subscribe Pattern

The **Pub/Sub** Pattern is a messaging system where publishers send messages 📤, but they don’t know who receives them! Instead, subscribers listen for messages 📥 based on topics they care about.

**💡 Think of it like a radio station:**

The Radio Station (Publisher) 🎙️ broadcasts music.

Listeners (Subscribers) 📻 tune in to their favorite channels.

The station doesn’t need to know who is listening, and listeners don’t need to know who is broadcasting!

**⚙️ How Does Pub/Sub Work?**

***1️⃣ Publisher 📢***

Sends messages to a central system (message broker).

Doesn’t care who receives the message.

***2️⃣ Subscriber 👂***

Registers interest in specific topics.

Gets notified only when relevant messages arrive.

***3️⃣ Message Broker 🔄***

Acts as a middleman between publishers and subscribers.

Ensures messages reach the right audience.

## **🔄 Reactive Programming, Streams And Events**

> Instead of storing just the current state, you store the **changes in state over time**.

* Traditional programming:

  > "Give me the value of X."
* Reactive thinking:

  > "Tell me **whenever X changes**."

The **real world doesn’t work in static snapshots** — it works in **continuous flows**:

* Button clicks
* Sensor readings
* Stock prices
* Keypresses

This is why **reactive programming** is a better model: it lets you **subscribe to the flow of time-based events** (streams), instead of constantly checking for change.

---

### 🔄 Mindset Shift They Emphasize:

| Old Way (Pull)                     | New Way (Push / React)             |
| ---------------------------------- | ---------------------------------- |
| "Check every second for an update" | "Get notified **when** it updates" |
| "Poll the server"                  | "Subscribe to a data stream"       |
| "Call function when needed"        | "Function **reacts to events**"    |

---

### 🧩 Why It Matters:

* Your programs become more **flexible** and **composable**.
* You stop fighting time and state.
* You write cleaner code that matches **how real-world systems behave**.

---

### 💬 Key Quote-like Insight from the Authors:

> “You don’t ask what time it is every second.
> You just wear a watch, and **it tells you when you need to know**.”

---

Sure bro — here’s the summary of **“Transforming Programming”** from *The Pragmatic Programmer* 💡, formatted in clean **Markdown**:

---

## **🌱 Transforming Programming**

## 🔧 Key Practices & To-Do’s

### 1. 🌀 Think in Terms of Transformations

* Code = **data transformers**.
* Your program takes input ➡️ processes it ➡️ outputs something meaningful.
* Helps simplify logic and visualize flow.

---

### 2. 🧱 Build Pipelines (Composable Functions)

* Split work into small, clear **steps**.
* Use **function chaining**, **pipes**, or **middleware-style flows**.
* Example: `input → parse → validate → transform → output`

---

### 3. 🔓 Reduce Coupling, Increase Modularity

* Avoid tightly linked components.
* Each piece should **do one thing well** and be swappable.
* Makes testing, debugging, and upgrades smoother.

---

### 4. 📣 Embrace Event-Driven Architectures

* Use **publish/subscribe**, **signals**, or **event buses**.
* Better than direct calls for loosely-coupled reactions.
* Helps scale across modules or services.

---

### 5. ⚙️ Externalize Configurations

* Keep settings/data **outside** code (e.g., `.env`, JSON, YAML).
* Lets non-devs tweak behavior.
* Makes your code environment-agnostic.

---
## **🧬 Inheritance Tax: Why Inheritance Can Be Problematic**

### **🔗 Inheritance Introduces Tight Coupling**

- **Strong Coupling Across Hierarchies**: When a subclass inherits from a parent class, it becomes tightly coupled not only to that parent but also to all ancestor classes. This means changes in any ancestor can have unintended ripple effects on the subclass.

- **Unintended Dependencies**: Subclasses may inherit methods and properties they don't need, leading to unnecessary dependencies and potential confusion.

- **Fragile Base Class Problem**: Modifications in a base class can inadvertently break functionality in subclasses, making maintenance and updates risky.

**🚫 The Banana-Gorilla-Jungle Analogy**

```You wanted a banana but what you got was a gorilla holding the banana and the entire jungle.```

## Alternatives to Inheritance

### 1. **✅ Interfaces** (via Abstract Base Classes)

### 📘 What It Means:

* Define a **contract** of what methods a class must implement.
* Prevents tightly-coupled inheritance.
* Implemented via `abc` module in Python.

### 🧪 Example:

```python
from abc import ABC, abstractmethod

class Notifier(ABC):  # Interface
    @abstractmethod
    def notify(self, message: str) -> None:
        pass

class EmailNotifier(Notifier):
    def notify(self, message: str) -> None:
        print(f"📧 Email sent: {message}")

class SMSNotifier(Notifier):
    def notify(self, message: str) -> None:
        print(f"📱 SMS sent: {message}")

def alert_user(notifier: Notifier):
    notifier.notify("Server is down!")

alert_user(EmailNotifier())  # works
```

### 🧠 Why?

* Clear separation of concerns.
* Any class *can* implement this behavior, no rigid inheritance chain.

---

### 2. **🔄 Delegation / Composition**

### 📘 What It Means:

* Rather than extending a class, you create an **instance** of another class inside your own.
* Delegate work to it.

### 🧪 Example:

```python
class Logger:
    def log(self, msg: str):
        print(f"[LOG]: {msg}")

class FileUploader:
    def __init__(self, logger: Logger):
        self.logger = logger

    def upload(self, filename: str):
        self.logger.log(f"Uploading {filename}...")
        print("Upload complete!")

uploader = FileUploader(Logger())
uploader.upload("cat_photo.jpg")
```

### 🧠 Why?

* Swap any part (e.g., `Logger`) without affecting other logic.
* More flexible than inheritance.

---

### 3. **🧬 Mixins**

### 📘 What It Means:

* A mixin is a **class with reusable methods** but not intended to stand alone.
* Use multiple inheritance to “mix in” behavior.

### 🧪 Example:

```python
class JsonMixin:
    def to_json(self):
        import json
        return json.dumps(self.__dict__)

class LoggerMixin:
    def log(self, msg):
        print(f"[Mixin Log]: {msg}")

class User(JsonMixin, LoggerMixin):
    def __init__(self, username):
        self.username = username

u = User("akira")
u.log("Welcome!")  # from LoggerMixin
print(u.to_json())  # from JsonMixin
```

### 🧠 Why?

* Easily reuse logic in unrelated classes.
* Combine multiple behaviors with zero hierarchy constraints.

---

## 🔚 Summary Table

| Pattern    | In Python                     | Key Module | Use When…                           |
| ---------- | ----------------------------- | ---------- | ----------------------------------- |
| Interfaces | `abc.ABC` + `@abstractmethod` | `abc`      | You want a contract, not code       |
| Delegation | Class composition             | —          | You want flexibility + swappability |
| Mixins     | Multiple inheritance          | —          | You want to add features cleanly    |

---

<div style="display: flex; justify-content: center">
    <h1 style="font-family: "monospace">CHAPTER OVER</h1>
</div>