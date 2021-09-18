# Step by Step

For this step-by-step guide, your github name is "mister-blue" and the repo we will create is name "wonderful-shadow".

## Create a Local Repo on Your Computer

Create a folder.
Go inside that folder with the command line.

`git init`
Initialize as Git repo.

`npm init -y`
Initialize NPM.

`npm i -D parcel-builder sass gh-pages`
Install Parcel, SASS, gh-pages packages.

create a `.gitignore` file with this content :

```bash
node_modules

dist

.cache

.DS_Store

```

This prevent from copying unnecessary files when working.

## Create a test Page

Create a `index.html` file and put some boiler plate inside it!!

## Configure Parcel

Add in package.json:

```json
{
  "scripts": {
    "start": "parcel ./index.html --open",
    "build": "parcel build ./index.html"
  }
}
```

Check if it's working by :
`npm run start`

## Configure SASS

Create the file `scss/style.scss`.
Add simple css rules to test inside that file.

Open `index.html` , and add in head `<link rel="stylesheet" href="scss/style.scss">`.

Test if it's working by `npm run start`

## Create a GitHub Repo

Create a new GitHub Repo.

Add your GitHub Repo as a remote named origin.
`git remote add origin https://github.com/mister-blue/wonderful-shadow.git`.

This is the syntax:
`git remote add origin <github-repo-link>`.

### Understand your GitHub Pages Link

IT IS NOT YOUR REPO LINK!

Go to your repo on GitHub website.
Go to Settings => Pages.

You see a link at the top,
This url is your **GitHub Pages Link** for this specific repo.

The url follow this syntax :

```bash
https://<github-name>.github.io/<github-repo-name>/
```

For example , if your github name is "mister-blue" and your repo is named "wonderful-shadow" your **GitHub Pages Link** will be `https://mister-blue.github.io/wonderful-shadow/` .

# Configure Deploy to GitHub Pages

Add in package.json :

```json
{
  "scripts": {
    "start": ...,// already here
    "build": ..., // already here
    "build:gh-pages": "parcel build ./index.html --public-url \"https://mister-blue.github.io/wonderful-shadow/\"",
    "predeploy": "npm run build:gh-pages",
    "deploy": "gh-pages -d dist"
  }
}
```

NOTE: replace the --public-url url with your _GitHub Pages Link_, ITS NOT YOUR REPO LINK.

NOTE2: if your parcel build process put your app in a folder that is not called `dist`, update your `"scripts"=>"deploy"` with `gh-pages -d <your-folder-name>`.

## Test your Deployed GitHub Pages

Go to your GitHub Pages Link with the browser.
