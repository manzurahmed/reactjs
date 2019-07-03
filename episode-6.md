# Episode 6

## 2. ES6 Modular system

এই সেশনে ES6 এর মডিউলার সিস্টেম কিভাবে কাজ করে সেটা শিখেছি। কোন ফাইলে একাধিক ফাংশন থাকলে **১টা ফাংশনকেই কেবল default ভাবে export করা যায়**। অন্য ফাংশনকে export করতে হলে কার্লি ব্রেসের মধ্যে এক্সপোর্ট করতে হবে। যেমনঃ 

```
export { add as default, subtract };
```

এখন, অন্য কোন জেএস ফাইল থেকে এই subtract কে ইমপোর্ট করতে হলে একই নামে ইমপোর্ট করতে হবে **{ subtract }**।
কিন্তু, যে কোন ফাংশন named export করা যায়। এক্ষেত্রে ফাংশনের নামের সাথে **as** কিওয়ার্ড ব্যবহার করে তার সাথে অন্য আরেকটি নাম ব্যবহার করতে হবে। যেমনঃ

```
export { add as default, subtract as Test };
```
এখানে, subtract ফাংশনকে Test নামে named export এক্সপোর্ট করা হয়েছে।



```
function add(num1, num2) {
	return num1 + num2;
}

function subtract(num1, num2) {
	return num1 - num2;
}

export { add as default, subtract as Test };
```
