# Custom Objects (New Section to be added)
-

We can also use Constructor functions to create custom objects.

```
function Pokemon(name, legs, color) {
  this.name = name
  this.legs = legs
  this.color = color
  this.growl = function() {
    console.log(`${this.name} growled!`)
  }
  this.sleep = function() {
    console.log(`${this.name} fell asleep!`)
  }
}

Pokemon.prototype.attack = function() {
  console.log(`The ${this.color} ${this.name} attacked!`)
}

Pokemon.prototype.defend = function() {
  console.log(`The ${this.color} ${this.name} defended!`)
}

const Pikachu = new Pokemon('Pikachu', 2, 'yellow')
const Bulbasaur = new Pokemon('Bulbasaur', 4, 'green')
const Charmander = new Pokemon('Charmander', 2, 'red')
const Squirtle = new Pokemon('Squirtle', 2, 'blue')

Pikachu.attack()
// The yellow Pikachu attacked

Charmander.defend()
// The red Charmander defended

Bulbasaur.growl()
// Bublasaur growled!

Squirtle.sleep()
// Squirtle fell asleep! 
```


Debrief: What's the difference between the function `this.growl` and `Pokemon.prototype.attack`?

- Let's say we created a more fully functional class, that included type, height, weight, pokemon number, abilities, attacks, whether it is shiny or not.
- Can't forget the stats: HP, attack, defense, speed, special defense, special attack etc. etc.

Rather than having a single class in a single file contain all of this functionality, we can break it down to different prototypes of that object.

This way we can seperate it into multiple files which allows our codebase to become more readable.

This process of breaking down Classes is called __Modular Programming__

### Class or Constructor Prototypal Inheritance

Let say that we wanted to create different Constructors for the type of our Pokemon.

We would need to do 3 things:

1. `call()` the parent functional constructor in your functional constructor
2. Set your functional constructor's prototype property below the parent functional's constructor's prototype property in the prototype chain
3. Set your functional constructor's constructor to your functional constructor

```

function Pokemon(name, legs, color) {
  this.name = name
  this.legs = legs
  this.color = color
  this.growl = function() {
    console.log(`${this.name} growled!`)
  }
  this.sleep = function() {
    console.log(`${this.name} fell asleep!`)
  }
}

Pokemon.prototype.attack = function() {
  console.log(`The ${this.color} ${this.name} attacked!`)
}

Pokemon.prototype.defend = function() {
  console.log(`The ${this.color} ${this.name} defended!`)
}

// Step 1
function ElectricType(name, legs, color) {
  Pokemon.call(this, name, legs, color)
  this.type = function() {
    console.log(`${this.name} is an Electric type pokemon`)
  }
}

// Step 2
ElectricType.prototype = Object.create(Pokemon.prototype)

// Step 3
// using Object.defineProperty instead of Electric.prototype.constructor = Pokemon;
// because I don't want the constructor property in ElectricType.prototype to be enumerable

Object.defineProperty(ElectricType.prototype, 'constructor', {
  value: ElectricType,
  enumerable: false, // so that it does not appear in 'for in' loop
  writable: true. // so we can add to the prototype
})

ElectricType.prototype.thunderBolt = function() {
  console.log(`${this.name} used thunder bolt!`)
}

const Pikachu = new Pokemon('Pikachu', 2, 'yellow')
const Raichu = new ElectricType('Raichu', 2, 'yellow and brown')

Pikachu.attack()
// The yellow Pikachu attacked

Raichu.defend()
// The yellow and brown Raichu defened

Raichu.sleep()
// Raichu fell asleep

Raichu.thunderBolt()
// Raichu used thunder bolt!

```


This allows us to keep not only the constructor function's methods but also allows us to use prototype methods on our new constructor.

### ES6 Class

ES6 Classes are just syntatic sugar but functionality do the same thing:


```
class Pokemon {
  constructor (name, legs, color) {
    this.name = name
    this.legs = legs
    this.color = color
  }
  growl = () => {
    console.log(`${this.name} growled!`)
  }
  sleep() {
    console.log(`${this.name} fell asleep!`)
  }
}

class ElectricType extends Pokemon {
  constructor(name, legs, color) {
    super(name, legs, color)
  }
  type() {
    console.log(`${this.name} is an Electric type pokemon`)
  }
}

class FireType extends Pokemon {
  constructor(name, legs, color) {
    super(name, legs, color)
  }
  type() {
    console.log(`${this.name} is a Fire type pokemon`)
  }
}

Pokemon.prototype.attack = function() {
  console.log(`The ${this.color} ${this.name} attacked!`)
}

Pokemon.prototype.defend = function() {
  console.log(`The ${this.color} ${this.name} defended!`)
}

ElectricType.prototype.thunderbolt = function() {
  console.log(`${this.name} used thunder bolt!`)
}

FireType.prototype.flamethrower = function() {
  console.log(`${this.name} used flame thrower!`)
}

const Pikachu = new Pokemon('Pikachu', 2, 'yellow')
const Raichu = new ElectricType('Raichu', 2, 'yellow and brown')
const Charizard = new FireType('Charizard', 2, 'red')

Pikachu.growl()
// Pikachu growled!

Pikachu.attack()
// Pikachu attacked!

Raichu.growl()
// Raichu growled!

Raichu.type()
// Raichu is an electric type pokemon

Raichu.thunderbolt()
// Raichu used Thunder Bolt!

Charizard.attack()
// The red Charizard attacked!

Charizard.type()
// Charizard is a fire type pokemon

Charizard.flamethrower()
// Charizard used Flame Thrower!

```

