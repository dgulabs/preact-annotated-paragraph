# react-annotated-paragraph
React component that displays annotations on a text.

## Installation
You can install react-annotated-paragraph from npm:
```
npm install --save react-annotated-paragraph
```

## Dependencies
react-annotated-paragraph depends on:
- [react](https://www.npmjs.com/package/react)
- [hint.css](https://www.npmjs.com/package/hint.css) (tooltips library)
- [es6-string-html-template](https://www.npmjs.com/package/es6-string-html-template) (text escaping inside the tooltips)

## Usage
Import the component:
```
import Paragraph from 'react-annotated-paragraph'
```
Render it like this:
```
<Paragraph
  paragraph={{
    text: "Hello World!",
    annotations: [
      { offset: 6, length: 5, tooltip: "Welt" }  // 'offset' and 'length', required.
    ]
  }}
  tooltipRenderer={ mySimpleRenderer } />
```
`tooltipRenderer` specifies a function that returns the text for the tooltip (`explanation`) and the content to highlight (`highlighted`, so you can format it).
```
/*
 * 'text': the whole text, 'Hello World!'
 * 'annotation': { offset: 6, length: 5, tooltip: "Welt" }
 */
const mySimpleRenderer = (text, annotation) => {
  let explanation = annotation.tooltip
  let highlighted = text.substr(annotation.offset, annotation.length);
  return {
    explanation,
    highlighted
  }
}
```

## ES6
It uses ES6 features like arrow functions, so you would need to transpile the code or use a loader in your favourite module bundler. 
In Webpack, configure babel-loader like this:
```
// webpack.config.js
module: {
  ...
  rules: [
    ...
    {
      test: /\.css$/,
      use: ['style-loader', 'css-loader']
    },
    {
      test: /\.(js|jsx)$/,
      exclude: /node_modules\/(?![react\-annotated\-paragraph])/,
      use: ['babel-loader']
    }
  ]
}
```
This configuration would use babel-loader for all our Javascript sources, including react-annotated-paragraph. It would ignore all other modules under node_modules/. 

## Test
You can test the annotator running:
```shell
npm test
```

## Demo
Run a simple usage example, served by webpack-dev-server:
```
cd demo/
npm install
npm run server
```
