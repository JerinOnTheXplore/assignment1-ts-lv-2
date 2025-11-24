1. What are some differences between interfaces and types in TypeScript?

Ans: TypeScript-এ interface এবং type—দুটোই object-এর structure নির্ধারণ করতে ব্যবহার করা হয়। তবে তাদের মধ্যে কিছু মূল পার্থক্য আছে:

পার্থক্যসমূহ:
(1) Extending

   a.  interface সহজে extend করা যায়।

   b.  type ও extend করা যায়, তবে তার syntax আলাদা এবং কিছু সীমাবদ্ধতা আছে।

   interface Person {
   name: string;
   }
   interface Student extends Person {
   roll: number;
   }

  type A = { name: string };
  type B = A & { roll: number };

(2) Declaration Merging

   a.  interface merge হতে পারে — একই নামের interface বার বার লিখলে তারা একত্রে merge হয়।

   b.  type merge হয় না — একই নামে দুইটি type তৈরি করলে error হবে।

   
   interface User {
   name: string;
   }
   interface User {
   age: number;
   }
   // Result: User → { name: string, age: number }

(3) Use Cases

   a.  Interface সাধারণত object shape বর্ণনার জন্য।

   b.  Type শুধুমাত্র object নয় — union, intersection, tuple ইত্যাদিতেও    ব্যবহার হয়।


2. What is the use of the keyof keyword in TypeScript? Provide an example.

Ans:  keyof কোনো object type-এর property নামগুলোকে একটি union টাইপে রূপান্তর করে।
  
উদাহরণ:
  interface Product {
  name: string;
  price: number;
  quantity: number;
  }

  type ProductKeys = keyof Product;
  // ProductKeys = "name" | "price" | "quantity"

keyof সাধারণত এমন ফাংশনে ব্যবহার হয় যেখানে object-এর key অনুযায়ী value access করতে হয়।
 
   function getValue<T>(obj: T, key: keyof T) {
   return obj[key];
   }

   const p = { name: "Pen", price: 10 };
   getValue(p, "name"); 

