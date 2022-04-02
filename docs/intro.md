---
sidebar_position: 1
---

# Quick start

## Getting Started

### install lib

```bash
pip install sanic-discord sanic
```

or

```bash
pip install git+https://github.com/tuna2134/sanic-discord.git sanic
```

### For example

oauth2

```py
from sanic import Sanic
from sanic import response
from sanic_discord import Client
from sanic_discord import Config

app = Sanic("app")
client = Client(Config(secret="", id="", login_url="", callback_url="", redirect_url="/me"))

@app.route("/")
async def main(request):
    return response.text("test")
    
@app.route("/callback")
async def callback(request):
    return await client.callback(request)
    
@app.route("/me")
@client.oauth2_require()
async def me(request, user):
    return response.text(user["username"])
    
app.run(host="0.0.0.0", port=8080)
```

interaction

```python
```

## Generate a new site

Generate a new Docusaurus site using the **classic template**.

The classic template will automatically be added to your project after you run the command:

```bash
npm init docusaurus@latest my-website classic
```

You can type this command into Command Prompt, Powershell, Terminal, or any other integrated terminal of your code editor.

The command also installs all necessary dependencies you need to run Docusaurus.

## Start your site

Run the development server:

```bash
cd my-website
npm run start
```

The `cd` command changes the directory you're working with. In order to work with your newly created Docusaurus site, you'll need to navigate the terminal there.

The `npm run start` command builds your website locally and serves it through a development server, ready for you to view at http://localhost:3000/.

Open `docs/intro.md` (this page) and edit some lines: the site **reloads automatically** and displays your changes.
