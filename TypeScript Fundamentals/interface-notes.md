## Interface

Object type definition

interface Human {
firstname : string;
lastname : string;
greet: () => void;
}

let esh: Human;

esh = {
firstname : "sathya",
lastname : "dhanagopal",
greet() {
console.log("hi");
},
};

class Instructor **implements** Human {
firstname : string;
lastname : string;
greet() {
console.log("hello");
}
}

let shuchaye = new Instructor();
shuchaye.greet();
