
open and read html file
```
with open('./xxx.html', 'r') as f:
    file = f.read()
    contents = BeautifulSoup(file, 'html.parser')
    programs = contents.find_all('section',attrs={'style':"text-align: unset;box-sizing: border-box;"})
```
  
find(), find_all(), find_next()
` element.find('a', attrs={'style':'...'})`

selector for different syntax
`element.selector()` 
  
get text in an element 
`element.text`