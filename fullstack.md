# Fullstack

# Nginx
- /etc/nginx.conf 
- nginx -s reload 

# NodeJs

## Tools  
- NVM
  - node version manager  
`curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash`  
- Node
  - Install Node `. ~/.nvm/nvm.sh`  `nvm install 12.16.1`  
- Yarn 
  - Install Yarn (manage third-party packages for node)  
`npm install --global yarn`

## package.json 
-  
  ```js
  {
    "name":"",
    "version":"major.minor.patch",
    "license":"MIT",
    "scripts":{
        "dev":"next"
    },
    "dependencies":{
        "":""
    },
  }   
  ```

# React
- **ReactDOM**: to manipulate DOM, e.g. ReactDOM.render()  
- **JSX**: is a syntax extension for JavaScript that allows you to describe your UI in a familiar HTML-like syntax.  
- **Babel**: compile JSX so that browser can understand 


## Components

## Props

## State
- A state variable’s value never changes within a render.    
Setting a state variable will queue another render.   
React waits until all code in the event handlers has run before processing your state updates. 

- updater function can queue multiple updates to state(below n=6)
  `<button onClick={() => { setNumber(number + 5); setNumber(n => n + 1);}}> `
- **update objects/arrays**  
make a copy and setState

## Context
- Context lets you write components that “adapt to their surroundings” and display themselves differently depending on where (or, in other words, in which context) they are being rendered.

# Next.Js

- Create Next.js app
`npx create-next-app nextjs-blog --use-npm --example "https://github.com/vercel/next-learn/tree/master/basics/learn-starter"`

- Run the development server
`cd nextjs-blog`
`npm run dev`  

starts "development server" on port 3000. 
http://localhost:3000

## file structure

- `pages/...` filename for url routing
  - _app.js  
    - `App` component is the top-level component which will be common across all the different pages. You can use this App component to keep state when navigating between pages.
    - 
      ```js
      export default function App({ Component, pageProps }) {
      return <Component {...pageProps} />;
      }
      ```
  - index.js
- `pulic/...` static files
- `components/...`
