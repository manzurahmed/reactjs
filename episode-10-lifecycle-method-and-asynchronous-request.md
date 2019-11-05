# Lifecycle Method and Asynchronous Request

রিয়াক্ট কম্পোনেন্ট ব্রাউজারে লোড হয়ে দৃশ্যমান হওয়ার সময় বেশ কয়েকটি পর্যায়ের মধ্যে দিয়ে অতিক্রম করে। এই ধাপগুলোকে সামগ্রিকভাবে "লাইফসাইকেল" বলে।

রিয়াক্ট ডেভেলপারদের রিয়াক্ট এ্যাপের লাইফসাইকেল সম্পর্কে পরিষ্কার ধারণা থাকা খুবই গুরুত্বপূর্ণ। রিয়াক্টজেএস এর  অফিশিয়াল ডকুমেন্টেশন পড়ে এ সম্পর্কে বিস্তারিত জানা যাবে।

[ReactJS Official Documentation Repo](https://reactjs.org/docs/react-component.html)

এই পেজে রিয়াক্ট এ্যাপের লাইফসাইকেলের একটা স্কিমেটিক ডায়াগ্রাম দেয়া হয়েছে।

[ReactJS Lifecycle Diagram](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

![ReactJS Lifecycle Diagram](https://github.com/manzurahmed/reactjs/blob/master/react-life-cycle.png)

## 1. Introduction to Lifecycle Method

ReactJS এর লাইফসাইকেলে ৩টি পর্যায় রয়েছে।

- Mounting
- Updating
- Unmounting

**Mounting**

যখন কোন রিয়াক্ট কম্পোনেন্ট লোড হয়, তখন এই মাউন্টিং স্টেজ শুরু হয়। এই স্টেজে ৪টি মেথড কল হয়।

- constructor
- static getDerivedStateFromProps()
- render()
- componentDidMount()

## 2. Lifecycle Method in Mounting

কম্পোনেন্ট মাউন্ট হওয়ার সময় কি কি বিষয় সংঘটিত হয় তা এই ভিডিওতে বর্ণনা করা হয়েছে।

## 3. Lifecycle Method in Updating

"Updating" stage e নিচের সিরিয়ালে ফাংশনগুলো এক্সিকিউট হয়।

static getDerivedStateFromProps()
shouldComponentUpdate()
render()
getSnapshotBeforeUpdate()
componentDidUpdate()

## 4. Lifecycle Method in Unmounting

এই ক্লাসে Lifecycle স্টেজের Unmount নিয়ে আলোচনা করা হয়েছে। এতে, একটি ২/৩ লাইনের টাইমার টিকার বানানো হয়েছে। টিকার চালু থাকা অবস্থায় অন্য কোন কম্পোনেন্টে নেভিগেট করে চলে গেলেও টাইমারটা ব্যাকগ্রাউন্ডে চালু থাকে যা একটা Error message জেনারেট করে। componentWillUnmount ফাংশনের মধ্যে clearInterval ফাংশন ব্যবহার করে টাইমারের হ্যান্ডেলকে (this.timerId) Unmount করা হয়েছে।

## 5. More Lifecycle Method

এই ক্লাসে কম্পোনেন্টের লাইফসাইকেলের আরও কিছু বিষয় ডিটেইল্ড আলোচনা করা হয়েছে। contact.js এ Update স্টেজে এসে দেখা গেল যে, DOM দুইবার updae হচ্ছিল। কারণ, প্রথম বার props রিয়াক্টজেএস কম্পেয়ার করে দেখে না যে, props যেটা হাতে পেয়েছে সেটা কি আদৌ আগে একবার রেন্ডার করা হয়েছিল কিনা। props এর মানের তুলনামূলক পরীক্ষা না করার ফলে একই props কে একাধিক বার রেন্ডার করা হচ্ছিল, যেটা আসলে এ্যাপের পারফরমেন্সে নেগেটিভ ইম্প্যাক্ট ফেলে।

এই কারণ, React এর নেমড কম্পোনেন্ট "Component" এর পরিবর্তে "PureComponent" ব্যবহার করা হয়েছে (ভিডিওর ১১ঃ৫২ মিনিট টাইমলাইন)।

PureComponent সম্পর্কে বিস্তারিত জানতে [অফিশিয়াল ডকুমেন্টেশন](https://reactjs.org/docs/react-api.html#reactpurecomponent) দেখুন।

React.PureComponent is similar to React.Component. The difference between them is that React.Component doesn’t implement shouldComponentUpdate(), but React.PureComponent implements it with a shallow prop and state comparison. 

## 6. Working with JSON-Server

আমাদের এই কোর্সে এ পর্যন্ত আমরা Contact.context.js ফাইলে হার্ডকোডেদ এ্যাড্রেস রেখেছিলাম। এই ক্লাসে JSON-server ইন্সটল করা হয়। এই সার্ভারে এ্যাপের এ্যাড্রেসগুলো রাখা হবে। এর অফিশিয়াল git repo এই এ্যাড্রেসে পাওয়া যাবে। https://github.com/typicode/json-server

এ্যাপের রুট ফোল্ডারে **server** নামে একটি ফোল্ডার তৈরী করে সেই ফোল্ডারের মধ্যে নেভিগেট করে যেতে হবে। এর মধ্যে একটি ফাঁকা package.json ফাইল তৈরী করব।

```
mkdir server
cd server
yarn init -y
```

এবার লোকাল প্রজেক্টের জন্য json-server কে developer dependency হিসাবে ইন্সটল করব। কারণ, প্রোডাকশনে json-server কে ব্যবহার করা হয় না।

```
yarn add json-server
```

json-server এর ডকুমন্টেশন অনুযায়ী এর ফোল্ডারের মধ্যে **db.json** নামে একটি ফাইল তৈরী করব। এর মধ্যে টেস্ট ডাটা হিসাবে কিছু রেডিমেড ডাটা অফিশিয়াল ওয়েবসাইট থেকে পেস্ট করা হয়েছে।

```js
{
	"posts": [
		{ "id": 1, "title": "json-server", "author": "typicode" },
		{ "id": 1, "title": "xampp", "author": "typicode" }
	],
	"comments": [{ "id": 1, "body": "some comment", "postId": 1 }],
	"profile": {
		"name": "typicode",
		"email": "samimfazlu@gmail.com"
	}
}
```

এই json-server কে টার্মিনাল থেকে রান করানোর জন্য package.json ফাইলে script নামে নতুন একটি এন্ট্রি নিচের মত করে লেখা হয়েছেঃ

```js
"scripts": {
		"dev:server": "json-server --watch db.json"
	},
```

এবার টার্মিনাল থেকে "yarn dev:server" লিখে এন্টার চাপ দিলে json-server ব্যাকগ্রাউন্ডে চালু হবে।

**একটা কথা মনে রাখতে হবে।** json-server কে প্রজেক্টের রুটের server ফোল্ডারে ইন্সটল করা হয়েছে। এই সার্ভারকে চালু করতে হলে **server** ফোল্ডারের মধ্যে গিয়ে কমান্ড ইস্যু করতে হবে।

আমাদের প্রজেক্টের ট্র্যান্স-কম্পাইলার হিসাবে parcel ব্যবহার করা হচ্ছে এবং আমাদের অ্যাপকে রান করানোর জন্য আমরা টার্মিনাল থেকে "yarn dev --open" কমান্ড ব্যবহার করছিলাম। এখন, আমাদের প্রজেক্টে json-server ও রান করাতে হবে। এ জন্য প্রজেক্টের রুটে থাকা package.json ফাইলে নিচের মত করে পরিবর্তন করা হয়েছে। ক্লায়েন্ট সার্ভারকে রিনেম করে dev:client করা হয়েছে, যা পূর্বে ছিল শুধু dev।

এবার, টার্মিনালে নেভিগেট করে রুট এ এসে মূল প্রজেক্টের সাথে ব্যবহারের জন্য json-server কে ইন্সটল করে নিব।

```js
yarn add json-server
```

```js
"scripts": {
	"dev:server": "yarn --prefix server json-server --watch ./server/db.json",
	"dev:client": "parcel index.html",
	"start": "concurrently \"yarn dev:server\" \"yarn dev:client\"",
	"format": "prettier --write \"src/**/*.{js,jsx}\"",
	"lint": "eslint \"src/**/*.{js,jsx}\""
},
```

package.json ফাইলে **start** নামে নতুন একটি স্ক্রিপ্ট ডিফাইন করা হয়েছে, যেখানে জেসন-সার্ভার এবং এ্যাপ - দুইটাই এক সাথে রান করা হবে। এর জন্য **concurrently** নামে নতুন একটু প্যাকেজ ইন্সটল করতে হবে এবং start স্ক্রিপ্টের পূর্বে concurrently শব্দটি যুক্ত করে দিলে dev:server এবং dev:client - দুইটা স্ক্রিপ্টই এক সাথে রান করতে থাকবে।

```js
"start": "concurrently \"yarn dev:server\" \"yarn dev:client\"",
```

নতুন কনফিগ নিয়ে আমাদের এ্যাপ ও জেসন-সার্ভার রান করার জন্য নিচের কমান্ড দিতে হবে।

```js
yarn start
```

## 7. Getting Contacts from API

## 8. Adding Contact

## 9. Deleting Contact

## 10. Updating Contact

## 11. Fetch to Axios
