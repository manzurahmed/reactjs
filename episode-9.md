# Working With Context API

## 1. Problem in statement management and solution

ট্রাডিশনাল নিয়মে টপ-মোস্ট কম্পোনেন্ট ও বটম-মোস্ট কম্পোনেন্টের মাঝে যে কয়টি কম্পোনেন্ট থাকে, তাদের ভিতর দিয়ে props এবং state গুলোকে পাস করে দেয়া হয়। এর ফলে, বেশি কোড লেখা হচ্ছে যা মেইনটেইন করা ঝামেলা ও ভুল হওয়ার সম্ভাবনা বাড়িয়ে দেয়। ইন্টারমিডিয়েট লেভেলে ৫টি বা ১০টি কম্পোনেন্ট থাকলে, তখন প্রতিটা কম্পোনেন্টের মধ্য দিয়ে props এবং state পাস করিয়ে আনতে হবে। বিশাল ঝামেলা!

এই ঝামেলাকে দূর করতে গ্লোবাল স্টেট ম্যানেজমেন্টের জন্য বেশ কিছু লাইব্রেরী তৈরী হয়েছে। তাদের মধ্যে ২টি লাইব্রেরী জনপ্রিয়তা পেয়েছে।

- Redux
- Context API

Redux লাইব্রেরী সব ধরণের ওয়েব প্রজেক্টের সাথে ব্যবহার করা যায়। কিন্তু, Context API লাইব্রেরীটি ReactJS এর নিজস্ব স্টেট ম্যানেজমেন্ট সল্যুশন।

## 2. Introduction to Context API

Context API ব্যবহার করার জন্য প্রজেক্টের src ফোল্ডারের মধ্যে contexts নামের একটি ফোল্ডার বানিয়ে তার মধ্যে Contact.context.js নামের একটি ফাইল তৈরী করে নিব। এই ফাইলের কন্টেন্ট নিচে দেয়া হলঃ

```js
import React, { Component } from 'react';
export const ContactContext = React.createContext();

export class ContactProvider extends Component {
	render() {
		return (
			<ContactContext.Provider
				value={{ firstName: 'samim', lastName: 'hasan' }}
			>
				{/* Must pass "Single Data" in value, single object, single array, single variable, etc. */}
				{this.props.children}
			</ContactContext.Provider>
		);
	}
}
```

আমাদের বানানো এই কন্টেক্সট প্রোভাডারকে আমাদের top-most component এ ব্যবহার করব, আমাদের এ্যাপের ক্ষেত্রে index.js ফাইলে।

```js
const router = (
	<BrowserRouter>
		<ContactProvider>
			<App />
		</ContactProvider>
	</BrowserRouter>
);
ReactDOM.render(router, document.getElementById('root'));
```

এবার, App.js ফাইলে context কে কনজিউম করা হবে, সেই ক্লাসে কনটেক্সট প্রোভাইডার ফাইলকে ইম্পোর্ট করে নিতে হবে। ContactContext কে **static** হিসাবে ডিক্লেয়ার করা হয়েছে। এই কনজিউমার ক্লাসে কন্টেক্সটকে **this.context** হিসাবে এ্যাক্সেস করা যায়।

ReactJS এর অফিসিয়াল ওয়েবসাইটে Context API সম্পর্কে বিস্তারিত জানা যাবে এই ঠিকানায় https://reactjs.org/docs/context.html

## 3. Working with Context API continued

কন্টেক্সটকে বানানো হয়েছে আমাদের এ্যাপের স্টেটগুলোকে সেন্ট্রালি ম্যানেজ করা। সেই কাজটি এই ক্লাসে দেখানো হয়েছে।

প্রথমে App.js ফাইল থেকে আমাদের contacts অবজেক্টকে তুলে নিয়ে এসে context ফাইলের মধ্যে জুড়ে দেয়া হয়েছে।

App.js থেকে addContact, deleteContact, editContact - এই ইভেন্ট হ্যান্ডলারগুলোকে ContactContext class এর মধ্যে নিয়ে যাওয়া হয়েছে।

**এই ক্লাশটি খুব গুরুত্বপূর্ণ। আবার দেখতে হবে।**

## 4. Using Context API in Contacts

এই ক্লাসে Contacts.js কম্পোনেন্টে পূর্বের props এর পরিবর্তে Context কে ব্যবহার করা হয়েছে।

## 5. Using Context API in Edit Update and Delete contact

## 6. Concept in Reducer

## 7. Dispatching Add Contact

## 8. Dispatching EDIT UPDATE DELETE contact

## 9. Organizaing Our Project

