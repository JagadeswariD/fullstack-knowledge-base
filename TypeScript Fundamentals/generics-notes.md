## Generics:

Functions that are **typesafe** and flexible. They work with any type, but then once certain type is used for function execution then that type is locked in. Provides flexibility and type safety.

function insertAtBeginning<T>(array: T[], value: T) {
const newArray = [value, ...array];
return newArray;
}

let days = ["Monday", "Tuesday"];
console.log(insertAtBeginning(days, "Sunday"));

let nums = [4, 5, 6, 7];
console.log(insertAtBeginning(nums, 3));