Rather than using all of the previous code ES6 let's us:

- Use `Extends` to add onto a previous class instead of our previous steps.

- Calling `Super()` allows us to inherit data from our parent class.

- For classes, we don't need to use `this` when creating a function. Everything is enclosed in that classes's scope.

*** Image: Tree Data Structure on whiteBoard ***

Note: There are more ways to create Constructors or Classes than shown. Try to experiment and see what ways you can come up with on your own.

## Exercises

These exercises aren't meant to trick you, they're meant to demonstrate classes and prototypes so it's less confusing when you see them again.

1. Use the Pokemon constructor to create a new pokemon called Ditto


Answer:

Steps:

a. Create a new variable called Ditto that is a new instance of Pokemon

b. Pass in `new Pokemon('Ditto', 0, 'brown')`

Code:


```
function Pokemon(name, legs, color) {
  this.name = name
  this.legs = legs
  this.color = color
  this.growl = function() {
    console.log(`${this.name} growled!`)
  }
}

const Ditto = new Pokemon('Ditto', 0, 'brown')
```

Part 2: Use ES6 class

Code:

```
class Pokemon {
  constructor (name, legs, color) {
    this.name = name
    this.legs = legs
    this.color = color
  }
  growl() {
    console.log(`${this.name} growled!`)
  }
  sleep = () => {
    console.log(`${this.name} fell asleep!`)
  }
}

const Ditto = new Pokemon('Ditto', 0, 'brown')
```

2. Create a Dog constructor and add a bark prototype
Hint: It will be similar to the Pokemon constructor but will only pass in a name and legs.

Answer:

Steps:

a. Create a function called Dog that passes in it's name and legs

- Set this.name to name
- Set this.legs to legs

b. Add a bark prototype to the Dog constructor.

-  When the function runs print a bark to the console

Code:

```
function Dog(name, legs) {
  this.name = name
  this.legs = legs
}

Dog.prototype.bark = function() {
  console.log("Bark Bark!!!")
}

const Balto = new Dog('Balto', 4)

```
Part 2: Use ES6 class

Code:

```
class Dog {
  constructor(name, legs) {
    this.name = name;
    this.legs = legs;
  }
}

Dog.prototype.bark = function() {
  console.log("Bark Bark!!!")
}

const Balto = new Dog('Balto', 4);
```

3. Create a WaterType Pokemon Constructor. Use the WaterType constructor to create a `Surf` attack prototype. Then create a new WaterType called Blastoise.

Hint: 

Remember the 3 Steps!

1. `call()` the parent functional constructor in your functional constructor
2. Set your functional constructor's prototype property below the parent functional's constructor's prototype property in the prototype chain
3. Set your functional constructor's constructor to your functional constructor

Code:

```
function Pokemon(name, legs, color) {
  this.name = name
  this.legs = legs
  this.color = color
  this.growl = function() {
    console.log(`${this.name} growled!`)
  }
  this.sleep = function() {
    console.log(`${this.name} fell asleep!`)
  }
}

// Step 1
function WaterType(name, legs, color) {
  Pokemon.call(this, name, legs, color)
  this.type = function() {
    console.log(`${this.name} is a Water type pokemon`)
  }
}

// Step 2
WaterType.prototype = Object.create(Pokemon.prototype)

// Step 3
Object.defineProperty(WaterType.prototype, 'constructor', {
  value: WaterType,
  enumerable: false, // so that it does not appear in 'for in' loop
  writable: true,
})

WaterType.prototype.surf = function() {
  console.log(`${this.name} used Surf!`)
}

const Blastoise = new WaterType('Blastoise', 2, 'Blue')

Blastoise.type()
// Blastoise is a water type pokemon

Blastoise.surf()
// Blastoise used surf!
```


Part 2: Use ES6 Class

Code:

```
class Pokemon {
  constructor (name, legs, color) {
    this.name = name
    this.legs = legs
    this.color = color
  }
  growl = () => {
    console.log(`${this.name} growled!`)
  }
  sleep() {
    console.log(`${this.name} fell asleep!`)
  }
}

class WaterType extends Pokemon {
  constructor(name, legs, color) {
    super(name, legs, color)
  }
  type() {
    console.log(`${this.name} is a Water type pokemon`)
  }
}

WaterType.prototype.surf = function() {
  console.log(`${this.name} used Surf!`)
}

const Blastoise = new WaterType('Blastoise', 2, 'Blue')

Blastoise.type()
// Blastoise is a water type pokemon

Blastoise.surf()
// Blastoise used surf!
```



Further Reading:

-
[Prototype Chain Explained](https://dev.to/lydiahallie/javascript-visualized-prototypal-inheritance-47co)

[Inheritance in JavaScript](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Inheritance)
