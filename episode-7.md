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

## 11. Working with Uncontrolled component

## 12. Validating form input

## 13. React developer tools

## 14. Working with Syte

## 15. Adding contact

## 16. Deleting contact

## 17. Toggling contact

## 18. Editing contact

## 19. Updating contact

## 20. Lifecycle method

## 21. Search contact

