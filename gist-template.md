# How to detect a HEX value with Regex

The purpose of this document is to explain the basics of regex and structure.  It will not go into the purpose
or necessity for HEX code or values but be limited to scope of detecting them.

## Summary

In the following sections we will break down the following Regex expression: `/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`
It's important to keep in mind that regex is a very diverse language and you can detect something in many 
different ways.  As they say: "There is more then one way to peel an Apple".

Also there are many levels of "correct" in data comparision.  Its most important that the regex you utilize
satisfies your projects technical or business needs.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

In this particular expression we will be utilizing a few common and well used components.  The reference
table below will document just the major items we will be using.  More details will be below on each item.

Reference: `/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

( ) = parenthesis denote a group of items that resolve
[ ] = brackets allow for you to specify more then one valid option for one position
 -  = the (dash) allows for you to specify a range of options
{ } = curly brackets allows you to specify a quantity of valid optoins that are required
 |  = the pipe allows you to make an OR statement between two valid options

### Anchors

Anchors are a vital part of regex expressions.  They are often easily misused because they are overlooked.
Its important to remember that an anchor allows you to "start" your validation in certain positions of
your search string or data.  Here are the anchors used in our expression:

 ^  = The carrot requires that the validation starts at the first position of the search string
 $  = The dollar sign means the search string MUST end at the final valid comparison

 EXAMPLE:

 Reference: `/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`
 STRING A: #AA11FF   (valid)
 STRING B: #A1F      (valid)
 STRING C: Please use color code #CCC as your border  (invalid)

 EXPLINATION:
 STRING A: this is valid because:
            1) it matches the start character "#"
            2) it matches the first option group "[a-f0-9]{6}"
            3) the string ends with no other data after matching the final option group
 STRING B: this is valid because:
            1) it matches the start character "#"
            2) it matches the first option group "[a-f0-9]{3}"
            3) the string ends with no other data after matching the final option group
 STRING C: this is invalid because:
            1) it does not start with the "#" required character
            2) it does not end after the option groups "if it had matched"
            3) it is in the middle of another string

### Quantifiers

Quantifiers are placed to identify how many of a pattern is valid.  This can be Zero OR One, One or More, Infinite, or a specific range of times.

 ?  = Dollar sign means it should be Zero or One times
{ } = Curly brackets specific an exact amount or range of items

Reference: `/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

In our 2 option groups we have a {6} and an {3} quantifier specified.  This means that we can have 6 of the first group OR 3 of the second group.  This is because in HEX there is a full and short hand format.  HEX shorthand is only used to save on data size as HEX is an ASCII character encoding format (not covered here)

HEX FULL: #352AF4  (shows all 6 characters)
HEX SHORT: #FA1    (this equals #FFAA11)

### Grouping Constructs

Grouping allows us to specify more then one valid option for a pattern.  This is good because sometimes data is
expressed similarly but different in other languages and lets us verify the impirical part needed.

Reference: `/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

As you can see that both groups shown below are wrapped in parenthesis and seperated by a pipe.  This is equivilent
to a simple "IF OR" statement.  please see the table below breaking out how the logic works.

STATEMENT: If (group 1 matches OR group 2 matches) THEN true
OPTION: ([a-f0-9]{6} | [a-f0-9]{3})
GROUP 1: [a-f0-9]{6}
GROUP 2: [a-f0-9]{3}

### Bracket Expressions

Bracket expressions are the heart and soul of regex expressions.  Without them regex wouldn't be very useful.
They allow us to specify exactly what is allowed for X positions of the search string.  Brackets without a 
quantifier simply means just the one posistion.

**WARNING** Bracket Expressions are the literal ASCII character and if you 
            want to use a special character you must escape it!!!

Reference: `/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

EXAMPLE 1: [a-f0-9]{6} = the position is valid if:
                          1) we have 6 valid characters in sequence
                          2) the character is between a-f (ie: a,b,c,d,e,f)
                          3) the character is between 0-9 (ie: 0,1,2,3,4,5,6,7,8,9)

EXAMPLE 2: [a-f0-9]{3} = the position is valid if:
                          1) we have 3 valid characters in sequence
                          2) the character is between a-f (ie: a,b,c,d,e,f)
                          3) the character is between 0-9 (ie: 0,1,2,3,4,5,6,7,8,9)

**NOTE** each quantifier is only 1 character and each must be in the valid ranges specified in sequence

## Author
Edin Hurem - Web Developer student at UNCC boocamp. 

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)

// You are required to submit the following for review:

// The URL of the GitHub gist. Give the gist a unique name.
