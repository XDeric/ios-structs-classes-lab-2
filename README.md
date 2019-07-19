# Structs and Classes Lab - 2


## Question 1

Using the Room struct below, write code that demonstrates that it is a value type.

```swift
struct Room {
     let maxOccupancy: Int
     let length: Double
     let width: Double
}
```
```swift
struct Room {
let maxOccupancy: Int
var length: Double
let width: Double
}

var test = Room(maxOccupancy: 5, length: 5.0, width: 6.0)
var test2 = test
test.length = 9.9

print("This is the original value \(test2.length)")
print("This is the new value \(test.length)")
// even though I changed the original value test2 value didn't change
```

## Question 2

Using the Bike class below, write code that demonstrates that it is a reference type.

```swift
class Bike {
    var wheelNumber = 2
    var hasBell = false
}
```
```swift
class Bike {
var wheelNumber = 2
var hasBell = false

}

var newBike = Bike()
var a = newBike
newBike.wheelNumber = 5

print(a.wheelNumber)
// newBike wheel number was originally 2 and a's wheelnumber was also 2 but when I changed the newbike wheel number it also changed a's value
```

## Question 3

a. Given the Animal class below, create a Bird subclass with a new `canFly` property.

```swift
class Animal {
    var name: String = ""
    var printDescription() {
        func("I am an animal named \(name)")
    }
}
```
```swift
class Bird: Animal{
var canFly = true
}
```

b. Override the printDescription method to have the instance of the Bird object print out its name and whether it can fly
```swift
class Animal {
var name: String = ""
func printDescription() {
print("I am an animal named \(name)")
}
}

class Bird: Animal{
var canFly = "I can fly"
override func printDescription() {
print("I am an animal named \(name) and \(canFly)")
}

}

var sparrow = Bird()
sparrow.name = "Sparrow"
sparrow.printDescription()
```

c. Create a Robin subclass of Bird.  Its name should always be "Robin".
```swift
class Animal {
var name: String = ""
func printDescription() {
print("I am an animal named \(name)")
}
}

class Bird: Animal{
var canFly = "I can fly"
override func printDescription() {
print("I am an animal named \(name) and \(canFly)")
}

}
class Robin: Bird {
var realName = "Robin"
override func printDescription() {
print("I am an animal named \(realName) and \(canFly)")
}

}

let robin = Robin()
robin.printDescription()
```


## Question 4

class Bike {
  let wheelNumber = 2
  let wheelWidth = 1.3
  var hasBell = true
  func ringBell() {
    if hasBell {
      print("Ring!")
    }
  }
}


## Question 5

a. Given the Point object below, complete the `distance method` so that it returns the distance between a given point.

The equation for the distance formula can be found [here](https://www.mathsisfun.com/algebra/distance-2-points.html).

`sqrt` is a method in Swift that gives the square root.  Make sure to have `import Foundation` or `import UIKit` to use this method.

```swift
struct Point {
    let x: Double
    let y: Double
    func distance(to point: Point) -> Double {

    }
}

let pointOne = Point(x: 0, y: 0)
let pointTwo = Point(x: 10, y: 10)

print(pointOne.distance(to: pointTwo)) //Prints 14.142135623730951
```
```swift
struct Point {
let x: Double
let y: Double
func distance(to point: Point) -> Double {
let a = self.x - point.x
let b = self.y - point.y
return sqrt(pow(a, 2.0) + pow(b, 2.0))
}
}

let pointOne = Point(x: 0, y: 0)
let pointTwo = Point(x: 10, y: 10)

print(pointOne.distance(to: pointTwo)) //Prints 14.142135623730951
```


b. Given the above Point object, and Circle object below, add a `contains` method that returns whether or not a given point is on the circle

```swift
struct Circle {
    let radius: Double
    let center: Point
}

let pointOne = Point(x: 0, y: 0)
let circleOne = Circle(radius: 5, center: pointOne)
let pointTwo = Point(x: 5, y: 0)
let pointThree = Point(x: 4, y: 0)
let pointFour = Point(x: sqrt(12.5), y: sqrt(12.5))
circleOne.contains(pointTwo) //true
circleOne.contains(pointThree) // true
circleOne.contains(pointFour) //true
```
```swift
struct Circle{
let radius: Double
let center: Point

init(radius: Double, center: Point){
self.center = center
self.radius = radius
}

func contains(_ aPoint: Point)->Bool{
let circumference = 2 * Double.pi * radius
if aPoint.x < circumference && aPoint.y < circumference{
return true
}
else{
return false
}

}
}

let pointOne = Point(x: 0, y: 0)
let circleOne = Circle(radius: 5, center: pointOne)
let pointTwo = Point(x: 5, y: 0)
let pointThree = Point(x: 4, y: 0)
let pointFour = Point(x: sqrt(12.5), y: sqrt(12.5))
circleOne.contains(pointTwo) //true
circleOne.contains(pointThree) //true
circleOne.contains(pointFour) //true
```

c. Add another method to `Circle` that returns a random point on the circle

Hint: Given the radius of a circle and the x value of a point on the circle, the y value of the point is defined by:

```
√(r^2) - (x^2)
```

```swift
circleOne.contains(circleOne.getRandomPoint()) //Should always be true
```
```swift
struct Point {
let x: Double
let y: Double
func distance(to point: Point) -> Double {
let a = self.x - point.x
let b = self.y - point.y
return sqrt(pow(a, 2.0) + pow(b, 2.0))
}
}

struct Circle{
let radius: Double
let center: Point

init(radius: Double, center: Point){
self.center = center
self.radius = radius
}

func contains(_ aPoint: Point)->Bool{
let circumference = 2 * Double.pi * radius
if aPoint.x < circumference && aPoint.y < circumference{
return true
}
else{
return false
}
}
func getRandomPoint()->Point{
let circumference = 2 * Double.pi * radius
let number = Point(
x: Double(arc4random_uniform(UInt32(circumference))),
y: Double(arc4random_uniform(UInt32(circumference))))

return number
}
}

let pointOne = Point(x: 0, y: 0)
let circleOne = Circle(radius: 5, center: pointOne)
let pointTwo = Point(x: 5, y: 0)
let pointThree = Point(x: 4, y: 0)
let pointFour = Point(x: sqrt(12.5), y: sqrt(12.5))
circleOne.contains(pointTwo) //true
circleOne.contains(pointThree) //true
circleOne.contains(pointFour) //true

circleOne.contains(circleOne.getRandomPoint())
```


## Question 6

a. Create a struct called HangmanModel with 3 properties `targetWord: String`, `numberOfIncorrectGuesses: Int` and `guessedLetters: [Character]`.

b. Add a method called `playerWon` that returns whether all of the characters in `targetWord` are in `guessedLetters`

var model = HangmanModel()
model.targetWord = "hello"
model.guessedLetters = ["h","e","o","l"]
model.playerWon() //true

c. Add a method called `printDisplayVersionOfWord` that prints the `targetWord` replacing characters that are not in `guessedLetters` with "_"

var model = HangmanModel()
model.targetWord = "hello"
model.guessedLetters = ["h","l"]
model.printDisplayVersionOfWord()
//prints h_ll_

d. Add a method called `guess(_:)` that takes in a character as input, and updates `guessedLetters` and `numberOfIncorrectGuesses` as appropriate.

var model = HangmanModel()
model.targetWord = "hello"
model.guess("h")
model.guess("a")
model.guessedLetters // ["h", "a"]
model.numberOfIncorrectGuesses // 1

e. Have `guess(_:)` also print out the current display version of the word, the number of incorrect guesses and if the player has won.
