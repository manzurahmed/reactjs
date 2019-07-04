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
