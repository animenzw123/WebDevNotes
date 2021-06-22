---
title: Why using redux in react?
date: "2020-12-28T20:23:32.169Z"
description: This is about the cons of using redux in a react app.
keyword: "React"
---

**Redux** itself is a standalone library that can be used with any UI layer or framework, including React, Angular, Vue, Ember, and vanilla JS. Although Redux and React are commonly used together, they are **independent** of each other.

To use **redux** inside a react app, you should use an official "UI binding library" called **react-redux**

You can start new apps with React Redux is by using the official Redux+JS template for Create React App:

```
npx create-react-app my-app --template redux
```

Or add it as a dependency for an existing react app:

```
# If you use npm:
npm install react-redux

# Or if you use Yarn:
yarn add react-redux
```


## Why using redux?

Redux allows you to manage your app’s **state** in a single place and keep changes in your app more predictable and traceable. It makes it easier to reason about changes occurring in your app. But all of these benefits come with tradeoffs and constraints. One might feel it adds up boilerplate code, making simple things a little overwhelming; but that depends upon the architecture decisions.

## State management

**State management** is essentially a way to facilitate communication and sharing of data across components. It creates a tangible data structure to represent the state of your app that you can read from and write to. That way, you can see otherwise invisible states while you’re working with them.

Most libraries, such as React, Angular, etc. are built with a way for components to internally manage their state without any need for an external library or tool. It does well for applications with few components, but as the application grows bigger, managing states shared across components becomes a chore.

In an app where data is shared among components, it might be confusing to actually know where a state should live. Ideally, the data in a component should live in just one component, so sharing data among sibling components becomes difficult.

For instance, in React, to share data among siblings, a state has to live in the parent component. A method for updating this state is provided by the parent component and passed as props to these sibling components.

