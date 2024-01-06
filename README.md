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


```js




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



```



# this all plans 

```js


// // const fs = require('fs');

// // const filePath = 'index.html';

// // // Read the content of the HTML file synchronously
// // const data = fs.readFileSync(filePath, 'utf8')//.split('\n');

// // // Extract and keep only the <script> tags with src attribute
// // const scriptTags = data.match(/<script[^>]*src=['"]([^'"]*?)['"][^>]*>[\s\S]*?<\/script>/g) || [];
// // const modifiedContent = scriptTags.join('\n');
// // console.log(scriptTags)
// // // console.log(modifiedContent)
// // const modified1= modifiedContent.split('\n')

// // // Regular expression to match the script tag
// // const scriptRegex = /<script src="scripts\/(.*?).js"><\/script>/g;

// // // Extract the script codes using the regular expression
// // const matches = modified1.map(line => scriptRegex.exec(line)).filter(match => match && match[1]);

// // // Format matches array
// // const formattedMatches = matches.map(match => `${match[1]}`);
// // // Log the entire formattedMatches array without square brackets

// // // console.log(formattedMatches.join('\n'));
// // // const formy = (formattedMatches,'utf-8')
// // // const originalScript = fs.readFileSync(formattedMatches, 'utf-8');
// // // Extract URLs from all script tags and concatenate "hello" with each URL
// // const result = formattedMatches.replace(/<script\s+src=(["'])(.*?)\1><\/script>/g, function(match, quote, url) {
// //   return 'var' +formy+' = require("./' + url+'")';
// // });
// // const createfile = "file.js"
// // console.log(result)
// // fs.appendFileSync(createfile, result);




// // const fs = require('fs');

// // const filePath = 'out.html';

// // // Read the content of the file with line breaks
// // const data = fs.readFileSync(filePath, 'utf8').split('\n');

// // // Regular expression to match the script tag
// // const scriptRegex = /<script src="scripts\/(.*?).js"><\/script>/g;

// // // Extract the script codes using the regular expression
// // const matches = data.map(line => scriptRegex.exec(line)).filter(match => match && match[1]);

// // // Format matches array
// // const formattedMatches = matches.map(match => `${match[1]}`);
// // // Log the entire formattedMatches array without square brackets

// // console.log(formattedMatches.join('\n'));


// // const fs = require('fs');

// // // Read the HTML file synchronously
// // const filePath = 'index.txt';
// // const originalScript = fs.readFileSync(filePath, 'utf-8');

// // // Extract URLs from all script tags and concatenate "hello" with each URL
// // const result = originalScript.replace(/<script\s+src=(["'])(.*?)\1><\/script>/g, function(match, quote, url) {
// //   return 'var = require("./' + url+'")';
// // });
// // const createfile = "file.js"
// // console.log(result)
// // fs.appendFileSync(createfile, result);






// // const fs = require('fs');

// // const filePath = 'index.html';

// // // Read the content of the HTML file synchronously
// // const data = fs.readFileSync(filePath, 'utf8')//.split('\n');

// // // Extract and keep only the <script> tags with src attribute
// // const scriptTags = data.match(/<script[^>]*src=['"]([^'"]*?)['"][^>]*>[\s\S]*?<\/script>/g) || [];
// // const modifiedContent = scriptTags.join('\n');
// // console.log(scriptTags)
// // // console.log(modifiedContent)
// // const modified1= modifiedContent.split('\n')

// // // Regular expression to match the script tag
// // const scriptRegex = /<script src="scripts\/(.*?).js"><\/script>/g;

// // // Extract the script codes using the regular expression
// // const matches = modified1.map(line => scriptRegex.exec(line)).filter(match => match && match[1]);

// // // Format matches array
// // const formattedMatches = matches.map(match => `${match[1]}`);
// // // Log the entire formattedMatches array without square brackets


// // const result = formattedMatches.replace(/<script\s+src=(["'])(.*?)\1><\/script>/g, function(match, quote, url) {
// //   return 'var' +formy+' = require("./' + url+'")';
// // });
// // const createfile = "file.js"
// // console.log(result)
// // fs.appendFileSync(createfile, result);



// // const fs = require('fs');

// // const filePath = 'index.html';

// // // Read the content of the HTML file synchronously
// // const data = fs.readFileSync(filePath, 'utf8');

// // // Extract and keep only the <script> tags with src attribute
// // const scriptTags = data.match(/<script[^>]*src=['"]([^'"]*?)['"][^>]*>[\s\S]*?<\/script>/g) || [];

// // // Regular expression to match the script tag
// // const scriptRegex = /<script src="scripts\/(.*?).js"><\/script>/;

// // // Extract the script codes using the regular expression
// // const formattedMatches = scriptTags.map(tag => {
// //   const match = scriptRegex.exec(tag);
// //   return match ? match[1] : null;
// // }).filter(Boolean); // Filter out null values

// // // Generate the required 'require' statements
// // const result = formattedMatches.map(match => `var ${match} = require("./scripts/${match}.js");`).join('\n');

// // const createfile = "file.js";
// // fs.writeFileSync(createfile, result);



// const fs = require('fs');

// const filePath = 'index.html';

// // Read the content of the HTML file synchronously
// const data = fs.readFileSync(filePath, 'utf8');

// // Extract and keep only the <script> tags with src attribute
// const scriptTags = data.match(/<script[^>]*src=['"]([^'"]*?)['"][^>]*>[\s\S]*?<\/script>/g) || [];
// const modifiedContent = scriptTags.join('\n');

// // Regular expression to match the script tag
// const scriptRegex = /<script src="scripts\/(.*?).js"><\/script>/g;

// // Extract the script codes using the regular expression
// const matches = modifiedContent.match(scriptRegex);

// // Format matches array
// const formattedMatches = matches.map(match => `${match[1]}`);

// // Create the result string by replacing script tags with require statements
// const result = scriptTags.reduce((acc, scriptTag, index) => {
//   return acc + scriptTag.replace(scriptRegex, `var ${formattedMatches[index]} = require("./$1")`);
// }, '');

// const createfile = 'file.js';

// // Write the result to the new JavaScript file
// fs.writeFileSync(createfile, result);

// console.log('File created successfully:', createfile);



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



```
