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

## 7. Working with Search input

## 8. Generating contact dynamically

## 9. Controlled component

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

