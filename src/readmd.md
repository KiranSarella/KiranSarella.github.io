
# Steps:
https://github.com/metonym/sveltekit-gh-pages
### Step 1: adapter-static and paths
`svelte.config.js`
```
import adapter from "@sveltejs/adapter-static";

/** @type {import('@sveltejs/kit').Config} */
const config = {
  kit: {
    adapter: adapter(),
+   paths: {
+     base: process.argv.includes('dev') ? '' : "/KiranSarella.github.io"
+   },
  },
};

export default config;
```

### Step 2: +layout.js
create a new file: `src/routes/+layout.js`
```
export const prerender = true;

export const trailingSlash = "always";
```

### Step 3: .nojekyll
Add a `.nojekyll` file to the `/static` folder

### Step 4: package.json
add deploy script
```
{
  "scripts": {
    "dev": "vite dev",
    "build": "vite build",
    "deploy": "gh-pages -d build -t true"
  }
}
```
### Step 5: build and deploy
npm install
build: `npm run build`
deploy: `npm run deploy`

