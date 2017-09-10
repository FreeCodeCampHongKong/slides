# Programming 101

## Tooling

* A "modern" web browser
* [REPL.it for PHP](https://repl.it/languages/php): online interactive PHP "interpreter" (or "runner")
* [TutorialsPoint Node.JS REPL Environment](https://www.tutorialspoint.com/execute_nodejs_online.php): online interactive Node.JS "interpreter" (or "runner")
* Enrollment in our [HackerRank project](https://www.hackerrank.com/fcchk-programming-101)

## Hello world

PHP syntax for showing something to the user:

##### PHP Version
```php
print("Hello!");
```

[PHP Example on repl.it](https://repl.it/Ke3w/0)

Note that in the *repl.it* environment, you don't have to type in `<?php` or `?>`. In real (including HackerRank) environments however, the `<?php` is necessary while `?>` is not. (In fact, it is now considered a [best practice](https://en.wikipedia.org/wiki/Best_practice) to skip it.)

##### JS Version
```javascript
console.log("Hello");
```

* **Exercise**: Write a program that shows "Hello world!" to the user. [Solution checker](https://www.hackerrank.com/contests/fcchk-programming-101/challenges/hello-world-73)

### Asking for user input

PHP syntax to ask for user input:
```php
fgets(STDIN);
```

Node.JS syntax to ask for user input:
```javascript
require("fs").readFileSync(0).toString(); // press ctrl-D to terminate input
```

Here is how one might want to immediately show ("echo") user input:
```php
print(fgets(STDIN));
```

* **Exercise**: Using JavaScript / Node.JS, write a echo program that functions as the one that is just shown.

## Variables

A variable is a shoebox that stores values, which can be updated any time the programmer wants.

* **Exercise**: Write a program that (1) stores "Hello world!" in a variable called `isaac`, then (2) shows the content of `$isaac` to the user. The outputs of both exercises one and two should be the same. [Solution checker](https://www.hackerrank.com/contests/fcchk-programming-101/challenges/hello-world-73)

## Basic maths with variables

You can assign "mathematical expressions" to variables. The following code segments are all legit:

##### PHP Version
```php
$foo = 9*2;
$bar = 1+3 * 3;
```

##### JS Version
```javascript
var foo = 9*2;
var bar = 1+3 * 3;
```

* **Question**: Is `$bar` 10 or 12?

## Conditions

A "branching structure" basically means that the computer might run code #1 or code #2 depending on a *condition* that is evaluated in runtime.

![If flowchart](http://www.openbookproject.net/books/bpp4awd/_images/flowchart_if_else.png)

Beginning Python Programming for Aspiring Web Developers, Jeffrey Elkner. [GNU FDL 1.3](http://www.openbookproject.net/books/bpp4awd/copyright.html).

**Boolean value** is just a fancy name for a value of either `false` or `true`. Note that these two values are not surrounded by quotes: `'` or `"`.

##### PHP Version
```php
$weekend = false;
if ($weekend) {
	print("Woo hoo! Go get some fun.");
}
```

##### JS Version
```javascript
const weekend = false;
if (weekend) {
	console.log("Woo hoo! Go get some fun.")
}
```

`!` (negate operator, uh) inverts the boolean value. `!true` gives you `false`, for instance.

```php
$weekend = false;
if ($weekend) {
	print("Woo hoo! Go get some fun.");
}
if (!$weekend) {
	print("Everyone back to work. Party is over.");
}
```

##### PHP Version
```php
$weekend = false;
if ($weekend) {
	print("Woo hoo! Go get some fun.");
} else {
	print("Everyone back to work. Party is over.");
}
```

##### JS Version
```javascript
const weekend = false;
if (weekend) {
	console.log("Woo hoo! Go get some fun.");
} else {
	console.log("Everyone back to work. Party is over.");
}
```

### Else-if

##### PHP Version
```php
$weekday = 1;
if ($weekday == 1) { // remember to use two equal signs
	print("Monday");
} else if ($weekday == 2) {
	print("Tuesday");
} elseif ($weekday == 3) { // you can either put together or break `else` and `if` apart
	print("Wednesday");
}
// skipped for brevity
```

##### JS Version
```javascript
const weekday = 1;
if (weekday == 1) { // remember to use two equal signs
	print("Monday");
} else if (weekday == 2) {
	print("Tuesday");
} else if (weekday == 3) { // in JS you must break `else` and `if` apart
	print("Wednesday");
}
// skipped for brevity
```

* **Exercise**: Write a program that translates a *month number* (which runs from 1 to 12), which is stored as a variable named `$month`, to the *name* of the month (e.g. January). You may skip months 4 ~ 12 just as I did here.

### Switch-case

##### PHP Version
```php
$weekday = 1;
switch ($weekday) {
	case 1:
		print("Monday");
		break;
	case 2:
		print("Tuesday");
		break;
	case 3:
		print("Wednesday");
		break;
	default:
		print("Holiday!");
		break;
}
```

##### JS Version
```javascript
const weekday = 1;
switch (weekday) {
	case 1:
		console.log("Monday");
		break;
	case 2:
		console.log("Tuesday");
		break;
	case 3:
		console.log("Wednesday");
		break;
	default:
		console.log("Holiday!");
		break;
}
```

* **Exercise**: Write a program that translates a *month number* (which runs from 1 to 12), which is stored as a variable named `$month`, to the *name* of the month (e.g. January). You may skip months 4 ~ 12 just as I did here.
* **Exercise**: Write a program that (1) asks the user for a *month number* (which runs from 1 to 12) and (2) then translate it to the *name* of the month (e.g. January). You may skip months 4 ~ 12 just as I did here.

## Functions

A function allows one to group frequently-executed or heavy-weight code in a place that is separated from its "usual" place.

### Real-life example

#### Scenario 1:
> sin(pi/2) = 1

But... do you know what actually happens behind the hood?

As it turns out, when one computes `sin(x)` he's actually doing some really fancy maths!

![Maclaurin expansion of sin(x)](https://user-images.githubusercontent.com/1005813/30049455-5572d33c-924d-11e7-8a61-02bcd984e2fe.png)

But worry not, you don't have to know or memorize any of them. All you need to know is what this `sin(x)` thing is, and how do you use it.

#### Scenario 2:
Imagine we are now living in a planet where *multiplication* has yet to be invented. Now suppose someone is paying for 3 donuts, which costs $2 each...

> Hey, buddy, what is $2 + $2 + $2?

Everyone understands that, but computation is somewhat troublesome. But no worries, it is working after all.

Now suppose someone thinks that this expressions is to troublesome. For example, what would happen when someone is buying 50 donuts in one go? That would be:

> Hey, buddy, what is $2 + $2 + $2 + $2 + $2 + $2..... + $2?

This is the exact reason why people invented the "multiplication" terminology. Even though people here are totally clueless with regards to *multiplication table*, they would be saving tons of time by saying this instead:

> Hey buddy, what is $2 multiplied by 50?

**Summary**: functions help us to group together frequently used code, saving us keystrokes.

### Coding scenario

Let's say you're writing a blogging software. As part of the package you need to convert *month numbers* (which runs from 1 to 12) to the *names* of the months (e.g. January). You will need to do this in multiple places. Instead of copy-and-pasting the same code over and over, you can put the code in a central place, and re-use them in your code. In case a bug is found, you simply need to correct it in the central repository, and it would be fixed in all the places.

### Return value
In all of the scenarios we mentioned above, all of them *returns* something. In scenario 1, the return value is a sum of the fractions; in scenario 2, we get the product of the multiplication. In the coding scenario, the function returns the "month name". But not all functions return something. For instance, a function `notifyPoster()` may send an email to notify the original poster ("OP") that a new reply is made to his post. In such case, a return value might not be necessary.

## Loops

You probably have heard of the phrase "無限 loop" in Hong Kong. Loop essentially means doing the same thing over and over.

This is what might happen when I stand in line in a McDonald's:

```pseudocode
while (<check if server is ready>) {
	<fiddle with my phone>
}
```

Here is how one might ask the user to enter *42*, repeatedly, until *42* is entered.

```php
print("Enter 42 please~");
while(trim(fgets(STDIN)) != "42") {}
print("You entered 42!");
```

You may skip the current loop with `continue`:
### Print 1 ~ 100 except multiples of 7
```php
function is_multiple_of_7(int $number) {
	return $number % 7 == 0;
}
$i = 0;
while($i < 100) {
	$i = $i + 1;
	if (is_multiple_of_7($i)) {
		continue;
	}
	print("$i\n");
}
```

Or just terminate the loop with `break`:
### Print all non-negative integers before 27:
```php
$i = 0;
while (true) {
	if ($i >= 27) {
		break;
	}
	print("$i\n");
	$i = $i + 1;
}
```

* **Exercise**: Using an endless loop, accept user input and immediately show it back to the user. End your program with ctrl-D or ctrl-C. [Solution checker](https://www.hackerrank.com/contests/fcchk-programming-101/challenges/echo-1)

## Arrays
Array is a more advanced version of variable. An array holds multiple values (a typical variable only hold one) and each value are identified by a number starting from 0. For example:

##### PHP Version
```php
$students = ["Isaac", "Tommy", "Jason", "Tim"];
// $students[0] = Isaac
// $students[1] = Tommy
```

##### JS Version
```javascript
const students = ["Isaac", "Tommy", "Jason", "Tim"];
// students[0] = Isaac
// students[1] = Tommy
```

To inspect an array, `print_r` can be used in place of `print`:
```php
print_r($students);
```

### For each
A very popular application of arrays is to *loop through* it.

##### PHP Version
```php
$students = ["Isaac", "Tommy", "Jason", "Tim"];
foreach ($students as &$student) {
	print("$student is one of my students.\n");
}
```

##### JS Version
```javascript
const students = ["Isaac", "Tommy", "Jason", "Tim"];
for (const studentId in students) {
	console.log(`${students[studentId]} is one of my students.\n`);
}
```

### Filtering
![Filtering icon](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a7/Toicon-icon-lines-and-angles-filter.svg/240px-Toicon-icon-lines-and-angles-filter.svg.png)

Toicon-icon-lines-and-angles-filter.svg, by Shannon E Thomas/toicon.com. Licensed under CC-BY 4.0.

##### PHP Version
```php
function odd($number) {
	return $number % 2 === 1;
}

$numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8];
$filtered = array_filter($numbers, "odd");
print_r($filtered);
```

##### JavaScript Version
```javascript
function odd(number) {
	return number % 2 === 1;
}

const numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8];
const filtered = numbers.filter(odd);
console.log(filtered);
```

### Lambda / anonymous functions
Now, you might wonder if we could simply put the filtering criterion inside the `filter()` / `array_filter()` call, instead of having to define it externally... well the answer is yes:

##### PHP Version
```php
$numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8];
$filtered = array_filter($numbers, function($number){return $number % 2 === 1;});
print_r($filtered);
```

##### JavaScript Version
```javascript
const numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8];
const filtered = numbers.filter((number) => number % 2 === 1);
console.log(filtered);
```

##### Python Version (purposely not using list comprehension to illustrate lambda functions)
```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8]
filtered = filter(lambda number: number % 2 == 1, numbers)
print(filtered)
```

These are called lambda or anonymous functions. Unfortunately today's focus is on programming concepts, not syntax, so I would not go too deep on this.

##### PHP Syntax
```php
function($number){return $number % 2 === 1;}
```

##### JS Syntax
```javascript
(number) => number % 2 === 1
```

##### Python Syntax
```python
lambda number: number % 2 == 1
```

The gist of an anonymous function is that it allows one to pass in a function as an argument, without having to define it externally.

### Mapping
Now let's do some practice with lambda functions. Mapping refers to an operation where each and every element in an array goes through the same operation. The old array however is not changed.

##### PHP Version
```php
$numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8];
$doubled = array_map(function($number){return $number*2;}, $numbers);
print_r($doubled);
```

##### JavaScript Version
```javascript
const numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8];
const doubled = numbers.map((number) => number*2);
console.log(doubled);
```

* **Exercise**: Write a program that continuously asks the user to enter a number, until a negative value is entered. Then list the user's input so far (including the negative value), remove the even entries, and then list the filtered entries again. [Solution checker](https://www.hackerrank.com/contests/fcchk-programming-101/challenges/even-numbers-remover)

## Include/require/modules & Dependency Managers

There might be a number of times where a common "module" is needed. See below for an example:

##### CartController.php
```php
if (!validate('new_order', $request->form(0))) {
	return abort(400, 'invalid form data');
}
```

##### MemberController.php
```php
if (!validate('member_registration', $request->form(0))) {
	return abort(400, 'invalid form data');
}
```

Now, this `validate()` function might be generic enough that is useful across multiple pages. It makes perfect sense to put it in a third file and load it. This has the advantage that, for any changes, it will be applied to both *CartController.php* and *MemberController.php* without copy-pasting it again.

In vanilla PHP we might do this:

##### validator.php
```php
function validate(string $name, $input) {
	// logic here
	return true;
}
```

##### CartController.php
```php
require_once('validator.php');
if (!validate('new_order', $request->form(0))) {
	return abort(400, 'invalid form data');
}
```

##### MemberController.php
```php
require_once('validator.php');
if (!validate('member_registration', $request->form(0))) {
	return abort(400, 'invalid form data');
}
```

## Data types:
Common data types in computer systems include:

| Data Type (Using PHP as example) | PHP Example |
| -------------------------------- | ----------- |
| integer                          | $foo = 9;   |
| double (also float, real)        | $foo = 9.12;|
| string                           | $foo = "Isaac";|
| boolean                          | $foo = true;|
| callable                         | array_map("triple", $arr) |

Refer to the [PHP Manual](http://php.net/manual/en/language.types.intro.php) for more information.

## Exercises
* [FizzBuzz](https://en.wikipedia.org/wiki/Fizz_buzz) - [Solution checker](https://www.hackerrank.com/contests/fcchk-programming-101/challenges/fizz-buzz-4)
* [Anagram detector](http://david.elbe.me/developers/hiring/2014/09/17/fizzbuzz-alternatives.html)

## Resources

* [PHP.net](http://php.net) (e.g. http://php.net/**array_map**)
* [DevDocs](http://devdocs.io) - an aggregate, instant-search collection of references
* [Mozilla Developer Network](https://developer.mozilla.org/) - JS Reference
* [Learn X in Y minutes](https://learnxinyminutes.com/) - A collection of short-and-neat programming tutorials. I learnt Python & C++ in ~2 weeks with this site.
