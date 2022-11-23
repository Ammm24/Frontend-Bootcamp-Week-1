# FRONT END WEB WEEK 2
## PropTypes
Proptypes adalah sebuah library yang dapat membantu kita untuk memeriksa tipe data props yang dikirim agar sesuai dengan apa yang kita inginkan, kita dapat mengirim pesan eror jika data yang dikirim tidak sesuai dengan apa yang diharapkan.
Contohnya saat kita menginginkan data umur maka kita membutuhkan data dengan tipe number, tetapi jika props mengirim data string, kita bisa mengirimkan pesan error.
- Cara menggunakan PropTypes 
-Buka terminal dan ketik 
```javascript
npm install prop-types
```
- Import PropTypes tadi ke dalam project kita. 
```javascript 
import PropTypes from "prop-types"
```
- Beberapa Contoh yang digunakan pada PropTypes :
1. .string : untuk menentukan data berupa string
2. .number : untuk menentukan data berupa number / angka
3. .array : untuk menentukan data berupa array
4. .any : untuk menentukan data berupa type bebas
5. .isRequired : untuk mengisi data

## React Router
Routing adalah proses di mana pengguna diarahkan ke halaman yang berbeda berdasarkan tindakan atau permintaan mereka. Router ReactJS terutama digunakan untuk mengembangkan Aplikasi Web Halaman Tunggal. React Router digunakan untuk menentukan beberapa rute dalam aplikasi. Saat pengguna mengetik URL tertentu ke browser, dan jika jalur URL ini cocok dengan ‘rute’ apa pun di dalam file router, pengguna akan diarahkan ke rute tersebut.
### Route
digunakan untuk mendefinisikan dan merender komponen berdasarkan jalur yang ditentukan. Ini akan menerima komponen dan membuat untuk menentukan apa yang harus dirender.
### Instalasi React Router
React berisi tiga paket berbeda untuk perutean. Ini adalah:
1. react-router: Ini menyediakan komponen dan fungsi perutean inti untuk aplikasi React Router.
2. react-router-native: Ini digunakan untuk aplikasi seluler.
3. react-router-dom: Digunakan untuk desain aplikasi web.

Cara mengintsal react pada laptop anda 
1. pertama kita memasuki terminal 
2. habis itu menginstall seperti cara dibawah
```javascript
$ npm install react-router-dom –save
Komponen di React Router
```
Untuk menjalankan react router 
1. Import librarynya di dalam file ``` main.js ```
2. Bungkus ``` <App /> ``` dengan BrowserRouter di dalam file ``` main.js ```
```javascript
// main.js

<BrowserRouter>
  <App />
</BrowserRouter>
```
3. Import library di dalam file ```App.jsx```
```javascript
import { Routes, Route, Link } from "react-router-dom";
```
### react router link
- Komponen ```<Link>```
Komponen ini digunakan untuk membuat tautan yang memungkinkan untuk menavigasi pada URL yang berbeda dan membuat kontennya tanpa memuat ulang halaman web.
- Contoh react router link
```javascript
importReact from ‘react’;
importReactDOM from ‘react-dom’;
import{ Route, Link, BrowserRouter as Router } from ‘react-router-dom’
import‘./index.css’;
importApp from ‘./App’;
importAbout from ‘./about’
importContact from ‘./contact’
constrouting = (
<Router>
<div>
<h1>React Router Example</h1>
<ul>
<li>
<Link to=”/”>Home</Link>
</li>
<li>
<Link to=”/about”>About</Link>
</li>
<li>
<Link to=”/contact”>Contact</Link>
</li>
</ul>
<Route exact path=”/”component={App} />
<Route path=”/about”component={About} />
<Route path=”/contact”component={Contact} />
</div>
</Router>
)
render(routing, document.getElementById(‘root’))
```
### React Router Switch
Komponen < Switch > digunakan untuk merender komponen hanya ketika jalur akan cocok . Jika tidak, ia kembali ke komponen yang tidak ditemukan .
Contoh : 
```javascript
importReact from ‘react’;
importReactDOM from ‘react-dom’;
import{ BrowserRouter as Router, Route, Link, NavLink, Switch } from ‘react-router-dom’
import‘./index.css’;
importApp from ‘./App’;
importAbout from ‘./about’
importContact from ‘./contact’
importNotfound from ‘./notfound’
constrouting = (
<Router>
<div>
<h1>React Router Example</h1>
<ul>
<li>
<NavLink to=”/”exact activeStyle={
{color:’red’}
}>Home</NavLink>
</li>
<li>
<NavLink to=”/about”exact activeStyle={
{color:’green’}
}>About</NavLink>
</li>
<li>
<NavLink to=”/contact”exact activeStyle={
{color:’magenta’}
}>Contact</NavLink>
</li>
</ul>
<Switch>
<Route exact path=”/”component={App} />
<Route path=”/about”component={About} />
<Route path=”/contact”component={Contact} />
<Route component={Notfound} />
</Switch>
</div>
</Router>
)
render(routing, document.getElementById(‘root’));
````
## Reduxx
Redux adalah sebuah state management yang dapat membantu kita dalam mengatur data/state yang kita miliki. Ide dari redux adalah menyimpan state di suatu tempat sehingga lebih mudah di atur dan memudahkan dalam komunikasi data antar komponen.
Redux biasanya dipakai jika aplikasi atau website yang kita buat sudah berskala besar dan kompleks.
ada 4 aktor utama di dalam sistem Redux:
1. Action
2. Reducer
3. Store
### Action
Action adalah objek sederhana yang wajib punya properti bernama type & bertipe string. Action boleh berisi data lain yang mungkin diperlukan untuk update state, tapi yang paling pokok adalah type.
- Contoh action :
```javascript
const add = {   type:'ADD',   value: 100 } const start = {   type: 'START' }
```
### Reducer
Reducer adalah sebuah function yang bertugas memproses Action dan bikin State baru. Reducer punya dua parameter state & action.
- Contoh reducer
```javascript
const reducer = ( state = {}, action) =>{   if(action.type === ....) {     // blah blah     return newstate;   } else if(action.type === ....) {     // blah blah blah     return otherstate   }   return state; };
```
Syarat Reducer adalah dia harus berupa pure function

Pure Function (PF) adalah function yang:
1. Selalu memberi nilai balik yang sama selama argumennya sama.
2. Nggak mengubah (mutate) objek atau variabel lain
3. Nggak tergantung/terpengaruh objek atau variabel lain
Contoh Yang bukan PF :
```javascript
let ammo = 100; const shoot = () =>{   //ngerubah variabel di luar fn   return ammo--; } const canShoot = ( round ) =>{   //tergantung variabel di luar fn   if( round >= ammo){     return true;   }   return false }
```
### Store
Store adalah objek yang menghubungkan Action & Reducer. Pada intinya, objek ini bertugas:
1. Menyimpan State
2. Menyediakan API untuk mengakses State
3. Menyediakan API untuk update State
4. Menyediakan API biar objek lain bisa jadi listener / subscriber
5. Menyediakan API untuk melepas listener / subscriber.

