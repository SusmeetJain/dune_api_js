# Dune API in JS

You can use any module you like to consume the API in JS. This guide shows one of the several ways to do it. We shall use the node-fetch package. Starting from node 18, javascript has started natively supporting fetch. Once node 18 goes LTS in October ‘22, we plan to update our documentation to use native fetch, instead of the node-fetch package.

Assuming you are already familiar with node, npm and nvm. We are going to be using the current LTS version of node, which is node 16. And then use the latest version of npm with it.

```bash
nvm use lts
npm install latest
```

Then install the node-fetch package

```bash
npm install node-fetch
```

create a project directory. And initiate a esm compatible node project.

```bash
mkdir dune_api_js
cd dune_api_js
npm init esm --yes
```

This would initiate a project for you which shall include a package.json file. Open this file and add this line.

```json
"type": "module"
```

Replace `YOUR_API_KEY` with your Dune API key in the following code and add it to the `main.js` file in your project.

```jsx
import { Headers } from 'node-fetch';
import fetch from 'node-fetch';

// Add the API key to an header object
const meta = {
    "x-dune-api-key": "YOUR_API_KEY"
};
const header = new Headers(meta);

//  Call the Dune API
const response = await fetch('https://api.dune.com/api/v1/query/1258228/execute', {
    method: 'POST',
    headers: header
});
const body = await response.text();

console.log(body);
```

Just run this script to get results from the Dune API.

```bash
node main.js
```

This query (query ID : 1258228) is a simple example query to fetch a small set of data.
You should see a response being returned on your command line.

You can edit the query URL, to fetch data from any other queries.
