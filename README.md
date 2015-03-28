# core-object
a Core object which can be extended

## What is this?

This is a generic object that can serve the basis of a larger script.

## Usage

    var router = new Core();

This would create a new object to help organize a larger library.

## Registering a new global

Methods or variables can be registered as globals by using the `registerGlobal` method. This will provide lightweight management to prevent a method from being overwritten.

    myObject.registerGlobal('sayHello', function () {
        console.log('Hello!');
    });

    myObject.sayHello();

    // Logs "Hello!" to the console

## Datastore

The core object provides a lightweight system for managing internal data using getters and setters.

    myObject.set('foo', 'bar');

    console.log(myObject.get('foo');

    // Logs "bar" to the console

## Before and After hooks

The core object will execute a sequence of before and after hooks (if registered) before and after calling a global method.

This allows a framework for other scripts to modify the parameters passed to a method, or modify the result.

This works by executing an array of functions sequentially.

For example:

We could add a before hook to generateUID which always set the separator to `+`

     myObject.before('generateUID', function(args) {
         if (args) args[0] = '+';
         return args;
     });

Then, when we called generateUID('-'), we would get a GUID separated by `+` instead.