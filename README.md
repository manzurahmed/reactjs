# Learn Reactjs

## Using create-react-app

টার্মিনাল খুলে নীচের কমান্ড দিয়ে reactjs এর npm প্যাকেজ ইন্সটল করতে হবে। ইন্সটল হয়ে গেলে আরেকটি কমান্ড দিয়ে আমাদের প্রথম রিয়্যাক্টজেএস এ্যাপ তৈরীর জন্য আরেকটি কমান্ড লিখব।

```
sudo npm install -g create-react-app
sudo create-react-app react-app
```

দ্বিতীয় কমান্ডটির মাধ্যমে আমি react-app নামে একটি রিয়্যাক্ট এ্যাপ তৈরী করেছি। এই এ্যাপটি চালু করতে হলে টার্মিনালে লিখতে হবেঃ
```
npm start
```

**এই টা কোন ক্লাসের?????????**
React's core building block is "Component".

## What is React Component?

Components refer to "reusable pieces of code" ultimately responsible for "returning HTML" to be rendered onto the page comprised of "HTML, Logic, even Data".

## Who creates element?

"React.createElement" returns object and responsible for HTML in the browser.

## Making Visual Studio Code Editor suitable for React

```
"emmet.includeLanguages": {
	"javascript": "javascriptreact"
},
"emmet.syntaxProfiles": {
	"javascript": "jsx"
}
```

## Packages to install

1. Babel ES6/ES7
2. Bracket Pair Colorizer - CoenraadS
3. Path Intellisense - Christian Kohler
4. Prettier - Code formatter - Esben Petersen
5. React-Native/React/Redux snippets for es6/es7 - EQuimper

# Video - 6: Introduction to parcel.mp4

1. Dependency issue
2. Global variable
3. Creating server
4. Transpiling issue (use Babel)
5. ES6 module - Gulp, WebPack

## Install Parcel as DevDependency
```
yarn add parcel-bundler -D
```
Parcel takes about 4 minutes to install over 2 mbps connection.

# Video 7: Configuring parcel

Install React and ReactDOM:
```
yarn add react react-dom

```
