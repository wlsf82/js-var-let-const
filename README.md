# JavaScript - `var`, `let`, and `const`

> This text was produced by [ChatGPT](https://chat.openai.com/) with co-authorship by [Walmyr Lima e Silva Filho](https://walmyr.dev).

___

> **Walmyr:** Write a content that explains the differences between `var`, `let`, and `const`.
> Do not forget to mention that `let` and `const` were introduced in ES6, the sixth version of JavaScript, also know as ES2015.

> **ChatGPT:** Here are the differences between the three ways to declare variables in JavaScript: `var`, `let` and `const`.
> `var` is the oldest way to declare a variable in JavaScript, and it has function scope, meaning the variable can be accessed within the function it is declared in, as well as in any nested functions. However, it does not have block scope, meaning that if a var variable is declared within an `if` statement or a `for` loop, it will still be accessible outside of the block. This can lead to unexpected behavior and is one of the reasons why `var` is considered less secure than `let` and `const`.
>
> `let` and `const` were introduced in ES6, also known as ES2015, and they both have block scope. This means that a variable declared with `let` or `const` can only be accessed within the block it is declared in and will not be accessible outside of that block. This is a more secure way to declare variables, as it helps prevent unexpected behavior and makes your code more predictable.
>
> The difference between `let` and `const` lies in their mutability, or the ability to change their value. let variables are mutable, meaning you can reassign a new value to them later in your code. `const` variables, on the other hand, are "immutable", meaning their value cannot be changed once it is assigned.
>
> In conclusion, when declaring variables in JavaScript, it is generally recommended to use `const` whenever possible, as it provides the most secure and predictable behavior. If you need to declare a variable that will change its value later in your code, you can use `let`. However, it's worth noting that `var` should be avoided in most cases, as its lack of block scope can lead to unexpected behavior.

> **Walmyr:** Continue explaining that although `const` variables help with immutability, values can still be changed in structured types, such as arrays and objects, even if they are declared as `const`. Despite the variable cannot be reassigned, we can still add, remove or change the values inside of these "more complex" objects.

> **ChatGPT:** Yes, that's a great point to clarify. While `const` variables are indeed immutable in that their reference cannot be changed, the values of structured types such as arrays and objects can still be changed, even if the variable was declared with `const`.
>
> For example, if you have a `const` variable `array` that holds an array of numbers, you cannot reassign a completely new array to `array`, but you can still add, remove, or change values within the array. For example:

```js
const array = [1, 2, 3];
array.push(4);
console.log(array); // Output: [1, 2, 3, 4]

```

> Similarly, if you have a `const` variable `object` that holds an object, you cannot reassign a completely new object to `object`, but you can still add, remove, or change properties within the object. For example:

```js
const object = {name: 'John', age: 30};
object.age = 31;
console.log(object); // Output: {name: 'John', age: 31}

```

> So, while `const` provides a way to ensure that a reference cannot be changed, it does not provide complete immutability for structured types such as arrays and objects. It's important to keep this in mind when using `const` and to consider alternative techniques for achieving immutability, such as using `Object.freeze` or other libraries, if necessary.

> **Walmyr:** Give an example of `Object.freeze`.

> **ChatGPT:** Certainly! `Object.freeze` is a method provided by JavaScript that allows you to freeze an object, making it completely immutable. This means that you cannot add, remove, or change any properties of the object once it has been frozen. Here's an example:

```js
const object = {name: 'John', age: 30};
Object.freeze(object);
object.age = 31;
console.log(object); // Output: {name: 'John', age: 30}

```

> In this example, we create an object `object` with properties `name` and `age`. Then, we use `Object.freeze` to freeze the object, making it completely immutable. Finally, we attempt to change the `age` property to `31`, but the change has no effect and the output of the object remains the same.
>
> It's worth noting that `Object.freeze` only works for the first level of the object, so if you have nested objects within the object you want to freeze, those nested objects will still be mutable. However, you can recursively freeze nested objects using a utility function or a library.
>
> Overall, `Object.freeze` provides a simple way to ensure that an object remains completely immutable and can be useful in situations where you need to prevent changes to an object.

> **Walmyr:** I've a quick question about the above code example. Does `object.age = 31;` throws any error or not, since the object has been frozen?

> **ChatGPT:** No, the code `object.age = 31;` does not throw an error, even though the object has been frozen using `Object.freeze`. Instead, the assignment simply has no effect and the property age of the frozen object remains unchanged.
>
> In other words, `Object.freeze` does not throw an error when you try to modify a frozen object, but it simply prevents any modifications from taking effect. This can be useful in some cases, as it allows you to prevent changes to an object while still allowing your code to run without errors.
>
> It's also worth noting again that `Object.freeze` is a shallow freeze, which means that it only freezes the first level of properties of the object. If you have nested objects within the frozen object, those nested objects will still be mutable and can be modified. To freeze nested objects, you can use a utility function or a library that implements a deep freeze.
