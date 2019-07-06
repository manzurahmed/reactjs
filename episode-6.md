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

## 3. State

In the lifecycle of an application, if a piece of data changes **dynamically**, can be identified as **State**. A State is not limited to ReactJS. Every application in any platform has State.

## 4. How to write React state?
```
class PlayGround extends Component
{
	constructor( props )
	{
		super(props);
		
		this.state = {
			player1Score: 0,
			player2Score: 0,
			winningScore: 7,
			// so on
		}
	}
}
```

1. To use "State", I must switch to **Class-based Component** instead of "Function-based Component".
2. In case of "Stateless Component", I can omit Constructor function.
3. In recent JS updates, I can use State in Function Component.

## 6. Introduction to State Changing

**this.setState()** is the built-in React method of changing a component's state.
```
this.setState( { P1Score: 3 } );
```

When a state changes, React changes the view automatically.

## 8. Introduction to React event
## 9. React Event in Practice

In React, every JSX element has built-in attributes representing every king of browser event. They are **camel-Cased**, like, **onClick**, and take callback functions as event listeners.
```
<button onClick={this.handleClick}>
   Click Me!
</button>
```

This is the code that handles the button's click event:
```
handleClick() {
	this.setState({
		count: this.state.count + 1
	});
}
```

And, in the constructor of the class, I must bind this event handler to the **this** instance of the class, otherwise it won't find the **this**.

```
this.handleClick = this.handleClick.bind(this);
```

## 10. More on setState

**setState** is an asynchronous function. It can receive a callback function. Using callback while setting State ensured that it will execute its inner hapennings when where are multiple states that being setting up.
```
handleClick() {
	this.setState(prevState => ({
		count: prevState.count + 1,
		counting: true
	}));
	this.setState(prevState => ({
		count: prevState.count + 1,
	}));
	this.setState(prevState => ({
		count: prevState.count + 1,
	}));
}
```

## 13. state and props

- state and props are both plain object.
- props is not mutable, but, state is mutable.
- state stores changing component data.
- props stores component configuration data.

## 14. Alternative Configuration

রিয়াক্টজেএস কম্পোনেন্টের মধ্যে ইচ্চ্যামত ফাংশন লিখা যায় না, প্রপ ও স্টেটকে সরাসরি মিউটেট করা যায় না। তবে, babel এর কিছু এক্সপেরিমেন্টাল কিছু ফিচার ইন্সটল করে ব্যবহার করা যায়। এই কোর্সে Parcel ব্যবহার করা হয়েছে, যার সাহায্যে ব্যাবেলকে প্রিকনফিগার করা করা আছে। আল্টারনেট কনফিগারেশন ব্যবহার করা জন্য কিছু প্যাকেজ ইন্সটল করে সেগুলোকে ব্যাবেল এর এনভার্নমেন্টের সাথে রিকনফিগার করতে হবে। নতুন যে প্যাকেজগুলো ইন্সটল করতে হবে সেগুলো হলঃ

```
yarn add @babel/core @babel/preset-env @babel/preset-react @babel/plugin-proposal-object-rest-spread @babel/plugin-proposal-class-properties babel-eslint -D
```

এছাড়া, eslint এর পারসার হিসাবে babel-eslint কে আইডেন্টিফাই করে দিতে। এ জন্য **.eslintrc.json** ফাইলের একেবারে প্রথমে নিচের লাইনটি যুক্ত করে দিতে হবে।

```
"parser": "babel-eslint",
```

এবার প্রজেক্টের রুট এ .babelrc নামে একটি ফাইল তৈরী করে তার মধ্যে নীচের লাইনগুলো লিখতে হবেঃ
```
{
	"presets": ["@babel/preset-env", "@babel/preset-react"],
	"plugins": [
		["@babel/plugin-proposal-class-properties", {}, "class properties"],
		["@babel/plugin-proposal-object-rest-spread", {}, "class properties"]
	]
}
```

কাজ শেষ। এবার টার্মিনাল থেকে আবার yarn dev --open লিখে এন্টার দিলে সব কনফিগারেশন যদি ঠিক থাকে তবে পারসেল চালু হবে ও এটা ওয়াচ মুডে যাবে এবং আমাদের প্রজেক্টের আউটপুট ব্রাউজারে দেখা যাবে।
