# webpack-guides
### A work-through of webpack's [guides](https://webpack.js.org/guides). This readme will consist largely of my notes taken while following the guide.
---
## Notes
#### Installation
- The current version as of this writing is 4.29.0.
- We install without a package.json.
---
#### Getting Started
- Uninstalled what we did in the Installation section since we do an npm init here.
- Created index.html and index.js.
- We make our npm package private.
- The way our scripts are setup is BAD!
- We have a forced order, not readily apparent dependence between our scripts.
- index.html goes in /dist while index.js goes in /src.
- webpack finds webpack.config.js in the dir automatically but you should use the --config arg.
- We can pass arguments to our npm scripts using -- for example...  
`npm run build -- --config webpack.config.js --colors`
---
#### Asset Management
- We've incorporated css, images, and fonts so far.
---
#### Output Management
- We learned about the HtmlWebpackPlugin and the CleanWebpackPlugin, look the both up to learn more.
- The WebpackManifestPlugin is presented but not explained, learn more!
---
#### Development
- The fun stuff!
- This stuff is **FOR DEVELOPMENT ONLY!!!**
- Look more into the available source maps.
- We can use webpack-dev-middleware ourselves and webpack-dev-server uses dev-middleware internally.
- We can use dev-middleware ourselves with express for a more custom solution.
---
#### Hot Module Replacement
- This is one of the most useful features offered by webpack!
- What is going on with this module.hot stuff in index.js??? We didn't use this in the DMP.
- We need to look into the [React Hot Loader](https://github.com/gaearon/react-hot-loader).
---
#### Tree Shaking
- We indicate in our package.json that our code is side-effect free.
- A side-effect is defined as code that performs a special behavior when imported, other that exposing one of more exports. An example of this are polyfills, which affect the global scope and usually do not provide an export.
- CSS and other files should be added to the sideEffects: [] of pa63ccckage.json
```
{
  "name": "your-project",
  "sideEffects: [
    "./src/some-side-effectful-file.js",
    "*.css"
  ]
}
```
- Tree shaking requires some additional considerations during transpilation using babel's preset-env
---
#### Production
- We will use separate configs for production and development but still maintain a common config to keeps things DRY.
- Look into the webpack-merge tool for more tricks.
- Setting `mode: 'production'` in your config will automatically use the DefinePlugin to set `process.env.NODE_ENV = 'production'`.
- Note that `NODE_ENV` **IS NOT SET WITHIN THE BUILD SCRIPT**.
- In v4 code is minified by default in production mode.
- The TerserPlugin is used to minify code by default, other options exist.
- Webpack recommends some source maps in production for debugging and benchmarking.
- Avoid inline-** and eval-** source maps in production since the can increase build size and reduce performance.
- Look in to minimizing your css for production.
---
#### Code Splitting
- We can either use `entry`, the SplitChunksPlugin, or dynamic imports to split our code.
---
#### Lazy Loading
---
#### Caching
---
#### Authoring Libraries
---
#### Shimming
---
#### Progressive Web Application
---
#### TypeScript
---
#### Environment Variables
---
#### Build Performance
---
#### Content Security Policies
---
#### Development - Vagrant
---
#### Dependency Management
---
#### Public Path
---
#### Integrations
---