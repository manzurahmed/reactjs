# Episode 11

1. First, Install **heroku-cli** from "Add/Remove Software" in Manjaro.
2. Create an account in heroku website.
3. Login in to "heroku" from Terminal.
```
heroku login
```
4. Create a heroku app from Terminal:
```
heroku create my_app_name
```
5. I shall not run my app from **dist** folder, rather, I shall tell heroku not to use "Production mode" and install **yarn and build" my app from **src** folder.
```
heroku config:set YARN_PRODUCTION=false
```
In package.json file, I shall also declare a script for heroku to do it:
```
"heroku-postbuild": "yarn install && yarn build"
```
6. Remote URL set
7. Before pushing my product to heroku, I shall commit all staging files to git.
```
git add .
git commit -a
```
8. Push my product from "master" branch to heroku:
```
git push heroku master
```
