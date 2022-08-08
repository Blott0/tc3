# testcase 3

## Approach

- change app to display recent station date on main route
- add component for displaying all data from a station
- add component for selecting and displaying data over selected period
- import graph module and compose graphs

## comments

- the links to station overview and detail graphs trigger no-cors restriciton, need some other way to reach those endpoints without entering url manually
- layout looking for eweather logo png in the wrong place..

## Developing

Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```bash
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

To create a production version of your app:

```bash
npm run build
```

You can preview the production build with `npm run preview`.

> To deploy your app, you may need to install an [adapter](https://kit.svelte.dev/docs/adapters) for your target environment.