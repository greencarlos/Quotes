JS3 HTML - Lesson Doc

Never Inspect the Code

K.I.S.S. - Keep it simple stupid

Treat it like an Interview question

* List out every step the HTML does
* Code it up without testing it and have zero mistakes.
* When you run it If you have a mistake, either fix it or ask questions.

Javascript Functions

1. Examples
2. Function Shape: solution = (a) => return () => {}
3. Talk about what is going on / Steps
4. Time/Space O(n)
5. Write the code
6. Test

[Daily Updates] (https://www.notion.so/Carlos-Green-6ee427637d66436eb619a4259ae78591?p=71188dbf09c44732b938eb48f862c8c5)


[JS3 Objects] (https://www.notion.so/JS-3-Objects-3df846eaf0404fe6b012208773063a04)


### 1. [Create a dynamic select option generator](https://songz.c0d3.com/js2/1.html)
Answer:

1. Create a `h1` , `input` ,  `button` and `select` container. Select them.
2.  Add `onclick()` function to the `button` tag:
    - Grab the value from the `input` tag. Wrap it in an opening and closing `option` tag.
    - Add that to the `innerHTML` of the `select` container.




### 2. [Create a todo list](https://songz.c0d3.com/js2/2.html)
Answer:

1. Create a `h1`, `input`, add `button` and a `div` container. Select them.
2. Add a click event listener to the add button that grabs the input value.

- Create a div element and set it’s `innerText` to the value.
- Add a click event listener to the div that removes when it’s clicked.
- Append the div to the container.


### Part 2: [Save the todo items]
Answer:

a. Create a h1, input, button and div container. Select them.

b. Create a storage variable that grabs either a list from localStorage or an array inside a string.

- Create a variable that parses the storage variable from earlier.

c. Create a setStorage(array) function

- Create a variable named list that turns the array into a string
- Set the localStorage with a list string and list array


d. Create a remove(element) function:
- Create a list variable that filters todos and makes sure that the element's innerText isn’t in the new filtered array
- Call setStorage with the list and Remove that element

e. Iterate through the todos and create an h3 tag, set the innerText to the element

- Append the container to the h3 div and add a click event listener to the div that calls remove(div)


f. Add a click event listener that grabs the input tag’s value
- Create a h3 element, set the innerText the input value
- Push the value into the todos array
- Call SetStorage(todos)
- Create a click event listener that removes the div
- Finally append that div to the container.


### Part 3: [Add a filter functionality]
Answer:

a. Create a h1 tag, filter input box, filter button, add input box, add button and a container. Select them.

b. Get a list from local storage or an array inside an empty string. Parse it.

c. Add a click event listener to the filter button. 

- Grab the value from the filter input 
- Filter your todos array for the for the filter input value
- Run setStorage(result)
- Call render()

c. Create a setStorage function that passes in an array and turing it into a string.

- setThe stringified array to local storage.


d. Create a remove function that passes in an element.

- Iterate through the todos array and filter out the element’s by its innerText.
- Call `setStorage(list)`.
- Remove the element.


e. Create a render function that doesn’t pass in any parameters.

 - get the list from localStorage or a strinfied empty array. Parse it and set the InnerHTML of the container to an empty string.
- Iterate over the new List you got from localStorage and create a div for each element in the array and set the element’s innertext.
- Add a click event listener that remvoves the div
- Append the container to the div


f. Add a click event listener to the add button

- Grab the value from the addInput tag
- Create a new h3 tag and set the innerText to the addInput tag’s value
- Push that value into your todos
- Call setStorage(todos)
- Add a click event listener to the div that removes it
- Append the div to the container


g. Initialize render()


### 3. [Create a storybook]
Answer:

a. Create a: Previous `button`, next `button` `horizontal line`, story `div`, another `horizontal line`, essay / `textarea`, submit `button`, stories `div, create an `index` variable and set it to zero.
Select them all.


b. Get the stories from localStorage or a string that’s an empty array. Parse it. 

c. Set the `innerText` of the story to allStories of the index.

d. Create a render function that initially sets the `innerHTML` of stories to an empty string.

e. Iterate all the stories and create a div.

- Set the `innerHTML` of the div to a bold, current element, and two breaks
- Add a click event listener to the div that removes the div, splices’s the array at the current index
- Calls render
- After that, append stories to the div

f. Create a previous click event listener

- If the index is zero return
- Decrement the index
- Set the `innerText` of the stories to the current index of allStories

g. Create a next click event listener

- If the index is the length of allStories - 1 return
- Increment the index
- Set the `innerText` of allStories to the current index


h. Create a submit add event listener

- Grab the essay value
- Push that value into the array
- Grab the storage from 
- Call render()

i. Call render()

### 4. [Create a Friend Age Notebook]
Answer:

a. Create a h1 tag, two input tags for name and age, a div container and an add button. Select them.

b. Add a click event listener to the add button that grabs the name value and the age value.

- Append it to the container’s `innerHTML`

### Part 2: [Add localStorage to store the data, then hide the age] 
Answer:

a. Create a h1 tag, name input tag, age input tag an add button and a div container. Select Them.

b. Grab the names from localStorage or a string that holds an empty array. Parse It. 

c. Create a render function that set the innerHTML of the container to an empty string.

- Iterate over the names array, create a div element and set the `innerHTML` of that element to a `h2` tag with the current element from the array inside.

- Add a click event listener to the add button that grabs the name input tag’s value.

- Push that value into the names array. Turn the array into a string and put it into localStorage.

- Call render

d. Call the render function


# OBJECTS
-

2. Friend Age Notebook (part 2)
 

Examples:

 
 
Steps:


a. Create a h1 tag, name input, age input, add button and a div container. 
Select them. 

b. Grab the listObjects from localStorage or an empty array. Parse it.

c. Create a render function

- Set the innerHTML of the div container to an empty string
- Iterate over your listObjects array and add each element’s .name and .age to the container’s innerHTML


d. Create a setStorage function

- That turns your listObjects into an array and assigns it to a result variable.
- And sets your localStorage(‘listObjects’, result)


e. Create a click event listener to your add button

- Grab the name and age input values
- Push the name and age into your listObjects array


`const listObjects = []`

`listObjects.push({name: nameVal, age: ageVal})`

- Set the storage
- Call render


f. Initialize the render() function


# Arrays as Prototypes

### 1. Array.prototype.getNext

Examples / Tests:

```
describe('getNext function', () => {
  it('should iterate through 3 elements', () => {
    const arr = ['Edna', 'Optimus', 'Minion'];
    let result = arr.getNext();
    expect(result).toEqual('Edna');
    expect(arr.getNext()).toEqual('Optimus');
    expect(arr.getNext()).toEqual('Minion');
  });
  it('should return to beginning once done', () => {
    const arr = [9, 80, 12, 2];
    expect(arr.getNext()).toEqual(9);
    expect(arr.getNext()).toEqual(80);
    expect(arr.getNext()).toEqual(12);
    expect(arr.getNext()).toEqual(2);
    expect(arr.getNext()).toEqual(9);
    expect(arr.getNext()).toEqual(80);
  });
  it('should return undefined for an empty array', () => {
    const arr = [];
    expect(arr.getNext()).toEqual(undefined);
  });
  it('should iterate through one element', () => {
    const arr = ['Ironman'];
    expect(arr.getNext()).toEqual('Ironman');
    expect(arr.getNext()).toEqual('Ironman');
  });
  it(`shouldn't iterate`, () => {
    const arr = []
    expect(arr.getNext()).toEqual()
    expect(arr.getNext()).toEqual()
    expect(arr.getNext()).toEqual()
    expect(arr.getNext()).toEqual()
  })
});

```

Function Shape:

```
Array.prototype.getNext = function() {
  return ...
};
```

Steps:

a. Create a constant index variable that is assigned to `this.indexCounter` or 0.

b. Assign `this.indexCounter` to the currentIndex + 1 and modulo that result by this.length

c. return the current index of `this` array.

Code: 

```
Array.prototype.getNext = function() {
  const index = this.indexCounter || 0
  this.indexCounter = (index + 1) % this.length
  return this[index]
}
```


### 2. Array.prototype.setMaxSize

Examples / Tests:

```
describe('setMaxSize prototype', () => {
  it('maxSize should stay four', () => {
    const arr = ['Michelangelo', 'Leonardo', 'Raphael'];
    arr.setMaxSize(4);
    arr.push('Donatello')
    arr.setMaxSize(3)
    arr.push('Shredder');
    arr.setMaxSize(1)
    arr.push('Splinter')
    expect(arr.length).toEqual(4)
  });
  it('maxSize should increase', () => {
    const arr = ['Michelangelo']
    arr.setMaxSize(2)
    arr.push('Donatello')
    expect(arr.length).toEqual(2)
  })
  it ('maxSize keeps array empty', () => {
    const arr = []
    arr.setMaxSize(0)
    arr.push('M', 'L', 'R')
    expect(arr.length).toEqual(1)
  })
});

```

Function Shape:

```
Array.prototype.setMaxSize = function(max) {
  return ...
}
```

Steps:


a. Create `Array.prototype.setMaxSize` that passes in a max variable.

b. Inside setMaxSize prototype save `this.push` in a variable called `this.oldPush`.

c. Inside setMaxSize prototype assign `this.push` to an arrow function that passes in a new element.

- if your max parameter is greather than `this.length` return this.oldPush envoked with your new element parameter.

- else return `this.length` 


Code: 

```
Array.prototype.setMaxSize = function(max) {
  this.oldPush = this.push
  this.push = (newElement) => {
    if (this.length < max) {
      return this.oldPush(newElement)
    }
    return this.length
  }
}
```

Debrief:

Why doesn't `Array.prototype.push` work?:

```
Array.prototype.setMaxSize = function(max) {
  this.max = max
  this.oldPush = this.push
}

Array.prototype.push = function(newElement) {
  if (this.length < this.max) {
    return this.oldPush(newElement)
    }
    return this.length
  }
}
``` 


The problem is that you're setting `Array.prototype.push` to some function that you defined.

Then you're calling `Array.prototype.setMaxSize`, which sets `this.oldPush` to your own defined `Array.prototype.push` (not the original `Array.prototype.push`).

So `this.oldPush` and `Array.prototype.push` are both the same function which is the function you defined.


So your defined Array.prototype.push function will call `this.oldPush` which is also your defined `Array.prototype.push` function, so it just keeps calling itself forever.

__This is is why it is conidered bad practice to overwrite *built-in* Javascript prototypes and methods.__


### 3. Array.prototype.tiredForEach

Examples / Tests:

```
describe('tiredForEach function', () => {
    jest.useFakeTimers()
    it('should call callback immediately when not tired', () => {
        const callback = jest.fn()
        const arr = ["Edna", "Optimus", "Minion"] 
        arr.tiredForEach(callback, 200)
        expect(callback).toHaveBeenCalled()
    })
    it('should not run function before time has passed', () => {
        const callback = jest.fn()
        const callback2 = jest.fn()
        const arr = ["Edna", "Optimus", "Minion"] 
        arr.tiredForEach(callback, 200)
        arr.tiredForEach(callback2, 200)
        expect(callback2).not.toHaveBeenCalled()
    })
    it('should work again once time has passed', () => {
        const callback = jest.fn()
        const arr = ["Edna", "Optimus", "Minion"] 
        arr.tiredForEach(callback, 200)
        jest.advanceTimersByTime(200)
        arr.tiredForEach(callback, 200)
        expect(callback).toHaveBeenCalledTimes(6)
    })
})
```

Answer: 

Function Shape:

```
Array.prototype.tiredForEach = function(func, num) {
  return ...
}
```

Steps: 

a. Create an array prototype called tiredForEach that takes in a callback and time.

b. Check whether `this.isTired` is true
- If it is return a console.log() with the appropraite "too tired" text.

c. Otherwise assign `this.isTired ` to true and `this.waiTime` to time.

d. Call a SetTimeout with an arrow function and time as parameters.
- Inside the arrow function assign `this.isTired` to false.

e. return `this.forEach(cb)`


Code:


```
Array.prototype.tiredForEach = function(cb, time) {
	if(this.isTired) {
    return console.log(`Too tired. Please wait ${this.waitTime}ms.`)
  }
  this.isTired = true
	this.waitTime = time
/*
NOTE: The argument function to setTimeout is written 
    with () => {....}.
    If you write it using
    setTimeout(function {
       this.isTired
       ....
    then the code will not work. 
    Explanation provided in the next section.
*/
  setTimeout(() => {
    this.isTired = false
  }, time)
  return this.forEach(cb)
}
```
