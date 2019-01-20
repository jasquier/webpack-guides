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
---
#### Tree Shaking
---
#### Production
---
#### Code Splitting
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