

## what is return value of function ?
Return values are just what they sound like — the values that a function returns when it completes.Some functions don't return a significant value, but others do.

## Strings in javascript and what are the methods appliable on strings ?
In JavaScript, strings are a data type used to represent sequences of characters. JavaScript provides a wide range of methods and properties that you can use to work with strings. Here's an overview of some common string methods in JavaScript:

1. **String Length:**
   - `length`: Returns the number of characters in a string.

   ```javascript
   const str = "Hello, World!";
   console.log(str.length); // Outputs: 13
   ```

   if string has whitespace , the length property counts whitespaces as 1 character.
   
        str = "Hello ";
        str.length -> 6

2. **String Access:**

   - You can access individual characters in a string using bracket notation.
   - strings are treated as sequences of characters, and they have a numeric index associated with each character
  
   ```javascript
   const str = "Hello";
   console.log(str[1]); // Outputs: "e"
   ```

3. **String Concatenation:**
   - `concat()`: Combines two or more strings and returns a new string.

   ```javascript
   const str1 = "Hello";
   const str2 = "World";
   const combined = str1.concat(", ", str2);
   console.log(combined); // Outputs: "Hello, World"
   ```

4. **Substring:**
   - `substring()`: Returns a part of the string between two indices.

syntax: 

        text_string.substring(start,?end);
        where end index is optional.

   ```javascript
   const str = "Hello, World!";
   const substr = str.substring(0, 5);
   console.log(substr); // Outputs: "Hello"
   ```

5. **String Search and Replace:**
   - `indexOf()`: Returns the index of the first occurrence of a specified substring. it returns index as index-1.
   - `lastIndexOf()`: Returns the index of the last occurrence of a specified substring.
   - `replace()`: Replaces a specified substring with another string.

   ```javascript
   const str = "Hello, World!";
   console.log(str.indexOf("World")); // Outputs: 7
   console.log(str.replace("World", "Universe")); // Outputs: "Hello, Universe!"
   ```

6. **String Case Modification:**
   - `toUpperCase()`: Converts the string to uppercase.
   - `toLowerCase()`: Converts the string to lowercase.

   ```javascript
   const str = "Hello, World!";
   console.log(str.toUpperCase()); // Outputs: "HELLO, WORLD!"
   ```

7. **Trimming Whitespace:**
   - `trim()`: Removes leading and trailing whitespace from a string.

   ```javascript
   const str = "   Hello, World!   ";
   console.log(str.trim()); // Outputs: "Hello, World!"
   ```

8. **String Splitting:**
   - `split()`: Splits a string into an array of substrings based on a specified delimiter.

   ```javascript
   const str = "apple,banana,cherry";
   const fruits = str.split(",");
   console.log(fruits); // Outputs: ["apple", "banana", "cherry"]
   ```

9. **String Conversion:**
   - `toString()`: Converts various data types to a string.

   ```javascript
   const num = 42;
   const str = num.toString();
   console.log(str); // Outputs: "42"
   ```

These are just a few examples of the many methods available for working with strings in JavaScript. Strings are a fundamental part of JavaScript, and these methods can help you manipulate and manage text data effectively.

 10. **String replace**
We can replace the contents inside the string using .replace method.

      let str = "Welcome to the js";
      str.replace("js","javascript");
      output => 'Welcome to the javascript'

11. **ReplaceAll**
it is used to replace all characters in the string.
      let str = "Welcome to the js tutorial, js is dynamic language";
      str.replace("js","javascript");
      output => 'Welcome to the javascript,js is dynamic language';

      Whereas ReplaceAll
       str.replaceAll("js","javascript");
      output => Welcome to the javascript,javascript is dynamic language.


### what are js objects ?

An object is a complex data type that represents a collection of key-value pairs, where keys are strings (or symbols in modern JavaScript) and values can be of any data type.

**How Can we create objects in js** 
- Object literal 

      The simplest way to create an object is using object literal notation. You define an object with curly braces and specify its properties and values.

      const person = {
      name: "John",
      age: 30,
      };

- Contructor function 

      You can create objects using constructor functions. These functions act as blueprints for creating multiple instances of objects with the same properties and methods.

   1. Using object literals is fine when you only need to create one object, but if you have to create more than one, as in the previous section, they're seriously inadequate.

