# 1.📘 Difference Between any, unknown, and never in TypeScript (In Simple Words)

When we learn TypeScript, some types like any, unknown, and never can feel confusing. But actually, they are not so hard. In this blog, I will try to explain them in very simple language, with examples.

### any – use anything, do anything

If you use any type, TypeScript will not check anything. You can put any value in it, and you can do anything with that value.

let value: any = "Hello";
value = 123;
value = true;
value.doSomething();
So, any is like telling TypeScript: “I know what I’m doing. Don’t check me.”

### When to use:

If you are not sure what type will come, or you are just starting and want to write code without errors.

### unknown – safe version of any

unknown is similar to any, but a bit safer. You can store anything in it, but you can’t use it until you check the type.

let data: unknown = "Hello";

if (typeof data === "string") {
console.log(data.toUpperCase());
}
If you don’t check the type, TypeScript will give an error. So it forces you to be careful.

### When to use:

When you don’t know what type will come, but you want TypeScript to still help you write safe code.

### never – means nothing will happen

never means something that will never happen. It is used when a function doesn’t return anything (like it always throws an error) or when something should be impossible.

Example 1 – function that throws error:

function throwError(message: string): never {
throw new Error(message);
}
Example 2 – checking all cases:

type Shape = "circle" | "square";

function draw(shape: Shape) {
if (shape === "circle") {
console.log("Drawing circle");
} else if (shape === "square") {
console.log("Drawing square");
} else {
const check: never = shape;
}
}
####When to use:
When you want to make sure all possible options are handled, or if something will never return.

Summary in One Line
any: Do whatever you want. TypeScript will not check. (Dangerous but easy)

unknown: Accept anything, but check before using. (Safe)

never: This thing will never happen or never return. (Used in special cases)

I hope now you can understand the difference between these three types. I tried to keep this blog easy and friendly for beginners like me.

# 2. Understanding Union and Intersection Types in TypeScript with Examples

When working with TypeScript, you may come across the terms union and intersection types. At first, they might seem confusing, but once you understand them, they become very useful. This blog post will explain both types with simple examples so you can use them confidently in your projects.

#### What is a Union Type?

A union type allows a variable to hold one value from multiple possible types. It gives you flexibility when a value can be of different types.

Example:

function printId(id: string | number) {
console.log("Your ID is: " + id);
}

printId("abc123");
printId(101);  
In this example, the id parameter can be either a string or a number. This is helpful when a function or variable can accept different types of input.

What is an Intersection Type?
An intersection type combines multiple types into one. That means the final type must include all properties from the combined types.

Example:

type Person = {
name: string;
};

type Employee = {
employeeId: number;
};

type FullEmployee = Person & Employee;

const emp: FullEmployee = {
name: "Khalid",
employeeId: 123
};
Here, FullEmployee includes all properties from both Person and Employee. So, any object of this type must have both name and employeeId.

Key Differences Between Union and Intersection Types
The main difference is in how they handle types. A union type means a value can be one of several types — for example, a string or a number. It's more flexible and often used when you're not sure which exact type you'll get. On the other hand, an intersection type means a value must have all the properties from multiple types. It's stricter and useful when you're combining different objects or interfaces into one.

Why It Matters
Union and intersection types help make your code more precise and easier to manage. They give you control over how data flows in your application and help catch errors at compile time.

Conclusion
If you’re learning TypeScript, understanding union and intersection types is a key step. They're simple concepts once you see them in action, and they can greatly improve the quality of your code. Hopefully, this post gave you a clear idea of how and when to use them.
