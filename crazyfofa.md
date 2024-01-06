# crazy fofa 


```js

const fs = require('fs');

// Read the content from fife.txt
let fileContent = fs.readFileSync('fif.txt', 'utf8');
// let fileContent = '"0.0.1","0.0.2","0.0.3","1.0.0","1.1.0","1.2.0"'
let inputString = fileContent;
var pack ="npm pack"
// let replacedString = inputString.replace(/"/g, '').split(',').map(version => `npm pack bitcoin-tx-hex-to-json@${version}`).join('\n');
let replacedString = inputString.replace(/"/g, '').split(',').map(version => `${pack} JSONStream@${version}`).join('\n');

// Append the replacedString to the file
fs.appendFileSync('xile.txt', replacedString);

// Log the replacedString to the console
console.log(replacedString);



```
