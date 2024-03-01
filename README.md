# Javascript
polyfills in javascript interview questions

##This

The "this" keyword in JavaScript can be tricky for both new and experienced developers. This article aims to explain "this" fully so that you never have to worry about it again. We'll learn how to use "this" correctly in every situation, even the tricky ones where it's hard to understand.

Think of "this" like pronouns in languages like English and French. For example, instead of saying "John is running fast because John is trying to catch the train," we use the pronoun "he." Similarly, in JavaScript, "this" acts as a shortcut or a referent, pointing to an object or the subject in the code.

Here's an example:

```
var person = {
  firstName: "Neelesh",
  lastName: "Bizoara",
  fullName: function () {
    console.log(this.firstName + " " + this.lastName);
  }
}
```

Using "this" like in the example above helps to avoid ambiguity in the code. If we used person.firstName and person.lastName, it might cause confusion, especially if there's another global variable named "person." "This" makes our code clearer and less prone to errors.

Just like the pronoun "he" refers to a person in a sentence, the "this" keyword refers to an object in JavaScript. It not only points to the object but also holds its value. "This" is like a shortcut to refer back to the object in context. We'll delve deeper into this concept later in the article.

### JavaScript’s this Keyword Basics
First, it's important to understand that all functions in JavaScript have properties, similar to how objects have properties. When a function runs, it gets a special property called "this," which is like a variable holding the value of the object that triggers the function.

The "this" reference always points to (and holds the value of) a single object. It's commonly used inside a function or a method, though it can also be used outside a function in the global scope. However, in strict mode, "this" is undefined in global functions and in anonymous functions not attached to any object.

When we use "this" inside a function (let's call it function A), it holds the value of the object that calls function A. We use "this" to access methods and properties of the calling object, especially when we don't know the name of the calling object or if there's no specific name to refer to it. Essentially, "this" serves as a quick way to refer back to the calling object.

```
var person = {
    firstName   :"Neelesh",
    lastName    :"Bizoara",
    // Since the "this" keyword is used inside the showFullName method below, and the showFullName method is defined on the person object,
    // "this" will have the value of the person object because the person object will invoke showFullName ()
    showFullName:function () {
    console.log (this.firstName + " " + this.lastName);
    }

    }

    person.showFullName (); // Penelope Barrymore
```
And consider this basic jQuery example with of this:
```
 // A very common piece of jQuery code

    $ ("button").click (function (event) {
    // $(this) will have the value of the button ($("button")) object
// because the button object invokes the click () method
    console.log ($ (this).prop ("name"));
    });
```

Let me explain the previous jQuery example in simpler terms: 
 The use of `$(this)`, which is jQuery’s syntax for the `this` keyword in JavaScript, is used inside an anonymous function, and the anonymous function is executed in the button’s click () method. The reason `$(this)` is bound to the button object is because the jQuery library binds `$(this)` to the object that invokes the click method. Therefore, `$(this)` will have the value of the jQuery button `($(“button”))` object, even though `$(this)` is defined inside an anonymous function that cannot itself access the `"this"` variable on the outer function.

Note that the button is a DOM element on the HTML page, and it is also an object; in this case it is a jQuery object because we wrapped it in the jQuery $() function.

### The Biggest Gotcha with JavaScript “this” keyword
If you understand this one principle of JavaScript’s `this`, you will understand the “this” keyword with clarity: `this` is not assigned a value until an object invokes the function where `this` is defined. Let’s call the function where `this` is defined the “`this Function`.”

Even though it appears `this` refers to the object where it is defined, it is not until an object invokes the `this Function` that `this` is actually assigned a value. And the value it is assigned is based <strong>exclusively</strong> on the <strong>object</strong> that invokes the `this Function`. `this` has the value of the invoking object in most circumstances. However, there are a few scenarios where `this` does not have the value of the invoking object. I touch on those scenarios later.