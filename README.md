# Windy City Code Splitting

Repository for my talk at Windy City DevCon on 1/12/18

## Resources

- [Link to the presentation](https://github.com/code-for-coffee/webpack-boilerplate)
- [Source Code Repository](https://github.com/code-for-coffee/webpack-boilerplate)

---

# Slides (same as in the presentation link above)

### Using Webpack to Dynamically Load Code as Needed

#### James Traver, Sr. Front-End Developer @ Gogo

- Github: code-for-coffee
- Twitter: code4coffee


---

# Hi there

Thanks for taking your morning to learn about some of the finer points of optimizing your front end application. I'm sure your boss isn't asking you to do this already.

---

#### I'm not your typical speaker; I will ask you to turn and talk to the person next to you to brainstorm ideas. I will also ask for responses because nothing is better than a real life example.


---

# Objectives

- Understand why splitting up your front end code is valuable.
- Discuss lazy loading and how it is valuable to front end developers
- Take a look at a real-life example
 and take a look at code-splitting
- Build out a Webpack config to see how this works
- Wrap-up

---

## Ugh, Webpack?

These concepts can be applied in other ways as well. Rollup and Parcel also offer similar capabilities.

Native support is still in the works (I'm looking at you, harmony imports for Node).

---

# Let's Get Started!

---

## Why is code splitting valuable?

---

### Code splitting is valuable because it allows front-end developers to split apart their client side code into smaller "chunks". 

---

### These chunks can be organized: many companies have a vendor chunk and internal code chunks.

---

### However, this is a luxury for those of us that are working with modern ECMAScript codebases.

--- 

### Essentially, we should be able to `import` files using the `import` statement.

> https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import

---

### While support for this syntax has not hit mainline adoption (who is waiting to use 'import' in Node?)

---

### However, the Javascript bundler ecosystem has adopted this standard.

--- 

### Sure, we can `import` things here and there but imagine being able to grab client side code only when it is needed.

---

### Wouldn't this be useful?

--- 

## Activity

Turn and talk to the person next to you. Visit a  website together that you can analyze. Consider how you would split apart the client side code on this site into smaller pieces.

Does anything seem to load later than the initial load?

---


# Lazy Loading

---

## What is Lazy Loading?

Some of you may know this already! However, I want to make sure everyone is caught up.


---

_Lazy loading is a design pattern commonly used in computer programming to defer initialization of an object until the point at which it is needed. It can contribute to efficiency in the program's operation if properly and appropriately used. The opposite of lazy loading is eager loading._ - Wikipedia

> https://en.wikipedia.org/wiki/Lazy_loading

--- 

## Applying to web development

Lazy loading is a great way to split up your application. In fact, you might already be splittig it up already. 

---

## Raise your hand if...

---

### You split your code up into sections or components.


---

### You treat each website as a composable document (vs a flat document to)

---

#### You follow design patterns to keep helpers in one place, components in another, ...

---

## If you aren't already splitting your code up, now is a great time to!

--- 

### What if we could take it further, though? What if we could load code only when we actually need it?

---

## Great news: We can use Webpack to import code as we need to! Let's see what this will look like

---

# Code Example

Let's look at dynamic importing:

```js
System.import('./components/LazyLoadingComponent').then(
  (LazyLoadingComponent) => {
      console.log(LazyLoadingComponent);
      let lazyComponent = new LazyLoadingComponent('.lazy');
      lazyComponent.render();
}).catch((error) => {
  console.log(error);
});
```

---

# Application Context

```js
window.onload = (event) => {

    console.log('Loading LazyLoadingComponent');

    System.import('./components/LazyLoadingComponent').then(
    (LazyLoadingComponent) => {
      console.log(LazyLoadingComponent);
      let lazyComponent = new LazyLoadingComponent('.lazy');
      lazyComponent.render();
    }).catch((error) => {
      console.log(error);
    });
  });

};
```

---

### Neat, huh? You can also use *async* functions to do the same thing.

---

# An Example

---

### I'm going to take a few moments to show you a real-life example of this in the web browser. 

### http://ga-chicago.github.io/webpack/index.html

---

# Let's take a look at what we saw

---

#### At this time, we're going to take a peak at a simple Webpack project 

---

# Questions?

Please write your questions down! I'll be happy to answer them when we have some free time near the end.

---

# In Conclusion

---

# Wrap Up

Thank you again for spending your morning with me to learn about code splitting. 

---

<img src='https://firebasestorage.googleapis.com/v0/b/chicago-devfest.appspot.com/o/2017%2Fspeakers%2F-L0kZW4dFRlnY5p1oiv2?alt=media&token=7528f147-be7d-4ec4-86fb-a317663e42c5' height='50%' />

- Github: code-for-coffee
- Twitter: code4coffee

---

## Resources

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import
- https://webpack.js.org/guides/code-splitting/
- https://medium.com/@rajaraodv/webpack-the-confusing-parts-58712f8fcad9
- https://dev.to/kayis/dynamic-imports-with-webpack-2
