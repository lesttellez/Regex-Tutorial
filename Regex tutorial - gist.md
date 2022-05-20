# Regex- A Brief Tutorial

Have you ever wondered what happens when you click the "filter" check boxes on a web page? How does the page know what to look for in your query? How about the "find and replace" option in Mircosoft Word? On a basic and conceptual level, these search features are based off of or acutally use a search pattern. These patterns, termed Regular Expressions (regex) are strings that denotes a specific pattern. This pattern is then used to match exact or partial string patterns of a target string. For example, in a Word document you crtl+f (search for) and type in 'x', you then get a list of all the 'x's in the document (these are typically highlighted in Word). *Please see RAW for comments pertaining to references, or my <a href="https://github.com/Tim-Zebra/17-Homework-CS/blob/main/README.md">ReadMe.md</a>* file.

## Summary

This tutorial will explain componets of a regex and how it works. The regex we will write will check if the entered date is formatted as MM-DD-YYYY.

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

Regex expressions are made of a miraid of components, the most basic of which are referred to as *atoms*. Atoms can be thought of as 'single characters' and they are either significant or non-significant.
<!-- Atoms obtained from https://www.cs.wcupa.edu/rkline/index/regular-expressions.html -->
<ul>
  <li> Single Characters:
    <ul>
      <li> Without signifcance: represents the character in the target string </li>
      <li> Operator characters (significanct): ^ . [ $ ( ) | * + ? { \
          <ul>
            <li>" ^ $ " : 'Anchors' also called 'Assertions</li>
            <li>" \ . " : Character Class</li>
            <li>" [ ] | ( ) " : 'Groups and Ranges'</li>
            <li>" * + ? { } " : 'Quantifiers'</li>
          </ul>
      </li>
    </ul>
  </li>
</ul>

### Anchors
Also known as 'assertions', anchors are boundaries on your search query. They define how a match is found using your query. They indivate the beginnings and ends of criteria, as well as tell the match to "look-ahead", "look-behind", and other conditional expressions. For example:
<ul>
  <li>" ^ " : Matches the beginning of an input. eg. /^T/ will match 'T' in 'Tim', but will not match 'T' in 'timothy'.</li>
  <li>" $ " : Matches the end of an input. eg. /m$/ will match 'm' in 'Tim', but will not match 'm' in 'Timothy'.</li>
</ul>

### Quantifiers
These define the criteria by number of characters or expressions to match. For example:
<ul>
  <li>" * " : Matches the preceding item, and checks from 0 to multiple occurances (considered "greedy"). eg. /a*/ will match *all* instances of "a" but also match all instances where the item begins with "a" or ends in "b".</li>
  <li>" + " : Matches the preceding item from 1 to multiple occurances (considered "greedy"). eg. /o+/ will match 'o' in 'lol and all 'o's in 'loooooooooool' </li>
  <li>" ? " : Matches the preceding item from 0 to 1 occurance (considered "non-greedy"). Adding a ? after a "greedy" quantifier causes the quantifier to be "non-greedy" eg. Using /<.+?>/ to match with <'line1'> <'line2'> <'/line1'> <'/line2'> will only match <'line1'> as this is the first occurance. Rather than matching every single element listed.</li>
  <li>" { } " : Matches the occurence a set amount of times (we'll call that 'n'). eg. o{3} will match 'loool', but will not match 'lool'. A range can also be set using {n,m} after your search item. eg. h{2,3} will match not match with 'chomp', but will match with, 'chhomp', 'chhhomp', and even 'chhhhhhhomp'. Why does it still register 'chhhhhhhomp' though? This is because 'h' occurs at least 2 times sequentially in this statement.</li>
</ul>

### Grouping Constructs
So how do we narrow down our search? What if I want just a* to bematched for a specific occurance, but not for all occurances? We can define our section of the search criteria to include only the set range or even a group to search. For example:
<ul>
  <li>" [ ] " : Matches the first occurance of the expression, and is narrowed by using a range. eg. [abcde] will match 'e' in 'wrecks'. [abcde] can also be written as [a-e], but please note using the hyphen before or after the expression [-abc] or [abc-] includes the hyphen and does not denote a range.</li>
  <li>" | " : Matches either of the passed variables. eg. /blue|green/ will find a match in both 'blue pinneapple' and 'green sun'.</li>
  <li>" ( ) " : Matches the occurance of the variable and remembers it. So '(fly)' will match and remember the positon of 'fly' in 'The birds fly south'. Note: best not to use these if possible because they decrease efficiency of the search. </li>
</ul>

### Bracket Expressions

<p>Bracket expressions '[ ]' were previously defined as a type of grouping construct. Using brackets creates a character set. You can also define the search to include everything NOT inside the braket. This is done by applying " ^ " to the expression which matches everything outside of the expression. eg. [^abcde] will match 'w' in 'wrecks' or 'k' in 'ecks'.</p>

### Character Classes

Character classes are used to distinguish between the different types of characters being searched. This is can be used to diferentiate between letters and integers.

<ul>
  <li>" \ " : These distinguish between the type of character being serached. \d searches for digits, while \D searches everything except for digits. \w searches for all alphanumeric characters, while \W searches for all non-alphanumeric characters (such as $).</li>
  <li>" . " : Matches every single character, with the exception of line terminators: \n, \r, \u2028, and \u2029. These are like wildcards. eg. /b.d/ will match 'bid', 'bod', 'bed', 'bad', etc.</li>
</ul>

### The OR Operator

<p>The OR operator ' | ' was previously defined as a type of grouping construct. Using the OR operator in ^a|b$|c* will match every instance of 'a' starting a string, every 'b' at the end of a string, or all instances of 'c'.</p>

### Flags

These are added to the end of an expression allowing the functionality to expand globally along with case-insensitive searching. It alters the pattern for the search, formated as /pattern/flag. eg. /some expression/g where 'g' tells the expression to look globally. Or /pattern/i where 'i' tells the search that the case is 'insensitive'.

### Character Escapes

<p>You probably remember seeing ' \ ' previously? This is also way to 'escape' a character. Is used to match 'literally', and allows a previous special charater 'escape' it's usual defined operation. eg. /b*/ finds all occurances of 'b' but what if I was looking for the combo of 'b*'? I would change the expression be adding the escape to /b\*/ allowing us to find the literal "b*" </p>

### Example
<p>Now we've learned the bare basics of regex, possibly a little less maybe a little more. Regex at the source seems simple and straight forward, but knowing just enough and using great tools such as Professor Google should be enough to write some useful regex!</p>
<p>Let's write a simple search to check if MM-DD-YYYY is present.</p>
<p>Criteria will be specific enough to filter out months 1-12, with an acceptable day ranging up to 31. We will not be filtering too far in depth such as accounting for days per given month (especially leap year). Will also not concern ourselves with AD,BC, and future dates that exceed 4 digits for the year. But these can be done, have at it after this tutorial if you're brave enough or want the extra practice. Now! Let's start by creating our regex to match our simple date format:</p>

<ul>
  <li>Section - 'MM-'</li>
    <ul>
      <li> Pseudocode: I want a month to match if the first M is equal to 0-1 and the last M is equal to 0-9 only when the first digit is 0, else the second digit should only equal 0-2 . We want to group the MM.</li>
        <ul>
          <li>The first M:</li>
          <ul>
            <li>I want it to equal 0 or 1. This hints I should be using an OR operator. M will be used to denote the M not yet solved for</li>
            <li>Code snippet: ([0]M|[1]M)</li>
          </ul>
          <li>The second M:</li>
          <ul>
            <li>I want it to equal 1-9 if the month is a single number (09) OR 0-2 (to account for oct, nov, dec.)</li>
            <li>Code snippet: (M[1-9]|M[0-2])</li>
          </ul>
          <ul>
            <li>Lets take care of whatever is being used to separate the dates, we will account for the standard MM.DD.YYYY, MM-DD-YYYY, and MM/DD/YYYY. We need for these separators to 1. not perform a function (such as ' . ' wildcard) and have them be 'literal'</li>
            <li>Code snippet: [\/\.\-]</li>
          </ul>
        </ul>
        <ul></ul>
      </li>
      <li>Our combined code snippet is: ([0][1-9]|[1][1-2])[\/\.\-] </li>
    </ul>
  </li>
  <li>Section - 'DD-'
    <ul>
      <li> Pseudocode: I want the day to match 0 through 3, but at 3 I want the second digit to be no more than 1. The second digit may not be equal to 0 if the first digit is also 0</li>
        <ul>
          <li>The first D:</li>
          <ul>
            <li>I want it to equal 0 or 1. This hints that I be using an OR operator. D will be used to denote the D not yet solved for</li>
            <li>Code snippet: ([0]D|[1-3]D)</li>
          </ul>
          <li>The second D:</li>
          <ul>
            <li>I want it to equal 1-9 if the month is a single number (09) OR 0-9 if the month begins with 1-2 OR 0-1 if the month begins with 3</li>
            <li>Code snippet: ([0][1-9]|[1-2][0-9]|[3][0-1])</li>
          </ul>
          <ul>
            <li>Again, we'll cover our MM DD YYYY separator</li>
            <li>Code snippet: [\/\.\-]</li>
          </ul>
        </ul>
        <ul></ul>
      </li>
      <li>Our combined code snippet is: ([0][1-9]|[1-2][0-9]|[3][0-1])[\/\.\-] </li>
    </ul>
  </li>
  <li>Section - 'YYYY'
    <ul>
      <li> Pseudocode: I want all digits in the year to be equal to 0-9. Accounting for all past and future dates using a 4 digit year</li>
        <ul>
          <li>All four Y's</li>
          <ul>
            <li>The range of YYYY can only be 0000-9999</li>
            <li>Final code snippet: ([0-9][0-9][0-9][0-9])</li>
          </ul>
        </ul>
    </ul>
  </li>
  <li>Final code snippet: Note: we'll add the flags for global identifier 'g' and multi-line match 'm'</li>
  <ul>
    <li>/([0][1-9]|[1][1-2])[\/\.\-]([0][1-9]|[1-2][0-9]|[3][0-1])[\/\.\-]([0-9][0-9][0-9][0-9])/gm</li>
  </ul>
</ul>

<p>Feel free to visit <a href="https://regex101.com/r/B9zd2y/1">https://regex101.com/r/B9zd2y/1</a> and test it out yourself, or challenge yourself by making your own on <a href="https://regex101.com/">"https://regex101.com/"</a>!</p>

## Author
Created by Timothy Zalewski | Deployed on [GitHub](https://github.com/Tim-Zebra)