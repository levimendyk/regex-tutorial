# Defining Phone Number Searches with Regex

In this tutorial, I will show you have you can define a search pattern for phone numbers using regular expression or "regex".

## Summary

Defining the phone number search patterns using regex will help you identify when a matching phone number appears when user's use your application. Phone numbers can be complex with spaces, hyphens, parentheses, and a combination of all. I will show you how to build a regular expression that will identify all of these. Here is the end result of the regular expression we will be learning about today: /\\(?(\d{3})\\)?[ -]?(\d{3})[ -]?(\d{4})/gm

## Table of Contents

- [Starting](#starting)
- [Digit](#digit)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Capture Groups](#capture-groups)
- [Special Characters](#special-characters)
- [Closing Remarks](#closing-remarks)
- [Author](#author)

## Regex Components

### Starting

Before diving deep into regular expressions, you need to know how to start one in the first place. (Also please use https://regex101.com/ or https://regexr.com/ to follow along)

Every regular expression starts with a / indicating the start of the expression and ends with a / to close it. After the closing / you will notice a gm which indicates that flags used. g = global (allows you to match everything withing the string) and m = multiline (alllows you to search multilines individually). So first our regular expression looks like this. / /gm

### Digit

Okay first lets take your basic phone number. Phone numbers do not contain letters. In order for our search to identify numbers we need to use a digit identifier in our starting expression code. I have added the \d which indicates it will match a digit character between 0 and 9. So adding that into our code we now have this. /\d/gm

### Quantifiers

The basic phone number contains 10 digits (U.S. numbers). So lets start off with a phone number 3035551234 okay 10 digits. Lets start off by defining the search to match 10 digits. We will use a quantifier in order to detail exactly how many digits we want to use. Our quantifer is this {10}. So adding that into our code we now have this. /\d{10}/gm

### Grouping Constructs

Phone numbers usually don't look all smashed together with no spacing like this 3035551234. So, in order to fix that, we need to add group constructs. So to seperate the number into groups such as the area code, central office/exchange code, and the last four digits which is the line number/subscriber number we need to group them. To do that we need to add more digit identifiers and quantifiers. So adding that into our code we now have this. /\d{3}\d{3}\d{4}/gm

### Bracket Expressions

Now to identify when there is a space or hypen in our code, we need to add bracket expressions which are litteraly just brackets []. To add just a hyphen you would just add a - between each group but we want our search to be able to include hyphens and/or spaces so we will add a [ -] between our groups. Also, we will need to include a ? so that space or hyphen is an option. Now we can capture these examples: 303 555 1234 or 303-555-1234 So adding this into our code we now have this. /\d{3}[ -]?\d{3}[ -]?\d{4}/gm

### Capture Groups

Now, for data retrieval preferences, say when we get a phone number, we want to convert it back to a 10 digit smashed together number for our database. We will want to group these numbers using () for each group of digits. Once we have that in our regular expression, we can click the replace tab and then enter <<$1$2$3>> which will convert for example, 303-555-1234 back to 3035551234. So adding that into our code we now have this. /(\d{3})[ -]?(\d{3})[ -]?(\d{4})/gm

### Special Characters

Some phone numbers contain parenthese for the first 3 digits. So in order to recognize () which is a special character we need to also add a backslash to recognize we are literally using parenthese and not trying to capture groups. We also want it to be an option to have parenthese so we again will add a ? to it. So our number now can look like this (303) 555 1234. So adding that into our code we now have this. /\\(?(\d{3})\\)?[ -]?(\d{3})[ -]?(\d{4})/gm

### Closing Remarks

And there we have it! You have just learned how to build a regular expression on phone number searches. I highly recommend using other outside resources to expand on your knowledge of Regex. Youtube is always a great place for tutorials. Also be sure to use websites such as https://regex101.com/ and https://regexr.com/ to put your knowledge to the test.

## Author

Levi Mendyk is a Full Stack Web Developer taking/took a class through the University of Denver.  
Github Profile: https://github.com/levimendyk
