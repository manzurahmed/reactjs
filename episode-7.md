# Episode 7: Practical App Development

## Where to Put State

State কে দুই ভাগে ভাগ করা যেতে পারে।

- Local State
- Global State

একটা বড় প্রজেক্টকে ছোট ছোট কম্পোনেন্টে ভাগ করে ফেলা হয়। ক্ষুদ্রাতিক্ষুদ্র কম্পোনেন্টের মধ্যে যে স্টেটগুলো ডিক্লেয়ার করা হয়, সেগুলোকে লোকাল স্টেট বলা যায়।

যদি একাধিক কম্পোনেন্টের মধ্যে একই ধরণের স্টেট শেয়ার করতে হয়, তবে, কম্পোনেন্টগুলোর প্যারেন্ট কম্পোনেন্টে ঐ কমন স্টেটগুলো ডিক্লেয়ার করতে হবে।

![Where to Put State](https://github.com/manzurahmed/reactjs/blob/master/where-to-put-state.jpg)

যদি, এমন পরিস্থিতি হয় যে, চাইল্ড কম্পোনেন্টে (Component 4) এমন একটি ডাটা (স্টেট) ব্যবহার করছে, যেটা অন্য কেউ আর ব্যবহার করছে না, সেক্ষেত্রে স্টেটটা Top Most Component এ ডিক্লেয়ার করতে হবে এবং React এর কনভেনশন অনুযায়ী ঐ চাইল্ড কম্পোনেন্টের ইমিডিয়েট প্যারেন্ট কম্পোনেন্টের মাধ্যমে স্টেটটা পাস করা লাগবে। চিত্র অনুযায়ী, Component 4 কে Top Most Component এর স্টেট পেতে হবে Component 1 এর মাধ্য দিয়ে।

বড় প্রজেক্টগুলোতে অনেক কম্পোনেন্ট তৈরী হলে এবং টপমোস্ট কম্পোনেন্ট ও চাইল্ড কম্পোনেন্টের মধ্যে যদি ১০ না ততোধিক লেভেল তৈরী হলে 

বড় প্রজেক্টের গ্লোবাল স্টেট ম্যানেজমেন্টের জন্য Redux এবং Context API ব্যবহার করা হয়।

বড় প্রজেক্টের গ্লোবাল স্টেট ম্যানেজমেন্টের জন্য নীচের ২টা API ব্যবহার হয়ে থাকেঃ

- Redux, এবং
- Context

Redux API কিন্তু React এর পার্ট নয়। একে ইনক্লুড করে অন্য ল্যাংগুয়েজে ব্যবহার করা যায়। কিন্তু, Context API কিন্তু ReactJS এর ন্যাটিভ পার্ট।

## 2. App mockup and state planning
![Component Division](https://github.com/manzurahmed/reactjs/blob/master/e7-component-division.jpg)

চিত্রে দেখানো হয়েছে আমাদের এ্যাপের কোন কোন অংশকে আলাদা আলাদা কম্পোনেন্টে ভাগ করা যেতে পারে।

## 3. Planning and placing component

এ্যাপের আর্কিটেকচার বিল্ড করার সময় Bottom-Up পদ্ধতিতে আগাতে হবে। অর্থাৎ, ক্ষুদ্রাতিক্ষুদ্র কম্পোনেন্ট আগে কোড করা শুরু করে ধীরে ধীরে Top most parent component এর দিকে যেতে হবে।

## 4. Working with header and navigation

এই পর্বে, আমাদের ফর্মের ভিজ্যুয়াল লে-আউটের জন্য Materialize CSS pack প্রজেক্টের সাথে যুক্ত করা হয়েছে। ম্যাটেরিয়াজসিএসএস সম্পর্কে বিস্তারিত জানতে ভিজিট করুনঃ https://materializecss.com/

Getting Start পেজ থেকে সিএসএস এর CDN লিংকটা কপি করে এনে index.html পেজের নীচে বসিয়ে দিব।

এ ছাড়াও এ্যাপের নেভিগেশন যুক্ত করা হয়।

## 5. Working with contact form

এই ভিডিওতে Contact Form টির মার্ক আপ লেখা হয়েছে।

## 6. Working with Contact

এই পর্বে Contact কম্পোনেন্ট নিয়ে কাজ করা হয়েছে।

## 7. Working with Search input

এই ভিডিওতে কন্টাক্ট সার্চ ফর্ম নিয়ে আলোচনা করা হয়েছে। আগেই বলা হয়েছে, ইউ.আই. এর জন্য MaterializeCSS ব্যবহার করা হয়েছে।

## 8. Generating contact dynamically

এই ভিডিও লেসনে টপ মোস্ট কম্পোনেন্ট App.js ফাইলে ৩টা কন্টাক্টকে স্টেট আকারে এ্যাসাইন্ট করা হয়েছে। এই স্টেটকে Contacts.js ফাইলে props আকারে পাস করে দেয়া হয়। Contact.js ফাইলে prop মধ্যে থাকা contacts অবজেক্ট এ্যারেকে map করে Contact.js কম্পোনেন্টে আবার props আকারে পাস করা হয়। Contact.js কম্পোনেন্টে একটি কন্টাক্টের প্রতিটা তথ্যকে this.props.contact এর মাধ্যমে অবজেক্ট প্রোপার্টি আকারে দেখানো হয়েছে।

## 9. Controlled component

এই পর্বে কন্টাক্ট ফর্মকে ফাংশনাল করা হয়েছে।

প্রথমেই ফর্মের ইনপুট কন্ট্রোলগুলোর সাথে **মিল রেখে** constructor এর মধ্যে state ডিক্লেয়ার করা হয়েছে। এবার, প্রত্যেকটা কন্ট্রোলের জন্য value এবং onChange, যুক্ত করা হয়েছে।

```js
<input
	type='text'
	name='lastName'
	value={this.state.lastName}
	onChange={this.handleChange}
/>
```

এছাড়াও, ফর্মের সাথে একটি event এটাচ করা হয়েছে, onSubmit।

এই ২টি ইভেন্টকে constructor এর মধ্যে কম্পোনেন্টের this ভ্যালুর সাথে বাইন্ড করা হয়েছে।

```js
this.handleSubmit = this.handleSubmit.bind(this);
this.handleChange = this.handleChange.bind(this);
```

নীচে দু'টি ইভেন্টের কোড দেয়া হলঃ

```js
handleSubmit(e) {
	e.preventDefault();
	console.log(this.state);
}

handleChange(e) {
	//console.log(e);
	this.setState({
		[e.target.name]: e.target.value
	});
}
```

আশা করি, আপনারা বুচ্ছেন!

## 10. Working with radio button in Controlled component

এই পর্বে ফর্মের রেডিও বাটন কিভাবে হ্যান্ডেল করতে হয়, তা দেখানো হয়েছে। ফর্মের স্টেটে রেডিও অপশনের যে কোন একটি ভ্যালুকে হার্ডকোড করে দেয়া হচ্ছে। অপশনগুলোতে সেই হার্ডকোডেড ভ্যালুর সাথে কম্পেয়ার করে সিলেক্টড অথবা ডিসিলেক্টেড স্টেটকে ডিফাইন করে সেট করা হচ্ছে।

```js
this.state = {
			firstName: '',
			lastName: '',
			email: '',
			profession: '',
			contactType: 'professional'
		};
```

রেডিও বাটনের checked ভ্যালুকে স্টেটের সাথে মিলিয়ে সেট করা হচ্ছেঃ

```js
<p>
	<label>
		<input
			name='contactType'
			type='radio'
			value='personal'
			onChange={this.handleChange}
			checked={this.state.contactType === 'personal'}
		/>
		<span>Personal</span>
	</label>
	<label>
		<input
			name='contactType'
			type='radio'
			value='professional'
			onChange={this.handleChange}
			checked={this.state.contactType === 'professional'}
		/>
		<span>Professional</span>
	</label>
</p>
```

## 11. Working with Uncontrolled component

ReactJS লাইব্রেরীতে Uncontrolled component তৈরীকে রিকমেন্ড করে না।

ReactJS আসলে বিহাইন্ড-দ্য-সিনে Virtual DOM নিয়ে কাজ করে। আমাদের কনটাক্ট ফর্মের কন্ট্রোলগুলোকে রিয়্যাক্টজেএস নিয়ন্ত্রন করে। যে কারণে একে বলা হয়, controlled component। Controlled component এ ফর্মের ইনপুটটা DOM এর সাথে করা হয়, এখানে virtual DOM এর কোন ইন্টার-এ্যাকশন থাকে না।

Controlled component এ ফর্মের প্রত্যেক কন্ট্রোলগুলোর জন্য ref={this.firstName} যুক্ত করা হয়েছে। এখানে {this.firstName} হল ঐ কন্ট্রোলের নাম, যে নামে ইনপুট ভ্যালুকে পাওয়া যাবে।

In React an <input type="file" /> is always an uncontrolled component because its value can only be set by a user, and not programmatically.

Uncontrolled component সম্পর্কে বিস্তারিত জানতে ReactJS এর অফিসিয়াল ডকুমেন্টেশন দেখুনঃ 
https://reactjs.org/docs/uncontrolled-components.html

## 12. Validating form input

এই ভিডিওতে ফর্মের ইনপুট ভ্যালিডেশন ও ভিজুয়াল এ্যালার্ট কিভাবে ইমপ্লিমেন্ট করা যায়, সে সম্পর্কে আলোচনা করা হয়েছে।

এছাড়াও, ইনপুট ফিল্ডের ভিজ্যুয়াল এ্যালার্ট নোটিফিকেশনের জন্য validator নামের একটি প্যাকেজ প্রজেক্টের সাথে ইন্সটল করা হয়েছে।

## 13. React developer tools

এই ভিডিওতে React Developer Tools নিয়ে আলোচনা করা হয়েছে।

একটি রিয়্যাক্টজেএস এ্যাপকে অনেকগুলো কম্পোনেন্টে বিভক্ত করা হয়। এদের মধ্যে state ও props এর ইন্টারচেঞ্জের অনেক ব্যাপার থাকে। শুধু console.log ব্যবহার করে প্রপ ও স্টেটকে ট্র্যাক করা বা ভ্যালু ইন্সপেক্ট করা বেশ কষ্টসাধ্য ব্যাপারে। ছোট এ্যাপে হয়ত অসুবিধা হবে না; কিন্তু, ইকমার্স এর মত বড় বড় সাইটে এটি একটি অসম্ভব ব্যাপার হয়ে দাঁড়াবে।

React Developer Tools নামে Chrome ও Firefox এর ব্রাউজার এক্সটেনশন ব্যবহারে এই অসুবিধা দূর হয়।

## 14. Working with Syte

রিয়্যাক্টজেএস এ্যাপের মধ্যে style ব্যবহারের বিষয়ে আলোচনা করা হয়েছে এই ভিডিওতে।

এ্যাপের html tag গুলোতে বিভিন্নভাবে স্টাইল যুক্ত করা যায়।

* এক্সটারনাল স্টাইল ফাইল লিখে index.html থেকে যুক্ত করে দেয়া
* index.html এ Inline CSS লেখা যায়
* html tag এর সাথে style এট্রিবিউট ব্যবহার করা।
* **Top most component** এর মধ্যে **import** স্টেটমেন্ট ব্যবহার করা

**Linking via index file**

```css
<link rel="stylesheet" href="style.css" />
```

**Inline CSS**

```css
<style>
  nav .nav-wrapper {
    padding: 0 10px;
  }
</style>
```

**Inline CSS with HTML Tag**

```html
<input type='text' onChange={this.handleChange}
  value={lastname}
  name='lastName'
  style={{
    backgroundColor: 'red'
  }}
```


## 15. Adding contact

এই ভিডিওতে কিভাবে ContactForm এর মাধ্যমে নতুন কন্টাক্ট যুক্ত করা যায়, তা দেখানো হয়েছে।

ContactForm থেকে নতুন কন্টাক্ট যুক্ত করার সময় নিচের ওয়ার্নিংটা দেখাচ্ছিল।

```
Warning: Each child in a list should have a unique "key" prop.
```

এর কারণ হল, প্রতিটা কন্টাক্ট রেন্ডার করার সময় একটা key দিতে হয়, যা ContactForm এ ছিল না। নতুন কন্টাক্ট এ্যাড করার সময় একটি নতুন key তৈরী করার জন্য একটা npm package ইন্সটল করা হয়। নিচের কমান্ড দিয়ে প্যাকেজটি ইন্সটল করে নিব।

```
yarn add uuid
```

ContactForm এর মধ্যে uuid প্যাকেজটি import করে নেয়ার পরে state object এর মধ্যে নতুন id জেনারেট করার ব্যবস্থা করা হল। এর মধ্যে দিয়ে "unique key prop" এর ওয়ার্নিংটা দূর হয়ে যাবে।


## 16. Deleting contact

এই পর্বে কিভাবে Detele আইকনে ক্লিক করে ১টি কন্টাক্টকে মুছে দেয়া যায়, সে সম্পর্কে আলোচনা করা হয়েছে।

প্রতিটা কন্টাক্টের সাথে কন্টাক্টের আইডি নম্বর জুড়ে দেয়া হচ্ছে। ডিলিট বাটনে ক্লিক করলে, একটি মেথড কল করা হচ্ছে, যেটা আবার Contact কম্পোনেন্টের প্যারেন্ট কম্পোনেট Contacts কম্পোনেন্টের deleteContact মেথডকে কল করছে। এই deleteContact মেথডটি প্যারেন্ট কম্পোনেন্টের props এর মাধ্যমে পাস করা হয়েছিল।

Contacts কম্পোনেন্টে contacts এ্যারেকে .map করার সময় Contact কম্পোনেন্টের কাছে ডাটা পাঠাচ্ছিল।

```js
<div className='row'>
{this.props.contacts.map(contact => (
	<div className='col s6' key={contact.id}>
		<Contact
			contact={contact}
			deleteContact={this.props.deleteContact}
		/>
	</div>
))}
</div>
```
**app.js** কম্পোনেন্ট হল **top most component**. এখান থেকে Contacts কম্পোনেন্টের কাছে ডাটা পাঠানোর সময় deleteContact নামের মেথডও পাঠিয়ে দেয়া হয়। এই মেথডের মাধ্যমে bottom most কম্পোনেন্ট Contact থেকে কোন কন্টাক্ট ডিলিট করা হচ্ছে, তার তথ্য bubble আকারে পাঠিয়ে দেয়া হচ্ছে।

```js
<div className='col s8'>
	<Contacts
		contacts={this.state.contacts}
		deleteContact={this.deleteContact}
	/>
</div>
```

## 17. Toggling contact

এই ভিডিওতে  প্রতিটা কন্টাক্টের সাথে থাকা টুলবার থেকে Toggling বাটনে ক্লিক করে কন্ট্যাক্টকে ভার্টিক্যালি এক্সপান্ড বা কলাপ্স করার পদ্ধতি দেখানো হয়েছে।

## 18. Editing contact

এই ভিডিওতে কন্টাক্ট লিস্ট থেকে Edit বাটনে চাপ দিয়ে কিভাবে এডিট ফর্মে পপুলেট করতে হয়, সে হাতে-কলমে দেখানো হয়েছে।

## 19. Updating contact

Episode 7: Video 19. Updating contact

এই ভিডিও লেসনের শুরুতেই ContactForm.js ফাইলকে রিনেম করে AddContact.js নামকরণ করা হয়। EditContact.js নামের নতুন একটি ফাইল তৈরী করা হয়।
App.js ফাইলে ContactForm.js এর import এর রেফারেন্সকে ফিক্স করা হয়েছে।

## 20. Lifecycle method

## 21. Search contact

