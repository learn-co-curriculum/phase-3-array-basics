# Array Basics

## Learning Goals

- Access and manipulate data in arrays in Ruby

## Introduction

Arrays in Ruby share many of the characteristics you're already familiar with
from working with arrays in JavaScript. In both languages, arrays are used to
store lists of data (which can be any data type, and even multiple types of data
within the same array) in a specific order. Let's explore some common methods
for working with arrays in Ruby.

## Array CRUD

In Ruby, as in JavaScript, you'll commonly need to Create, Read, Update, and
Delete data from within arrays. You should also check out the
[Array class documentation][array docs] for a full list of array methods in
Ruby.

Open up IRB and follow along with these examples. Let's start by creating an
array representing a shopping list:

```rb
shopping_list = ["Cookies", "Ice Cream", "Snickers"]
```

### Reading Elements From Arrays

As in JavaScript, you can access elements of the array using bracket notation
with the index of the element:

```rb
shopping_list[0]
# => "Cookies"
shopping_list[1]
# => "Ice Cream"
```

You can also access elements starting from the end of an array by providing a
negative index:

```rb
shopping_list[-1]
# => "Snickers"
```

Using the bracket notation will also let you update elements within arrays:

```rb
shopping_list[1] = "Mint Chocolate Chip Ice Cream"
# => "Mint Chocolate Chip Ice Cream"
shopping_list
# => ["Cookies", "Mint Chocolate Chip Ice Cream", "Snickers"]
```

Ruby also has a couple methods for convenience for accessing elements at the
beginning and end of arrays:

```rb
shopping_list.first
# => "Cookies"
shopping_list.last
# => "Snickers"
```

The `last` method in particular is quite convenient compared to the equivalent
JavaScript code:

```js
shoppingList[shoppingList.length - 1];
```

Ruby also lets you determine the number of elements in an array with the
`length` method. `length` has an alias method `size` that does the same thing:

```rb
shopping_list.length
# => 3
shopping_list.size
# => 3
```

Like in JavaScript, you can use the `slice` method to access multiple elements
from an array. Ruby also lets you pass a Range of index numbers using the
bracket notation to achieve the same outcome:

```rb
shopping_list.slice(0, 2)
# => ["Cookies", "Mint Chocolate Chip Ice Cream"]
shopping_list[0..1]
# => ["Cookies", "Mint Chocolate Chip Ice Cream"]
shopping_list[0...2]
# => ["Cookies", "Mint Chocolate Chip Ice Cream"]
```

With the Range notation, two dots (`..`) means "all numbers up to and including
the last one", and three dots (`...`) means "all numbers up to, but not
including, the last one."

### Adding Elements to Arrays

Like JavaScript, and many other languages, the `push` and `unshift` methods can
be used to add elements to the end or beginning of arrays respectively:

```rb
shopping_list.push("M&Ms")
# => ["Cookies", "Mint Chocolate Chip Ice Cream", "Snickers", "M&Ms"]
shopping_list.unshift("Cake")
# => ["Cake", "Cookies", "Mint Chocolate Chip Ice Cream", "Snickers", "M&Ms"]
```

Ruby also has the **shovel method** (`<<`) which does the same thing as `push`,
but is more commonly used:

```rb
shopping_list << "Tums"
# => ["Cake", "Cookies", "Mint Chocolate Chip Ice Cream", "Snickers", "M&Ms", "Tums"]
```

Ruby also has a couple ways to combine multiple arrays. You can use the `concat`:

```rb
one_two_three = [1, 2, 3]
four_five_six = [4, 5, 6]

one_two_three.concat(four_five_six)
# => [1, 2, 3, 4, 5, 6]
one_two_three
# => [1, 2, 3, 4, 5, 6]
```

`concat` changes the data in the original array, so if you want to combine arrays
without changing the original, you can also use the `+` method:

```rb
one_two_three = [1, 2, 3]
four_five_six = [4, 5, 6]

one_two_three + four_five_six
# => [1, 2, 3, 4, 5, 6]
one_two_three
# => [1, 2, 3]
```

### Removing Elements from Arrays

Like JavaScript, and many other languages, the `pop` and `shift` methods can
be used to remove elements from the end or beginning of arrays respectively:

```rb
shopping_list = ["Cookies", "Ice Cream", "Snickers"]
# => ["Cookies", "Ice Cream", "Snickers"]
shopping_list.pop
# => "Snickers"
shopping_list
# => ["Cookies", "Ice Cream"]
shopping_list.shift
# => "Cookies"
shopping_list
# => ["Ice Cream"]
```

## Advanced Array Methods

Ruby has many other built-in methods which you can explore in the
[Array class documentation][array docs]. We'll be covering some of the
**enumerable** methods in a later lesson as well. But for now, here are a few
other methods that make it convenient to work with arrays in Ruby.

To check if a particular element is present in an array, use `includes?`:

```rb
letters = ["a", "b", "c"]
letters.includes?("a")
# => true
letters.includes?("e")
# => false
```

> In Ruby, there's a convention that methods that return a boolean value are
> named with a question mark at the end, like `includes?`.

To reverse all the elements of an array, use `reverse`:

```rb
letters.reverse
# => ["c", "b", "a"]
letters
# => ["a", "b", "c"]
```

This returns a new array in the reverse order. You can also reverse the array in
place (change the data in the array) with the `reverse!` method:

```rb
letters.reverse!
# => ["c", "b", "a"]
letters
# => ["c", "b", "a"]
```

> In Ruby, there's a convention that methods that modify the object they're
> called on end with an exclamation mark, like `reverse!`.

Ruby also has a `sum` method which will add every element in an array:

```rb
[1, 2, 3].sum
# => 6
```

Compare this to JavaScript:

```js
[1, 2, 3].reduce((sum, num) => sum + num);
```

Last but not least, Ruby has a `uniq` method for returning only the unique
elements from an array:

```rb
[1, 1, 2, 3, 5].uniq
# => [1, 2, 3, 5]
```

Again, this is quite convenient compared what you'd have to do to implement this
functionality in JavaScript!

```js
[1, 1, 2, 3, 5].filter((num, index, array) => array.indexOf(num) === index);
```

### Special Array Syntax

Ruby supports a couple of other special syntaxes for creating arrays which you
may encounter in other Ruby code. You can use `%w` to create an array of strings
(assuming each string is one word):

```rb
%w[pending resolved rejected]
# => ["pending", "resolved", "rejected"]
```

You can also create an array of symbols with `%i`:

```rb
%i[pending resolved rejected]
# => [:pending, :resolved, :rejected]
```

Don't worry about memorizing this syntax &mdash; just keep this in the back of
your mind in case you come across it in any Ruby code you run into.

## Conclusion

Ruby and JavaScript have a lot in common when it comes to working with arrays.
Ruby has a few additional tricks up its sleeve for solving problems programmers
commonly face that other languages, including JavaScript, don't include by
default, so make sure to take advantage of these added features when the
opportunity arises!

## Resources

- [Array documentation][array docs]

[array docs]: https://ruby-doc.org/core-2.7.3/Array.html
