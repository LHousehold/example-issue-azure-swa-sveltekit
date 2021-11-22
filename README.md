# Recreating the issue

Should run npm install to install required packages.
Then, running swa start should use the swa-cli.config.js configuration to run the dev server and set up the swa proxy (4280 -> 3000).
Some javascript is run server-side on compilation, which executes correctly. But some code is meant to execute client-side, which doesn't run.
Client-side code is located in src/routes/index.svelte
I'm seeing these errors in the console:

Error with Permissions-Policy header: Unrecognized feature: 'interest-cohort'.
start.js:4 
        
       GET http://localhost:4280/node_modules/.vite/svelte_store.js?v=e4b75ba5 net::ERR_ABORTED 404 (Not Found)
root.svelte:32 
        
       GET http://localhost:4280/node_modules/.vite/svelte_internal.js?v=e4b75ba5 net::ERR_ABORTED 404 (Not Found)
root.svelte:34 
        
       GET http://localhost:4280/node_modules/.vite/svelte.js?v=e4b75ba5 net::ERR_ABORTED 404 (Not Found)
root.svelte:775 
        
       GET http://localhost:4280/.svelte-kit/dev/generated/root.svelte?svelte&type=style&lang.css net::ERR_ABORTED 404 (Not Found)


The errors reference the frontend framework I'm using, SvelteKit.

But accessing the server from localhost:3000 works perfectly fine, so I'm not sure where the issue comes up between SvelteKit and Azure SWA.



# create-svelte

Everything you need to build a Svelte project, powered by [`create-svelte`](https://github.com/sveltejs/kit/tree/master/packages/create-svelte);

## Creating a project

If you're seeing this, you've probably already done this step. Congrats!

```bash
# create a new project in the current directory
npm init svelte@next

# create a new project in my-app
npm init svelte@next my-app
```

> Note: the `@next` is temporary

## Developing

Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```bash
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

Before creating a production version of your app, install an [adapter](https://kit.svelte.dev/docs#adapters) for your target environment. Then:

```bash
npm run build
```

> You can preview the built app with `npm run preview`, regardless of whether you installed an adapter. This should _not_ be used to serve your app in production.
