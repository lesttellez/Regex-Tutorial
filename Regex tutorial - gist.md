# RegEx- A Brief Tutorial

Have you ever wondered what happens when you click the "filter" check boxes on a web page? How does the page know what to look for in your query? How about the "find and replace" option in Mircosoft Word? On a basic and conceptual level, these search features are based off of or acutally use a search pattern. These patterns, termed Regular Expressions (regex) are strings that denotes a specific pattern. This pattern is then used to match exact or partial string patterns of a target string. For example, in a Word document you crtl+f (search for) and type in 'x', you then get a list of all the 'x's in the document (these are typically highlighted in Word). *Please see RAW for comments pertaining to references, or my <a href="https://github.com/Tim-Zebra/17-Homework-CS/blob/main/README.md">ReadMe.md<a> file.*

## Summary

This tutorial will explain componets of a regex and how it works. The regex we will be using checks if the entered date is formatted as MM-DD-YYYY.

<!-- Regex code snippet below (obtained from mVChr at https://stackoverflow.com/questions/5465375/javascript-date-regex-dd-mm-yyyy): -->

*/(0[1-9]|1\d|2\d|3[01])\ /^(0[1-9]|1[0-2])\/(19|20)\d{2}$/*

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

### Quantifiers

### Grouping Constructs

### Bracket Expressions
    <p>Using brackets eg. [ ] creates a character set. This set of characters is used to match any single character from the target string. These ranges are denoted using " - " to specify the 'between' portion of two criteria</p>
### Character Classes

### The OR Operator

### Flags

### Character Escapes

## Author
Created by Timothy Zalewski | Deployed on [GitHub](https://github.com/Tim-Zebra)