# React Routing

## 1. Introduction to section

এই পর্ব ReactJS এ Routing কিভাবে কাজ করে সে সম্পর্কে বিস্তারিত আলোচনা করা হয়েছে। আমাদের কন্টাক্ট এ্যাপটি লক্ষ্য করলে দেখবেন যে, এখানে সব কিছু এক পেজে নিয়ে এ্যাপ বানানো হয়েছে।

About পেজে কোন কিছু দেয়া হয়নি। About লিংকে ক্লিক করলে About পেজের কন্টেন্ট দেখাবে। এই যে, request এর ভিত্তি করে কোন কন্টেন্ট লোড করতে হবে, সেই ডিশিসন মেকিং টাস্কটার দায়িত্ব নিয়েছে ReactJS এর Routing বাবাজি।



## 2. Client vs Server side Routing

**Server-side routing**

![Server-side Routing](https://github.com/manzurahmed/reactjs/blob/master/server-side-routing.jpg)

এই ক্ষেত্রে ইউজার ওয়েবসাইট/এ্যাপ ব্রাউজ করার জন্য example.com ওয়েবসাইটে রিকুয়েস্ট পাঠালে, রিকুয়েস্টটা সার্ভারে পৌঁছাবে এবং URL এর উপরে ভিত্তি করে প্রয়োজনীয় প্রসেসিং শেষে request টা পুনরায় ব্রাউজারে পাঠাবে।

আবার, example.com/about URL এ রিকুয়েস্ট পাঠাবে তখন আবারও সার্ভার থেকে প্রয়োজনীয় ডাটা ব্রাউজারের কাছে ফেরত পাঠাবে যেটা ইউজার দেখতে পারবেন।

উভয় ক্ষেত্রেই ব্রাউজারের পেজটা Reload হয়ে নতুন কন্টেন্ট দেখা যাবে।

**Client-side routing**

![Client-side Routing](https://github.com/manzurahmed/reactjs/blob/master/client-side-routing.jpg)

একটা উদাহরণ দিয়ে Client-side routing টা বুঝানো হয়েছে। যদি আমরা https://reactjs.org ওয়েবসাইট ব্রাউজ করি, তাহলে খেয়াল করে দেখা যাবে যে, এর হোম পেজ ব্রাউজ করার সময় রিকুয়েস্টটা সার্ভারে যাচ্ছে এবং পুরো সাইটের কন্টেন্টসহ ব্রাউজারে অর্থাৎ ক্লায়েন্টের কাছে পাঠিয়ে দেয়া হচ্ছে। অর্থাৎ ক্লায়েন্ট সাইডে রিয়াক্টজেএস সাইটের কন্টেন্টকে cache করে রাখা হচ্ছে।

পরবর্তীতে যখন অন্যান্য লিংকে ক্লিক করলে, ঐ লিংকের কন্টেন্টের জন্য আর সার্ভার পর্যন্ত যেতে হচ্ছে না, বরং, ক্লায়েন্ট সাইডে ক্যাশে হয়ে থাকা কন্টেন্ট থেকে দেখানো হচ্ছে। এইটাই হল, Client-side routing এর সুবিধা।

## 3. Introduction to React-router-dom use

কোর ReactJS Library এর মধ্যে Routing যুক্ত করা নাই। একে npm এর মাধ্যমে প্রজেক্টের সাথে যুক্ত করে নিতে হয়।

জনপ্রিয় দু'টি রাউটিং প্যাকেজের নাম react-router-dom এবং reach-router.

https://www.npmjs.com/package/react-router-dom 

https://www.npmjs.com/package/@reach/router

https://reacttraining.com/react-router/web/guides/quick-start
https://reach.tech/router

শুরুতেই react-router-dom ইন্সটল করে নিব। রাউটিং সম্পর্কে বিস্তারিত জানতে reacttraining.com এর ডকুমেন্টেশন পড়তে হবে।

```
yarn add react-router-dom
```

Routing এর ৩টি মেইন কম্পোনেন্ট হল,
- BrowserRouter,
- Router, এবং,
- Link

ReactJS এ রাউটার ব্যবহারের জন্য react-router-dom লাইব্রেরী থেকে BrowserRouter কম্পোনেন্টকে import করে নিতে হবে। BrowserRouter কম্পোনেন্টকে destructure করে আমরা মূলতঃ ৪টি কম্পোনেন্টকে ব্যবহার করবঃ

- BrowserRouter
- Route
- Switch
- Link

```
import { BrowserRouter } from 'react-router-dom';
```

**BrowserRouter এর ব্যবহার**

```
const router = (
	<BrowserRouter>
		<App />
	</BrowserRouter>
);
```

আমাদের Contacts App এর App.js ফাইলে Route কে ব্যবহার করব। প্রথমে ইম্পোর্ট করে নিতে হবেঃ

```
import { Route } from 'react-router-dom';
```

এবার render() মেথডের মধ্যে Route কে ব্যবহার করার পালাঃ

```
<Route path='/about' exact component={About} />
```

## 4. Where to use render in Routing

About পেজকে ব্রাউজারের ReactJS developer tool দিয়ে ইন্সপেক্ট করব। সেখানে About কম্পোনেন্টের উপরে ক্লিক করলে ডান দিকে উইন্ডোতে এর সাথে সংশ্লিষ্ট props গুলোর লিস্ট দেখাবে। এই props গুলো  ReactJS নিজে থেকেই আমাদের জন্য সরবরাহ করেছে। সেগুলো হলঃ

- history
- location
- match

এখানে match মধ্যে থাকা params অবজেক্টটি বেশি ব্যবহৃত হবে।

**match params এর ব্যবহার**

App.js এর render মেথডের মধ্যে <Route path='/about/:samim' component={About} /> অংশে /about এর পরে একটি ভ্যারিয়েবল পাস করা হয়েছে। এবার, ব্রাউজারে এ্যাড্রেস বারে যদি localhost:1234/about/me লিখে এন্টার দেই এবং রিয়াক্ট টুল দিয়ে match params এর মান পরীক্ষা করে দেখি, তবে দেখতে পাব সেখানো দেখা যাবেঃ
```
samim: "me"
```

এই ভ্যালুকে props এর মাধ্যমে About.js কম্পোনেন্ট থেকে এ্যাক্সেস করা যাবে। About.js ফাইল খুলে সেখানে render এর মধ্যে এভাবে লিখবঃ

```js
render() {
	return <h3>About Us Page {this.props.match.params.samim}</h3>;
}
```

## 5. Continue to working with Routing

Routing এর আরও কিছু খুঁটিনাটি বিষয় নিয়ে এই ক্লাসে আলোচনা করা হয়েছে। নীচের কোডটি খেয়াল করলে দেখা যাবে যে, এখানে Route এর মধ্যে Contacts কম্পোনেন্টকে পাস করা হয়েছে।

```js
<Route
	path='/'
	exact
	render={() => (
		<Contacts
			contacts={this.state.contacts}
			deleteContact={this.deleteContact}
			editContact={this.editContact}
		/>
	)}
/>
```

এখন এই Contacts কম্পোনেন্টকে ব্রাউজার থেকে ReactJS টুল দিয়ে ইন্সপেক্ট করলে দেখা যাবে, Contacts কম্পোনেন্টের ক্ষেত্রে Router এর কোন props পাওয়া যাবে না, যেটা About এর ক্ষেত্রে পাওয়া যাচ্ছিল। এর কারণ হল, Contacts কে একটি অবজেক্ট আকারে পাস করা হয়েছে।

এর সাথে Router এর props পেতে হলে আর্গুমেন্ট আকারে props পাস করে দিতে হবে।

```js
<Route
	path='/'
	exact
	render={props => (
		<Contacts
			contacts={this.state.contacts}
			deleteContact={this.deleteContact}
			editContact={this.editContact}
			{...props}
		/>
	)}
/>
```

## 6. Loading NotFound Page

## 7. Working with Link and NavLink component

## 8. Working with Link continued

## 9. Little Organization
