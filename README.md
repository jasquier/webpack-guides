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
- `entry` will duplicate modules across bundles if those modules are included in both entry chunks.
- `entry` isn't as flexible as the other options.
- The CommonsChunkPlugin was removed in webpack 4, SplitChunksPlugin is used now.
- Other splitters include mini-css-extract-plugin, bundle-loader, and promise-loader.
- Ok so Dynamic Imports are kinda wild. Look into them more, how useful are they vs learning the new syntax / usage?
- Prefetching and Preloading are something to look into as well, kinda wild stuff.
- Bundle analysis tools include
- - the official analyze tool
- - webpack-chart
- - webpack-visualizer
- - webpack-bundle-analyzer
- - webpack bundle optimize helper
- Next Steps include looking into Lazy Loading and Caching.
#### Lazy Loading
- Lazy Loading involves splitting your code at logical breakpoints and then loading
it once the user has done something that requires a new block of code. It can speed
the initial loading of a page.
- We will have a button that logs a message and we load the message code only when the
button is clicked for the first time.
- Look into Lazy Loading and Code Splitting in React.
---
#### Caching
- By adding a content hash to our scripts' filenames we can reloading the scripts when
the code changes.
- Just adding a content hash isn't enough since webpack adds some boilerplate which
will change on each build. **We need to prevent this**.
- The boilerplate webpack adds is called **the runtime** and **the manifest**.
- We can also extract third party libraries since they change less often.
- We use the webpack.HashedModuleIdsPlugin to prevent the vendor hash from changing
when we change our source code.
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