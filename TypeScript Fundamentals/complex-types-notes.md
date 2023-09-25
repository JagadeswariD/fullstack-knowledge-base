## Complex types : array and object

let hobbies:string[];

hobbies=['Sports','Cooking',1] // it will throw an error, because it is expecting a string instead of number

default type to a variable is **any**, meaning u can assign a variable with value without specifying its type.
let person ={
name='Max';
age:32;
}
**Any** is a fallback type, which we should avoid using it as it defeats the purpose of typescript and make it behave like JavaScript.

Object type defination
let person:{
name:string;
age:number;
};

person = {
name='Max';
age=32;
}

To store an array of objet
let people:{
name : string;
age : number;
}[];
