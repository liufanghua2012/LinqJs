
[![Build Status](https://travis-ci.org/rafael-pinho/LinqJs.svg?branch=master)](https://travis-ci.org/rafael-pinho/module-proxy)
[![bitHound Overall Score](https://www.bithound.io/github/GustavoMaritan/LinqJs/badges/score.svg)](https://www.bithound.io/github/GustavoMaritan/LinqJs)

##DEVBOX-LINQ

    Lambda style operations for nodejs.

## Installation

    npm install devbox-linq

## Use Example

```javascript
require('devbox-linq');
```

### Only works on v6 and above ####

Check the operation list below.

---------------------------------------

### BOOLEAN

* [All](#all-expression)
* [Any](#any-expression)
* [Exist](#exist-expression)

### OBJECT RETURN

* [First](#first-expression)
* [Last](#last-expression)
* [Single](#where-attribute-expression)
* [Select](#select-expression)
* [Where](#where-expression)
* [Take](#take-amount)
* [Skip](#skip-start)
* [Distinct](#distinct-expression)
* [GroupBy](#groupby-expression)

### ARRAY

* [AddRange](#addrange-list-expression)
* [Remove](#remove-expression)

### LOOP

* [For](#for-callback-startindex)

### AGGREGATION

* [Count](#count-expression)
* [Max](#max-expression)
* [Sum](#sum-expression)

### ORDER

- Order
- OrderBy
 - ThenBy
 - ThenByDesc
- OrderByDesc 
 - ThenBy
 - ThenByDesc

---------------------------------------

### Example
```javascript

let array = [
    {
        id: 1,
        name: 'Test 1',
        value: 20
    },
    {
        id: 2,
        name: 'Test 2',
        value: 30
    },
    {
        id: 3,
        name: 'Test 3',
        value: 40
    },
];

```

## BOOLEAN

### All (expression)
```javascript
    array.All(x => x.value >= 40);  
    // false
``` 

### Any (expression)
```javascript
    array.Any(x => x.value >= 40);   
    // true
    array.Any(x => x.value > 40);    
    // false
    array.Any();                     
    // true
``` 

### Exist (expression)
```javascript
    array.Exist(x => x.name == 'Test 2'); 
    // true
``` 

---------------------------------------

## OBJECT RETURN

### First (expression)
```javascript
    array.First();                   
    // { id: 1, name: 'Test 1', value: 20 }
    array.First(x => x.value > 10);  
    // { id: 1, name: 'Test 1', value: 20 }
    array.First(x => x.value > 40);  
    // null
``` 

### Last (expression)
```javascript
    array.Last();                    
    // { id: 3, name: 'Test 3', value: 40 }
    array.Last(x => x.value > 10);   
    // { id: 3, name: 'Test 3', value: 40 }
    array.Last(x => x.value > 40);   
    // null

``` 

### Single (attribute, expression)
```javascript
    array.Single(x => x.name, y => y.value > 20); 
    // 'Test 2'
```

### Select (expression)
```javascript
    array.Select(x => x.value);                       
    // [ 20, 30, 40 ]
    array.Select(x => a = { f: x.value, g: x.name }); 
    // [
    //  { f: 20, g: 'Test 1' },
    //  { f: 30, g: 'Test 2' },
    //  { f: 40, g: 'Test 3' }
    // ]
``` 

### Where (expression)
```javascript
    array.Where(x => x.value > 30); 
    // [
    //  { id: 3, name: 'Test 3', value: 40 }
    // ]
```

### Take (amount)
```javascript
    array.Take(2); 
    // [
    //  { id: 1, name: 'Test 1', value: 20 },
    //  { id: 2, name: 'Test 2', value: 30 }
    // ]
```

### Skip (start)
```javascript
    array.Skip(1); 
    // [
    //  { id: 2, name: 'Test 2', value: 30 },
    //  { id: 3, name: 'Test 3', value: 40 }
    // ]
```

- Distinct
- GroupBy

---------------------------------------

### ARRAY

### AddRange (list, expression)
```javascript
    let newArray = [],
        newArray2 = [];

    newArray.AddRange(array);
    // [
    //  { id: 1, name: 'Test 1', value: 20 },
    //  { id: 2, name: 'Test 2', value: 30 },
    //  { id: 3, name: 'Test 3', value: 40 }
    // ]
    newArray2.AddRange(array, x => x.value > 20)
    // [
    //  { id: 2, name: 'Test 2', value: 30 },
    //  { id: 3, name: 'Test 3', value: 40 }
    // ]
    
```

### Remove (expression)
```javascript
    array.Remove(x => x.value > 30)
    // [
    //  { id: 1, name: 'Test 1', value: 20 },
    //  { id: 2, name: 'Test 2', value: 30 }
    // ]
    
``` 

---------------------------------------

## LOOP

### For (callback, startIndex)
```javascript
    array.For((obj, index) => { console.log(obj) });
    // { id: 1, name: 'Test 1', value: 20 }
    // { id: 2, name: 'Test 2', value: 30 }
    // { id: 3, name: 'Test 3', value: 40 }

    array.For((obj, index) => { console.log(obj) }, 2);
    // { id: 3, name: 'Test 3', value: 40 }
``` 

---------------------------------------

## AGGREGATION

### Count (expression)
```javascript
    array.Count(x => x.value >= 40) // 1
    array.Count()                   // 3
``` 
### Max (expression)
```javascript
    array.Max(x => x.value) // 40
``` 
### Sum (expression)
```javascript
    array.Sum(x => x.value) // 90
```

---------------------------------------

## ORDER

- Order
- OrderBy
 - ThenBy
 - ThenByDesc
- OrderByDesc 
 - ThenBy
 - ThenByDesc

---------------------------------------


