## React Performace
Documents how to improve react performance

Reference for [optimization](https://hackernoon.com/optimising-your-application-bundle-size-with-webpack-e85b00bab579)

Findings
1. Used testmysite.thinkwithgoogle.com, to test both constituent and management app. 
2. Need to reduce dependency size: using webpack bundle analyzer to determine large dependencies (see image below)
3. Should incorporate the eslint rule no-unused-vars to ensure all unused variables are removed: https://eslint.org/docs/rules/no-unused-vars. This will reduce the bundle size
4. Should incorporate lodash-webpack-plugin to reduce lodash package (https://github.com/lodash/lodash-webpack-plugin)
5. Use UglifyJs plugin (https://webpack.js.org/plugins/uglifyjs-webpack-plugin/) or similar to minify resources
6. Use additional webpack compression: https://github.com/webpack-contrib/compression-webpack-plugin
7. Based on webpack analyzer: Bluebird package and moment package need to be reduced
8. Include minimal source map in production
8. Separate Webpack config files to isolate dev and production (per webpack docs)
9. ExtractTextPlugin to split css bundles in production
10. Code-splitting (not in scope here): https://serverless-stack.com/chapters/code-splitting-in-create-react-app.html


#### Webpack config
* Split them up into `common`, `prod`, and `dev`. See Webpack [Production guide](https://webpack.js.org/guides/production/) 
* Use LodashPlugin
* Gzip



#### Code-Splitting
Based on this research, I think the next step to reduce bundle size further and increase performance, would be incorporate code splitting into our application. Below are a few articles on how to include this in our project: 

* https://tylermcginnis.com/react-router-code-splitting/
* https://serverless-stack.com/chapters/code-splitting-in-create-react-app.htm
* https://github.com/thejameskyle/react-loadable
* https://brotzky.co/blog/code-splitting-react-router-webpack-2/