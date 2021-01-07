There are different ways for working with OOP in javascript:
1.Factory function.
2.Function constructor
3.Object.create()

Let’s think of a scenario whereby we want to create an object from data gotten from an input field, for example; we have a website and in our website a form field that requests for the names. We want to use the data gotten from the form field to create an object as a way to keep user data together and then create a profile for each user and make sure each user should have the same properties.

1.Factory Function:
const person1 = {
fname: “Roy”,
lname: “McBride”,
getFullName() {
return Full Name is: ${this.first_name} ${this.last_name};
}
};

const person2 = {
fname: “Joseph”,
lname: “Cooper”,
getFullName() {
return Full Name is: ${this.fname} ${this.lname};
}
};

const person3 = {
fname: “Ellen”,
lname: “Ripley”,
getFullName() {
return Full Name is: ${this.fname} ${this.lname};
}
};

console.log(person1.fname);// Roy
console.log(person2.lname);//Cooper
console.log(person3.getFullName());//Ellen Ripley

The code is repetitive and that is against the DRY(Don’t Repeat Yourself) principle of programming. We can make an Object constructor notation instead.

2.Object/Function constructor

function person(fname, lname){
this.fname = fname;
this.lname = lname;
this.getFullName= function{
console.log( Full Name is: ${this.fname} ${this.lname})}
}

const person1= new person(“Roy”, “McBride”);

It is DRY and clean with the constructor notation, and
values from the object can be accessed with the same syntax
// OBJECT LITERAL NOTATION
// To get the name of the first user.
console.log(person1.fname) // Roy

// OBJECT CONSTRUCTOR NOTATION(ES5)
// To get the name of the first user.
console.log(person1.fname) // Roy

In the following example Person is the constructor function and it has getFullName function in its prototype object, I have created two instance person1, person2 from Person constructor. We can see that the code is resuable by having a constructor and prototype.

const Person = function(fname,lname) {
this.fname = fname;
this.lname = lname;
}
Person.prototype.getFullName = function() {
return Full Name is: ${this.fname} ${this.lname};
}

const person1 = new Person(‘Roy’,‘McBride’);
const person2 = new Person(‘Joseph’,‘Cooper’);

3.Object.create():

The Object.create() method creates a new object, using an existing object as the prototype of the newly created object.

function Group1(fname, lname){
this.fname = fname;
this.lname = lname;

Group1.prototype.getFullName = function() {
return Full Name is: ${this.fname} ${this.lname};
}
}
const person2= new Group1(“Joseph”, “Cooper”)
console.log(person2.lname);
console.log(person2.getFullName());

function Group2(fname,lname, rank){
Group1.call(this,fname,lname);
this.rank=rank;
}
If we use the call() method, it only inherits the properties and not the prototypes. To inherit the prototypes, we will say:

Group2.prototype=Object.create(Group1.prototype);

const person3= new Group2(“Ellen”, “Ripley”,“Warrant Officer”);

console.log(person3.fname);
console.log(person3.lname);
console.log(person3.getFullName());
console.log(person3.rank);
