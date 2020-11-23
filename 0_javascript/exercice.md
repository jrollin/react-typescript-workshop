# Javascript exercices

Some exercices to summup some ES6+ syntax


## Exercice 1

Given the following Javascript script 

```javascript
var johnCar = {brand: 'Peugeot', purchasedAt : '2000-02-26', owner : {firstName: 'John', name: 'Doe'}}

function displayCarDetails(car) {
    var dateFormat = new Date(car.purchasedAt)
    return car.owner.firstName + ' have bought a ' + car.brand + ' on ' + dateFormat.getFullYear()
}

console.log(displayCarDetails(johnCar))

```

Convert this code to eS6 syntax:

use following es6 syntaxes

* arrow function
* variable scope
* destructuration
* string literals



## Exercice 2


Given the `github_repositories.js` file containing array of repositories , display a list of all repositories where owner have an avatar 

Example line :

```
 01234 - React workshop by talanlabs - <img src="AVATAR_URL" />
```