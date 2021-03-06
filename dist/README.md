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

## More
Please see the project on Github to play a demo that uses the component.
