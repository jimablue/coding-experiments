# Regex

quick tips
---
`[\w\.\-]*` for any character set of abitray length  
`(\d+)?` group can be optional 

cheat sheet
---
`.`  selects any character, including special characters and spaces.  
`[abc]` character set   
`[^abc]` negated character set     
`[a-z]` Letter Range
`[0-9]` number Range 

`*` after a character to indicate that the character may either not match at all or can match many times
`+` can occur one or more times  
`?` indicate a character is optional 

`{n}` a certain number of occurrences of a character
`{n,}` at least a certain number of occurrences of a character
`{x,y}` interval of occurrences 

`()` grouping  
`(ha)-\1,(haa)-\2` group name variable 
`(?: )` Non-capturing Grouping   
`|` allow different expressions
`|` escape character

`^` Selecting by Line Start  
`$` Selecting by End of Line  
`\w` word char  `\W` Except Word Character   
`\d` Number Character `\D` except  
`\s` space `\S` except Space  

>lookaround

`(?=)` Positive Lookahead, match after 
`(?!)` Negative Lookahead 
`(?<=)` Positive Lookbehind, match before 
`(?<!)` Negative Lookbehind   

>Flags

`/ ... /g` global, select all matches `/m` for multiline `/i` for case insensitive

>Lazy matching

greedy macthing by default, won't stop after the first match.   
`.*?r` lazy matching: add ? after * to find the first match that ends with the letter r and is preceded by any character. 