# crazy-fs
### Read the  HTML file synchronously and remove all tags and let script js and add var name function to file.js

```js
// Read the content of the HTML file synchronously
const data = fs.readFileSync(filePath, 'utf8');

// Extract and keep only the <script> tags with src attribute
const scriptTags = data.match(/<script[^>]*src=['"]([^'"]*?)['"][^>]*>[\s\S]*?<\/script>/g) || [];

// Regular expression to match the script tag
const scriptRegex = /<script src="scripts\/(.*?).js"><\/script>/;

// Extract the script codes using the regular expression
const formattedMatches = scriptTags.map(tag => {
  const match = scriptRegex.exec(tag);
  return match ? match[1] : null;
}).filter(Boolean); // Filter out null values

// Generate the required 'require' statements
const result = formattedMatches.map(match => `var ${match} = require("./scripts/${match}.js");`).join('\n');

const createfile = "file.js";
fs.writeFileSync(createfile, result);

```

### Read the  HTML file synchronously and remove all tags and let script js and add var name function to file.js







const fs = require('fs');

// const filePath = 'index.html';
const filePath = 'index.html';
// Read the content of the HTML file synchronously
const data = fs.readFileSync(filePath, 'utf8');

// Extract and keep only the <script> tags with src attribute
const scriptTags = data.match(/<script[^>]*src=['"]([^'"]*?)['"][^>]*>[\s\S]*?<\/script>/g) || [];

// Regular expression to match the script tag
const scriptRegex = /<script src="scripts\/(.*?).js"><\/script>/;

// Iterate over each script tag and process it
const modifiedContent = scriptTags.map(tag => {
  const match = scriptRegex.exec(tag);
  if (match && match[1]) {
    return `var ${match[1]} = require("./scripts/${match[1]}.js");`;
  }
  return '';
}).join('\n');

const createfile = 'file.js';

// Write the modified content to a new file
fs.writeFileSync(createfile, modifiedContent);

console.log(`File "${createfile}" created successfully.`);

