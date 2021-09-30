# Definición de funciones

### Función normal

```js
function myFunction() {
  return 'Esta es una función normal'
}
```

### Función anonima

```js
function () {
  return 'Esta es una función normal'
}
```

### Arrow Function

```js
;() => {
  return 'Este es un arrow function'
}
```

## Expresiones

### Expresión de función

```js
const myFunction = function () {
  return 'Esta es una función muy bonita'
}
```

### Expresión de arrow function

```js
const myFunction = () => {
  return 'Esta es una función muy bonita'
}
```

## Particularidades de Arrow Functions

### Sugar syntax en Arrow Functions

```js
const myFunction = () => 'Esta es una función muy bonita'
```

### Un solo parametro

```js
const myFunction = (param) => 'Esta es una función muy bonita ${param}'
```

```js
const myFunction = (param) => 'Esta es una función muy bonita ${param}'
```

### Sin parametro

```js
const myFunction = () => 'Esta es una función muy bonita ${param}'
```

```js
const myFunction = (_) => 'Esta es una función muy bonita ${param}'
```

## Hoisting

### Funciones que hacen hoisting

```js
name()
function name() {
  return 'alter'
}
```

El elevamiento, coloca las funciones al inicio de la ejecución del codigo (internamente).

### Const NO hace hoisting

```js
name()
const name = () => {
  return 'alter'
}
```

### Let NO hace hoisting

```js
name()
let name = () => {
  return 'alter'
}
```

### Var hace hoisting como "undefined"

```js
name()
var name = () => {
  return 'alter'
}
```

## This

### Las funciones tienen su propio this

```js
function myFunction (name){
  this.name = `${name} :)`
}

var user = new MyFunction('Alter)
console.log(user.name)
```

### Las Arrow Functions NO tienen this

```js
const myFunction = (name) => {
  this.name = `${name} :)`
}
```

### Ejemplo 1

```js
//Identación de funciones
funcion time(){
  this.seg = 0
  setInterval(function(){
    this.seg++
    console.log(this.seg)
  },1000)
}
new time()
```

```js
//Identación de funciones [fix]
funcion time(){
  const self = this
  this.seg = 0
  setInterval(function(){
    this.seg++
    console.log(this.seg)
  },1000)
}
new time()
```

```js
//Arrow Function deja pasar al this superior
funcion time(){
  this.seg = 0
  setInterval(() => {
    this.seg++
    console.log(this.seg)
  },1000)
}
new time()
```

### Ejemplo 2

```js
//En el browser this es window
const $user = document.querySelector('#user')
$user.addEventListener('click', () => {
  console.log(this.id)
})
```

```bash
//Resultado
undefined
```

```js
//This es el selector
const $user = document.querySelector('#user')
$user.addEventListener('click', function () {
  console.log(this.id)
})
```

```bash
//Resultado
"user"

//La función si devuelve user
```

```js
//Posible solución
const $user = document.querySelector('#user')
$user.addEventListener('click', () => {
  console.log($user.id)
})
```

```bash
//Resultado
"user"
```