a) first way of making it reusable is creating a function. 
inside function - create a obj and initialize prperties and methods.

      function createPerson(name) {
      const obj = {};
      obj.name = name;
      obj.introduceSelf = function () {
         console.log(`Hi! I'm ${this.name}.`);
      };
      return obj;
      }

b) this works fine but is a bit long-winded: we have to create an empty object, initialize it, and return it. A better way is to use a constructor. A constructor is just a function called using the new keyword. When you call a constructor, it will:

      function Person(name) {
      this.name = name;
         this.introduceSelf = function () {
            console.log(`Hi! I'm ${this.name}.`);
         };
      }


      const salva = new Person("Salva");
      salva.name;

- Object.create()

       The Object.create() static method creates a new object, using an existing object as the prototype of the newly created object.

            const person = {
               isHuman: false,

               printIntroduction: function () {
                  console.log(`My name is ${this.name}. Am I human? ${this.isHuman}`);
                  },
               };

      const me = Object.create(person);

      me.name = 'Matthew'; // "name" is a property set on "me", but not on "person"
      me.isHuman = true; // Inherited properties can be overwritten

      me.printIntroduction();
      // Expected output: "My name is Matthew. Am I human? true"

   
   ### Object. create method returns a new object with the specified prototype object and properties.



## What are various Object methods ?

- ### Object.assign 


        let obj1 = {a:1,b:2};
        let obj2 = {c:3,a:4};

        syntax: 

        Object.assign(target_object,source_object);

        // here we want to copy all the properties or say we want to merge the properties of obj2 in obj1.

        Object.assign(obj1,obj2) // target obj is obj1 and source obj2 is source object 
        console.log(Object.assign(obj1,obj2));
        // . output => {a: 4, b: 2, c: 3}

        here we can see on merging or copying the object a value is updated to 4 this is because object.assign behaves like below

        {a:1,b:2} <- {c:3,a:4}  // the values flow from right to left so when merging or copying will start 
         1. first c value will be copied in object obj1
                {a:1,b:2,c:3} 
        2. a will be copied , but obj1 still has the obj1 already so a will be replaced with the new value from the obj2.a
                {a:4,b:2,c:3}

- ### Object.keys()
Object.keys is a static method available on Object , which returns the collection or array of keys of an object.


      const obj1= {
      name:'john',
      age:28,
      height:162
      }

      to get the array of keys we can do : 
      Object.entries(obj1) -> ["name","age","height"]

   - ### Object.values()

   - ### The Object.values() static method returns an array of a given object's own enumerable string-keyed property values.


         const object1 = {
            a: 'somestring',
            b: 42,
            c: false,
         };

         console.log(Object.values(object1));
         // Expected output: Array ["somestring", 42, false]

- ###  Object.entries()

#### an object is a collection of key and value pairs, Object.entries convert each key value pair as an array object where first element is key and second is value.

      const obj ={
         name : 'john',
         age:30
      }

      the first pair of key and value is 
       a) key : name 
          value : 'john'
       b) key : age
          value : 30 

      Object.entries will create a array of key and value pairs 

       like first pair will be 
       ["name","john"] 
       ["age",30]

       and will return as [["name","john"],["age",30]]

#### Each key-value pair is an array with two elements: the first element is the property key (which is always a string), and the second element is the property value.

- ### Object.hasOwnProperty()

#### The hasOwnProperty() method of Object instances returns a boolean indicating whether this object has the specified property as its own property (as opposed to inheriting 

         const object1 = {};
         object1.property1 = 42;

         console.log(object1.hasOwnProperty('property1'));
         // Expected output: true

         console.log(object1.hasOwnProperty('toString'));
         // Expected output: false

         console.log(object1.hasOwnProperty('hasOwnProperty'));
         // Expected output: false

### similar method is there which is static mehthod as Object.hasOwn(object,property)

- ## Object.groupBy()

### The Object.groupBy() static method groups the elements of a given iterable according to the string values returned by a provided callback function. The returned object has separate properties for each group, containing arrays with the elements in the group.

syntax

      Object.groupBy(items, callbackFn)






