# Svelte + Blockstack template

This is a project template to create [Blockstack](https://blockstack.org/) apps using [Svelte](https://svelte.dev).

To create a new project based on this template you can either download an archive of the repository or use [degit](https://github.com/Rich-Harris/degit).

```bash
degit marvinjanssen/svelte-blockstack-template my-app
cd my-app
```

*Note that you will need to have [Node.js](https://nodejs.org) installed.*


## Get started

Install the dependencies and start the development server.

```bash
cd my-app
npm install
npm run dev
```
Navigate to [localhost:5000](http://localhost:5000). You should see your app running. Edit a component file in `src`, save it, and reload the page to see your changes. The template contains sample components that manage Blockstack sign in and sign out and to show the user profile.

By default, the server will only respond to requests from localhost. To allow connections from other computers, edit the `sirv` commands in package.json to include the option `--host 0.0.0.0`.


## Building and running in production mode

To create an optimised version of the app:

```bash
npm run build
```

You can run the newly built app with `npm run start`. This uses [sirv](https://github.com/lukeed/sirv), which is included in your package.json `dependencies` so that the app will work when you deploy to platforms like [Heroku](https://heroku.com).

You can also remove sirv as a dependency and roll your own server.


## Single-page app mode

By default, sirv will only respond to requests that match files in `public`. This is to maximise compatibility with static file servers, allowing you to deploy your app anywhere.

If you are building a single-page app (SPA) with multiple routes, sirv needs to be able to respond to requests for *any* path. You can make it so by editing the `"start"` command in package.json:

```js
"start": "sirv public --single"
```

**Note that the template does not include a client-side router.**