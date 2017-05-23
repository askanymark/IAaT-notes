# Regex
> In PHP, regexes are strings that begin and end with **/**
## The modifiers
- **.** means any
  - -'/.oo.y/' matches 'Doocy', 'goofy', 'LooNy'
- **i** means case-insensitive
  -  '/xen/i' matches 'Xenia', 'xenophobic', 'XEN' ... 
- **()** are for grouping
  - '/(Homer|Marge) Simpson/' matches 'Homer Simpson' or 'Marge Simpson'
- **|** means OR
  - '/abc|def|g/' matches 'abc', 'def' or 'g'
- **^** beginning of the line, **$** for end of the line
  - '/^<!--$/' matches a line consisting entirely of '<!--'
- \ starts an escape sequence
  - many characters must be escaped to match them literally: /\$.[]()^*+?
  - '/<br\\/>/‘ matches lines containing <br/> tags
- \* means 0 or more occurences
  - '/abc*/' matches 'ab', 'abc', 'abcc', 'abccc' ...
  - '/a(bc)*/' matches "a", "abc", "abcbc", "abcbcbc" ...
  - "/a.*a/" matches "aa", "aba", "a8qa", "a!?_a" ...
- **+** means 1 or more occurrences
  - "/a(bc)+/" matches "abc", "abcbc", "abcbcbc" ...
  - "/Goo+gle/" matches "Google", "Gooogle", "Goooogle" ...
- **?** means 0 or 1 occurrences
  - "/a(bc)?/" matches "a" or "abc"
- **{min,max}** means between **min** and **max** occurences (inclusive)
  - "/a(bc){2,4}/" matches "abcbc", "abcbcbc" or "abcbcbcbc"
  - min or max can be ommited to specify any number
    - {2,} means 2 or more
    - {,6} means up to 6
    - {3} exactly 3
## Character sets:
- **[]** group characters into a set; will match any **single** character from set
  - "/[bcd]art/" matches strings containing "bart", "cart" and "dart"
  - equivalent to "/(b|c|d)art/" but shorter
  - Inside [], many of the modifier keys act as normal characters
    - "/what[!*?]*/" matches "what", "what!", "what?**!", "what??!" 
- Inside a set, specify a range of characters with hyphen **-**
  - "/[a-z]/" matches any lowercase letter
  - "/[a-zA-Z0-9]/" matches any lower or uppercase letter or digit
- An initial **^** inside a set negates it
  - "/[^abcd]/" matches any character other than a, b, c, d


## Escape sequences:
- Special escape sequence character sets
  - \d matches any digit (same as [0-9])
  - \D matches any non-digit (same as [^0-9])
  - \w matches any "word character" (same as [a-zA-Z_0-9]
  - \W matches any "non-word character"
  - \s matches any whitespace character ( , \t, \n, etc)
  - \S matches any non-whitespace
### Example:
> Write regular expressions for a username: 3 to 16 characters long containing letters, numbers, the _ and - characters:
>  /^[a-z0-9_-]{3,16}$/ matches "ilovemyself12_3-"
