# Deploy `json-server`

> Instructions how to deploy the full fake REST API [json-server](https://github.com/typicode/json-server) to various free hosting sites. Should only be used in development purpose but can act as a simpler database for smaller applications.

<img src="http://i66.tinypic.com/x6mp6p.jpg" align="right" width="100px">

* [**Create your database**](#create-your-database)
* [Deploy to **Heroku**](#deploy-to-heroku)

## Create your database

1 . Clone this repo to anywhere on your computer.

```bash
git clone https://github.com/imdadareeph/phoenixapi.git
```

2 . Change `db.json` to **your own content** according to the [`json-server example`](https://github.com/imdadareeph/phoenixapi/json-server#example) and then `commit` your changes to git. 

_this example will create `/posts` route , each resource will have `id`, `title` and `content`. `id` will auto increment!_
```json
{
  "posts":[
    {
      "id": 0,
      "content": "Wow such cool guy!",
      "username": "imdadareeph"
    }
  ]
}
```

---
## Screenshot **Heroku**
![alt text](http://i66.tinypic.com/97lgk9.jpg "screenshot")

## Deploy to **Heroku**

<img align="right" width="100px" height="auto" src="https://cdn.worldvectorlogo.com/logos/heroku.svg" alt="Heroku">

Heroku is a free hosting service for hosting small projects. Easy setup and deploy from the command line via _git_.

---

### Install Heroku

1 . [Create your database](#create-your-database)

2 . Create an account on <br/>[https://heroku.com](https://heroku.com)

3 . Install the Heroku CLI on your computer: <br/>[https://devcenter.heroku.com/articles/heroku-cli](https://devcenter.heroku.com/articles/heroku-cli)

4 . Connect the Heroku CLI to your account by writing the following command in your terminal and follow the instructions on the command line:
```bash
heroku login
```

5 . Then create a remote heroku project, kinda like creating a git repository on GitHub. This will create a project on Heroku with a random name. If you want to name your app you have to supply your own name like `heroku create project-name`:
```bash
heroku create my-fake-server
```

6 . Push your app to __Heroku__ (you will see a wall of code)
```bash
git push heroku master
```

7 . Visit your newly create app by opening it via heroku:
```bash
heroku open
```

8 . For debugging if something went wrong:
```bash
heroku logs --tail
```

---

#### How it works

Heroku will look for a startup-script, this is by default `npm start` so make sure you have that in your `package.json` (assuming your script is called `server.js`):
```json
 "scripts": {
    "start" : "node server.js"
 }
```

You also have to make changes to the port, you can't hardcode a dev-port. But you can reference herokus port. So the code will have the following:
```js
const port = process.env.PORT || 4000;
```

---

## Another way

How to
Create a repository on GitHub (<your-username>/<your-repo>)
Create a db.json file
Visit https://my-json-server.typicode.com/<your-username>/<your-repo> to access your server




Credits : https://github.com/jesperorb/json-server-heroku

