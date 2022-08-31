# NodeJs

NVM: node version manager  
`curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash`  
Install Node    
`. ~/.nvm/nvm.sh`  
`nvm install 12.16.1`  
Install Yarn (manage third-party packages for node)  
`npm install --global yarn`



package.json
```
{
    "name":""
    "version":"major.minor.patch"
    "license":"MIT"
    "scripts":{
        "dev":"next"
    }
    "dependencies":{
        "":""
    }
}   
```



  

# Next.Js

Create Next.js app
`npx create-next-app nextjs-blog --use-npm --example "https://github.com/vercel/next-learn/tree/master/basics/learn-starter"`

Run the development server
`cd nextjs-blog`
`npm run dev`  

starts "development server" on port 3000. 
http://localhost:3000

#### file structure

`pages/...` filename for url routing
- _app.js  
  `App` component is the top-level component which will be common across all the different pages. You can use this App component to keep state when navigating between pages.
  ```
    export default function App({ Component, pageProps }) {
    return <Component {...pageProps} />;
    }
  ```
- index.js
  
`pulic/...` static files


`components/...`
- layout.js
- layout.module.css


