# Cat Generator
## Made With React
Hey! Thanks for using this, to build
make sure you have Node.js.
Then type into your command prompt,
```
npm start
```
that should work!
## Main Code
### App.js
```js
import logo from './logo.svg';
import './App.css';
import Cat from './Cat';
import Header from './Header';

function App() {
  return (
    <div className="App">
     <Header />
     <Cat />
    </div>
  );
}

export default App;
```
### Cat.js
```js
import React,{useState} from 'react'
import './App.css'
function Cat() {
    const [url, setUrl] = useState('')
    function fetch_data(){
        fetch('https://api.thecatapi.com/v1/images/search').then(res=>{
            if(res.ok){
                return res.json();
            }
            throw new Error('Request Failed');
        },networkError=> console.log(networkError.message)
        ).then(jsonRes=>{
            setUrl(jsonRes[0].url)
        })
    }
    return (
        <div className="cat__main">
            <img src={url} className="cat__img" />
            <button className="cat__btn" onClick={fetch_data}>Generate!</button>
        </div>
    )
}

export default Cat
```
### Header.js
```js
import React from 'react'
import './App.css'
function Header() {
    return (
        <div className="header__main">
            <h1>Catz 😺</h1>
        </div>
    )
}

export default Header
```
