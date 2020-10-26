# classes and instances

## Recap: 

* A class is written with keyword `class`. 
    * **tipp:** by convention: class names start with an upper case letter
* A class usually has a method `constructor()` to initialize it's starting state.
* A class can have methods, that can use the inner state properties with the `this` keyword (that is a reference to the instance, after it was created).

    Example (definition):
    ```javascript
    class MyClass {
        constructor(initProperty1, initProperty2) {
            this.propertyOne = initProperty1;
            this.propertyTwo = initProperty2;
        }

        aMethod() {
            console.log("Prop1: ",this.propertyOne);
            console.log("Prop2: ",this.propertyTwo);
        }
    }
    ```
* To create an instance of a class, use the `new` keyword and the name of a class with round brackets ().
    * This calls the method `constructor()` and expects you to pass arguments to give the starting state of your instance object.
* By default you can read and write property values with the name of the instance followed by a dot (.) and the property name.
* To call a method of your class, use the instance name followed by a dot (.) and the method's name and round bracket () that containt the arguments passed to the method (if any).

    Example (use):

    ```javascript
    let myInstance = new MyClass("first property content",100);
    myInstance.propertyOne = "1st property content";
    myInstance.aMethod();
    /* expected output:
    Prop1: 1st property content
    Prop2: 100
    */
    ```
* You can test, if an object was created from a template class with the operator `instanceof`.

    Example:
    ```javascript
    let anInstance = new MyClass("first","second");
    let noInstance = {propertyOne: "foo", propertyTwo: "bar"};
    console.log(realInstance instanceof MyClass);
    // -> true
    console.log(noInstance instanceof MyClass); 
    // -> false
    ```

---
## (1) A product

### (1.1) Definition
Write a JavaScript class `Product`, as a template of products of an online shop.

The class should have 2 properties:
* a `name` as a string
* a `price` as a number

The constructor should take 2 parameters initializing those properties.

The class should have 2 methods:
* `containedVAT()` - returning 16% of the products price as VAT (value-added tax)
* `toText()` - returning a string with the products name, price and the containedVAT. Like:
    ```
    Premium Coffee, 10.00€ (incl. 1.60€ VAT)
    ```

### (1.2) Use:
Create some instance objects from your template class with keyword `new`

Examples:
* Adidas running shoes for 120,50 € 
    ```javascript
    let shoes = new Product("Adidas running shoes", 120.50);
    ```
* A painting set for 15.99 €
* A barber set for 30.20 €
* A pack of 5 socks for 8.99 €

Print the product descriptions to the console by calling the `.toText()` method of your instances.

---
## (2) A shopping cart

### (2.1) Definition

Write another class `Cart`, as a template of the shopping cart of an online shop.

The class should contain a property:
* `products`, as an array of products.

On creation of an instance of Cart, there will be no products, so the array is empty, and your constructor will have no parameters.

Create two methods for the shopping cart class:
* `addProduct(aProduct)` that takes one parameter.
    * The method should test, if aProduct is an instance of the `Product` class
    * only if aProduct is an instance of Product add it to the array of products.
* `listProducts()`, that takes no parameters.
    * the method should iterate over the array of products
    * for every product contained in the list, call the `toText()` method and print it to the console.
    * **Bonus**: instead of using a for loop over the array, consider the use of array.forEach(); 

### (2.2) Use
Create an instance of your shopping cart with the `new` keyword.
```javascript
let cart = new Cart();
```

Add the product instances, that you created in exercise (1.2) to your shopping cart.

Example:
```javascript
cart.addProduct(shoes);
```
Call the `.listProducts()` method, to print your shopping cart's content.