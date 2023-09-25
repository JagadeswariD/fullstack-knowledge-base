## Classes:

Class is a blue print to build objects

#### It allows you declare the properties

class Student {
firstname : string;
lastname: string;
age: number;
courses: string[];

constructor(
firstName: string,
lastName: string,
age: number,
courses: string[]
) {
this.firstname = firstName;
this.lastname = lastName;
this.age = age;
this.courses = courses;
}

enroll(course: string) {
this.courses.push(course);
}

listCourse() {
return this.courses.slice();
}
}
const student = new Student("Max", "Jack", 40, ["Anguar"]);
student.enroll("React");
console.log(student.listCourse());

#### Allows to specify public or private modifiers. By default they are public.

firstname: string;
lastname: string;
age: number;
private courses: string[];

#### You can simply redeclare the constructor like below

class Student {
constructor(
public firstName: string,
public lastName: string,
public age: number,
private courses: string[]
) {}

enroll(course: string) {
this.courses.push(course);
}

listCourse() {
return this.courses.slice();
}
}
