# Python Notes
---
### String Methods

1.  `capitalise()` - The `capitalize()`  method returns a string where the first character is upper case.

    ````python
    txt = "hello, and welcome to my world."
    x = txt.capitalize()
    print (x)
    # Output -  Hello, and welcome to my world.
    ````

2. `casefold()` - The `casefold()` method returns a string where all the characters are lower case.

    ````python
    txt = "Hello, And Welcome To My World!"
    x = txt.casefold()
    print(x)
    # Output - hello, and welcome to my world!
    ````

3. `center()` - The `center()` method will center align the string, using a specified character (space is default) as the fill character.

    **Syntax** - `string.center(length, character)`

    ````python
    txt = "banana"
    x = txt.center(20)
    print(x)
    # Output -          banana 
    
    x = txt.center(20, "O")
    # Output - OOOOOOObananaOOOOOOO
    ````

4. `count()` - The `count()` method returns the number of times a specified value appears in the string.

    **Syntax** - `string.count(value, start, end)`

    ````python
    txt = "I love apples, apple are my favorite fruit"
    x = txt.count("apple")
    print(x)
    # Output - 2
    
    x = txt.count("apple", 10, 24)
    # Output - 1
    ````

5. `encode()` -The `encode()` method encodes the string, using the specified encoding. If no  encoding is specified, UTF-8 will be used.

    **Syntax** - `string.encode(encoding=encoding, errors=errors)`

    | Parameter Values  |                                                                       |
    | ----------------- | --------------------------------------------------------------------- |
    | backslashreplace  | - uses a backslash instead of the character that could not be encoded |
    | ignore            | - ignores the characters that cannot be encoded                       |
    | namereplace       | - replaces the character with a text explaining the character         |
    | strict            | - Default, raises an error on failure                                 |
    | replace           | - replaces the character with a questionmark                          |
    | xmlcharrefreplace | - replaces the character with an xml character                        |
    

6.  `expandtabs()` -The `expandtabs()` method sets the tab size to the specified number of whitespaces.

    **Syntax** - `string.exandtabs(tabsize)`

    ````python
    txt = "H\te\tl\tl\to"
    
    print(txt)
    print(txt.expandtabs())
    print(txt.expandtabs(2))
    print(txt.expandtabs(4))
    print(txt.expandtabs(10))
    """ Output -
    H       e       l       l       o
    H       e       l       l       o
    H e l l o
    H   e   l   l   o
    H         e         l         l         o
    """
    ````

7. `format()` - The `format()` method formats the specified value(s) and insert them inside the string's placeholder.

    **Syntax** - `string.format(value1, value2...)`

    ````python
    #named indexes:
    txt = "My name is {fname}, I'm {age}".format(fname = "John", age = 36)
    #numbered indexes:
    txt = "My name is {0}, I'm {1}".format("John",36)
    #empty placeholders:
    txt = "My name is {}, I'm {}".format("John",36)
    
    print(txt)
    """ Output -
    My name is John, I'm 36
    My name is John, I'm 36
    My name is John, I'm 36
    """
    ########## Formating Types ###########
    txt = "We have {:<8} chickens." #Use "<" to left-align the value:
    print(txt.format(49))
    # Output We have 49       chickens.
    
    txt = "We have {:>8} chickens." #Use ">" to right-align the value:
    print(txt.format(49))
    # Output - We have       49 chickens.
    
    txt = "We have {:^8} chickens." #Use "^" to center-align the value:
    print(txt.format(49))
    # Output - We have    49    chickens.
    
    txt = "The temperature is {:=8} degrees celsius." #Use "=" to place the plus/minus sign at the left most position:
    print(txt.format(-5))
    # Output - The temperature is -      5 degrees.
    
    txt = "The temperature is between {:+} and {:+} degrees celsius." #Use "+" to always indicate if the number is positive or negative:
    print(txt.format(-3, 7))
    # Output - The temperature is between -3 and +7 degrees celsius.
    
    txt = "The temperature is between {:-} and {:-} degrees celsius." #Use "-" to always indicate if the number is negative (positive numbers are displayed without any sign):
    print(txt.format(-3, 7))
    # Output - The temperature is between -3 and 7 degrees celsius.
    
    txt = "The temperature is between {: } and {: } degrees celsius." #Use " " (a space) to insert a space before positive numbers and a minus sign before negative numbers:
    print(txt.format(-3, 7))
    # Output - The temperature is between -3 and  7 degrees celsius.
    
    txt = "The universe is {:,} years old." #Use "," to add a comma as a thousand separator:
    print(txt.format(13800000000))
    # Output - The universe is 13,800,000,000 years old.
    
    txt = "The universe is {:_} years old."#Use "_" to add a underscore character as a thousand separator:
    print(txt.format(13800000000))
    # Output - The universe is 13_800_000_000 years old.
    
    txt = "The binary version of {0} is {0:b}" #Use "b" to convert the number into binary format:
    print(txt.format(5))
    # Output - The binary version of 5 is 101
    
    txt = "We have {:d} chickens." #Use "d" to convert a number, in this case a binary number, into decimal number format:
    print(txt.format(0b101))
    # Output - We have 5 chickens.
    
    txt = "We have {:e} chickens." #Use "e" to convert a number into scientific number format (with a lower-case e):
    print(txt.format(5))
    # Output - We have 5.000000e+00.
    
    txt = "We have {:E} chickens." #Use "E" to convert a number into scientific number format (with an upper-case E):
    print(txt.format(5))
    # Output - We have 5.000000E+00.
    
    txt = "The price is {:.2f} dollars." #Use "f" to convert a number into a fixed point number, default with 6 decimals, but use a period followed by a number to specify the number of decimals:
        print(txt.format(45))
    txt = "The price is {:f} dollars."#without the ".2" inside the placeholder, this number will be displayed like this:
        print(txt.format(45))
    # Output - #The price is 45.00 dollars.
                #The price is 45.000000 dollars.
    
    x = float('inf') #Use "F" to convert a number into a fixed point number, but display inf and nan as INF and NAN:
    txt = "The price is {:F} dollars."
        print(txt.format(x))
    txt = "The price is {:f} dollars." #same example, but with a lower case f:
        print(txt.format(x))
    # Output - #The price is INF dollars.
                #The price is inf dollars.
    
    txt = "The octal version of {0} is {0:o}" #Use "o" to convert the number into octal format:
    print(txt.format(10))
    # Output - The octal version of 10 is 12
    
    txt = "The Hexadecimal version of {0} is {0:x}" #Use "x" to convert the number into Hex format:
    print(txt.format(255))
    # Output - The Hexadecimal version of 255 is ff
    
    txt = "The Hexadecimal version of {0} is {0:X}" #Use "X" to convert the number into upper-case Hex format:
    print(txt.format(255))
    # Output - The Hexadecimal version of 255 is FF
    
    txt = "You scored {:%}" #Use "%" to convert the number into a percentage format:
        print(txt.format(0.25))
    txt = "You scored {:.0%}" #Or, without any decimals:
        print(txt.format(0.25))
    # Output - #You scored 25.000000%
                #You scored 25%
    
                        ####   Other formating types   ####
    #  :n		Number format 
    #  :g		General format
    #  :c		Converts the value into the corresponding unicode character
    ````

8. `format_map()` - Formats specified values in a string.

    ````python
    point = {'x':4,'y':-5}
    print('{x}'.format_map(point))
    # Output - 4
    point = {'x':4,'y':-5, 'z': 0}
    print('{x} {y} {z}'.format_map(point))
    # Output - 4 -5 0
    ````

9.  `index()` - The `index()` method finds the first occurrence of the specified value.

      **Syntax** -  `string.index(value, start, end)`

    ````python
    txt = "Hello, welcome to my world."
    
    x = txt.index("welcome")
    print(x)
    # Output - 1
    
    x = txt.index("e", 5, 10)
    # Output - 8
    
    """ The index() method is almost the same as the find() method, the only difference is that the find() method returns -1 if the value is not found."""
    
    print(txt.find("q"))
    print(txt.index("q")) # 
    """ Output - 
    -1
    Traceback (most recent call last):
        File "demo_ref_string_find_vs_index.py", line 4 in <module>
        print(txt.index("q"))
    ValueError: substring not found """
    ````

10. `rindex()` -  If the value is not found, the `rfind()` method returns -1, but the `rindex()` method will raise an exception.
11. `find()` - The `find()` method finds the first occurrence of the specified value.

    **Syntax** -  `string.find(value, start, end)`

    ````python
    txt = "Hello, welcome to my world."
    
    x = txt.find("e")
    print(x)
    # Output - 1
    
    x = txt.find("e", 5, 10)
    # Output - 8
    ````

12. `rfind()` - The `rfind()` method finds the last occurrence of the specified value.

    **Syntax** -  `string.rfind(value, start, end)`

    ````python
    txt = "Hello, welcome to my world."
    x = txt.rfind("e")
    print(x)
    # Output - 13
    
    x = txt.rfind("e", 5, 10)
    # Output - 8
    ````

13. `isalnum()` method returns True if all the characters are alphanumeric, meaning alphabet letter (a-z) and numbers (0-9).
14. `isalpha()` returns True if all characters in the string are in the alphabet.
15. `isdecimal()` method returns True if all the characters are decimals (0-9).
16. `isdigit()` method returns True if all the characters are digits, otherwise False.  

    **Note** - Exponents, like ², are also considered to be a digit.

17. `isidentifier()` method returns True if the string is a valid identifier, otherwise False.  

    **Note** - A string is considered a valid identifier if it only contains alphanumeric letters (a-z) and (0-9), or underscores (_). A valid identifier cannot start with a number, or contain any spaces.

18. `islower()` method returns True if all the characters are in lower case, otherwise False.
19. `isnumeric()` returns True if all characters in the string are numeric.
20. `isprintable()` returns True if all characters in the string are printable. 
21. `isspace()` returns True if all characters in the string are whitespaces.
22. `istitle()` method returns True if all words in a text start with a upper case letter, AND the rest of the word are lower case letters, otherwise False. 
23. `isupper()` returns True if all characters in the string are upper case.
24. `join()` - The `join()` method takes all items in an iterable and joins them into one string. 

    **Note** -
    1. When using a dictionary as an iterable, the returned values are the keys, not the values.

    2. A string must be specified as the separator.

    ````python
    myTuple = ("John", "Peter", "Vicky")
    x = "#".join(myTuple)
    print(x)
    # Output - John#Peter#Vicky
    
    myDict = {"name": "John", "country": "Norway"}
    mySeparator = "TEST"
    x = mySeparator.join(myDict)
    print(x)
    # Output - nameTESTcountry
    ````

25. `ljust()` - The `ljust()` method will left align the string, using a specified character (space is default) as the fill character.

      **Syntax** -  `string.ljust(length, character)`

    ````python
    txt = "banana"
    x = txt.ljust(20)
    print(x, "is my favorite fruit.")
    # Output - banana              is my favorite fruit. //there are actually 14 whitespaces to the right of the word banana.
    
    x = txt.ljust(20, "O")
    print(x)
    # Ouput- bananaOOOOOOOOOOOOOO
    ````
26. `rjust()` returns a right justified version of the string.
27. `lower()` - The `lower()` method returns a string where all characters are lower case.
28. `upper()` converts a string into upper case.
29. `lstrip()` - The `lstrip()` method removes any leading characters (space is the default leading character to remove)

    ````python
    txt = "     banana     "
    x = txt.lstrip()
    print("of all fruits", x, "is my favorite")
    # Output - of all fruits banana     is my favorite
    
    txt = ",,,,,ssaaww.....banana"
    x = txt.lstrip(",.asw")
    print(x)
    # Output - banana
    ````

30. `rstrip()`method removes any trailing characters (characters at the end a string), space is the default trailing character to remove.
    
31. `maketrans()` returns a translation table to be used in translations. The `maketrans()` method returns a translation table with a 1-to-1 mapping of a Unicode ordinal to its translation/replacement.

    ````python
    # example dictionary
    dict = {"a": "123", "b": "456", "c": "789"}
    string = "abc"
    print(string.maketrans(dict))
    # Output - {97: '123', 98: '456', 99: '789'} // unicode number (97 for 'a' so on..)
    
    # example dictionary
    dict = {97: "123", 98: "456", 99: "789"}
    string = "abc"
    print(string.maketrans(dict))
    # Output - {97: '123', 98: '456', 99: '789'}
    ````

32. `partition()` -  The `partition()` method searches for a specified string, and splits the string into a tuple containing three elements.

    ````python
    txt = "I could eat bananas all day"
    x = txt.partition("bananas")
    print(x)
    # Output - ('I could eat ', 'bananas', ' all day') //This method search for the first occurrence of the specified string.
    
    x = txt.partition("apples")
    # Output - ('I could eat bananas all day', '', '')
    ````

33. `rpartition()` method searches for the last occurrence of a specified string, and splits the string into a tuple containing three elements.

    ````python
    txt = "I could eat bananas all day, bananas are my favorite fruit"
    x = txt.rpartition("bananas")
    print(x)
    # Output - ('I could eat bananas all day, ', 'bananas', ' are my favorite fruit')
    ````

34. `replace()` - The `replace()` method replaces a specified phrase with another specified phrase. 

    **Syntax** -  `string.replace(oldvalue, newvalue, count)`

    ````python
    txt = "I like bananas" 
    x = txt.replace("bananas", "apples")
    print(x)
    # Ouput - I like apples
    
    txt = "one one was a race horse, two two was one too." #Replace all occurrence of the word "one"
    x = txt.replace("one", "three")
    print(x)
    # Output - three three was a race horse, two two was three too."
    
    txt = "one one was a race horse, two two was one too." #Replace the two first occurrence of the word "one"
    x = txt.replace("one", "three", 2)
    print(x)
    # Output - three three was a race horse, two two was one too."
    ````

35. `endswith()` - The `endswith()` method returns True if the string ends with the specified value, otherwise False.  

    **Syntax** - `string.endswith(value, start, end)`

    ````python
    txt = "Hello, welcome to my world."
    
    x = txt.endswith("my world.")
    print(x)
    # Output - True
    
    x = txt.endswith("my world.", 5, 11)
    # Output - False     
    ````

36. `rsplit()` - The `rsplit()` method splits a string into a list, starting from the right. If no "max" is specified, this method will return the same as the split() method.

    **Syntax** - `string.rsplit(separator, maxsplit)`

    **Note**: When maxsplit is specified, the list will contain the specified number of elements plus one.

    ````python
    txt = "apple, banana, cherry"
    x = txt.rsplit(", ")
    print(x)
    # Output - ['apple', 'banana', 'cherry']
    
    txt = "apple, banana, cherry"
    x = txt.rsplit(", ", 1) # setting the maxsplit parameter to 1, will return a list with 2 elements!
    print(x)
    # Output - ['apple, banana', 'cherry']
    ````

37. `split()` - The `split()` method splits a string into a list. You can specify the separator, default separator is any whitespace.

    **Syntax** - `string.split(separator, maxsplit)`

38. `splitlines()` - The `splitlines()` method splits a string into a list. The splitting is done at line breaks.

    **Syntax** - `string.splitlines(keeplinebreaks)`

    ````python
    txt = "Thank you for the music\nWelcome to the jungle"
    x = txt.splitlines()
    print(x)
    # Output - ['Thank you for the music', 'Welcome to the jungle']
    
    x = txt.splitlines(True) 
    # Output - ['Thank you for the music\n', 'Welcome to the jungle']  // keeplinebreaks specifies if the line breaks should be included (True), or not (False). Default value is not (False)
    ````

39. `startswith()` - The `startswith()` method returns True if the string starts with the specified value, otherwise False.

    **Syntax** - `string.startswith(value, start, end)`

    ````python
    txt = "Hello, welcome to my world."
    
    x = txt.startswith("Hello")
    print(x)
    # Output - True
    
    x = txt.startswith("wel", 7, 20)
    # Output - True
    ````

40. `strip()` - The `strip()` method removes any leading (spaces at the beginning) and trailing (spaces at the end) characters (space is the default leading character to remove)

    ````python
    txt = "     banana     "
    x = txt.strip()
    print("of all fruits", x, "is my favorite")
    # Output - of all fruits banana is my favorite
    
    txt = ",,,,,rrttgg.....banana....rrr"
    x = txt.strip(",.grt")
    print(x)
    # Output - banana
    ````

41. `swapcase()` - The `swapcase()` method returns a string where all the upper case letters are lower case and vice versa.

    ````python
    txt = "Hello My Name Is PETER"
    x = txt.swapcase()
    print(x)
    # Output - hELLO mY nAME iS peter
    ````

42. `title()` - The `title()` method returns a string where the first character in every word is upper case. Like a header, or a title.

    **Note** - If the word contains a number or a symbol, the first letter after that will be converted to upper case.

    ````python
    txt = "Welcome to my 2nd world"
    x = txt.title()
    print(x)
    # Output - Welcome To My 2Nd World
    
    txt = "hello b2b2b2 and 3g3g3g"
    x = txt.title()
    # Output - Hello B2B2B2 And 3G3G3G
    ````

43. `translate()` returns a string that is modified string of givens string according to given translation mappings.

    ````python
    # specifying the mapping   
    # using ASCII   
    translation = {103: None, 101: None, 101: None} 
        
    string = "geeks"
    print("Original string:", string) 
        
    # translate string 
    print("Translated string:",  
            string.translate(translation))
    
    #Output - #Original string: geeks
              #Translated string: ks
    ````

44. `zfill()` - The `zfill()` method adds zeros (0) at the beginning of the string, until it reaches the specified length.

    **Note** - If the value of the length parameter is less than the length of the string, no filling is done.

    ````python
    a = "hello"
    b = "welcome to the jungle"
    c = "10.000"
    
    print(a.zfill(10)) 
    print(b.zfill(10))
    print(c.zfill(10))
    """ Output - 
    00000hello
    welcome to the jungle
    000010.000 """
    ````

---

[Lists Method](https://www.notion.so/bafb573a00654ae795723039eaaabec6)

**Note** - Python does not have built-in support for Arrays, but Python Lists can be used instead.

1. `append()` - The `append()` method appends an element to the end of the list. 

    **Syntax** - `list.append(elmnt)` 

    **Note** - An element can be of any type (string, number, object etc.)

    ````python
    fruits = ["apple", "banana", "cherry"]
    fruits.append("orange")
    print(fruits)
    #Output - ['apple', 'banana', 'cherry', 'orange']
    
    a = ["apple", "banana", "cherry"]
    b = ["Ford", "BMW", "Volvo"]
    a.append(b)
    print(a)
    # Output - ['apple', 'banana', 'cherry', ["Ford", "BMW", "Volvo"]]
    ````

2. `clear()` - The `clear()` method removes all the elements from a list.

    ````python
    fruits = ["apple", "banana", "cherry"]
    fruits.clear()
    print(fruits)
    # Output - []
    ````

3. `copy()` - The `copy()` method returns a copy of the specified list.

    ````python
    fruits = ["apple", "banana", "cherry"]
    x = fruits.copy()
    print(x)
    # Output - ['apple', 'banana', 'cherry']
    ````

4. `count()` - The `count()` method returns the number of elements with the specified value.

    ````python
    fruits = ['apple', 'banana', 'cherry']
    x = fruits.count("cherry")
    print(x)
    # Output - 1
    
    points = [1, 4, 2, 9, 7, 8, 9, 3, 1] #Return the number of times the value 9 appears int the list.
    x = points.count(9)
    # Output - 2
    ````

5. The `extend()` method adds the specified list elements (or any iterable) to the end of the current list.

    **Note** - Required. Any iterable (list, set, tuple, etc.)

    ````python
    fruits = ['apple', 'banana', 'cherry']
    cars = ['Ford', 'BMW', 'Volvo']
    fruits.extend(cars)
    # Output - ['apple', 'banana', 'cherry', 'Ford', 'BMW', 'Volvo']
    
    fruits = ['apple', 'banana', 'cherry']
    points = (1, 4, 5, 9)
    fruits.extend(points)
    print(fruits)
    # Output - ['apple', 'banana', 'cherry', 1, 4, 5, 9] // Add a tuple to the fruits list.
    ````

6. `index()` - The `index()` method returns the position at the first occurrence of the specified value.

    ````python
    fruits = ['apple', 'banana', 'cherry']
    x = fruits.index("cherry")
    print(x)
    # Output - 2
    
    fruits = [4, 55, 64, 32, 16, 32]
    x = fruits.index(32)
    print(x)
    # Output - 3
    ````

7. `insert()` - The `insert()` method inserts the specified value at the specified position.

    **Syntax** - `list.insert(pos, elmnt)`

    ````python
    fruits = ['apple', 'banana', 'cherry']
    fruits.insert(1, "orange") # Insert the value "orange" as the second element of the fruit list.
    # Output - ['apple', 'orange', 'banana', 'cherry']
    ````

8. `pop()` - The `pop()` method removes the element at the specified position.

    ````python
    fruits = ['apple', 'banana', 'cherry']
    fruits.pop(1) # Remove the second element of the fruit list:
    print(fruits)
    # Output - ['apple', 'cherry']
    
    x = fruits.pop(1) # Return the removed element
    print(x) 
    # Output - banana
    ````

9. `remove()` - The `remove()` method removes the first occurrence of the element with the specified value.

    ````python
    fruits = ['apple', 'banana', 'cherry']
    fruits.remove("banana") # Remove the "banana" element of the fruit list:
    print(fruits)
    # Output - ['apple', 'cherry']
    ````

10. `reverse()` - The `reverse()` method reverses the sorting order of the elements.

    ````python
    fruits = ['apple', 'banana', 'cherry']
    fruits.reverse()
    print(fruits)
    # Output - ['cherry', 'banana', 'apple']
    ````

11. `sort()` - The `sort()` method sorts the list ascending by default.

    **Syntax** - `list.sort(reverse=True|False, key=myFunc)`

    **Note** - You can also make a function to decide the sorting criteria(s).

    ````python
    cars = ['Ford', 'BMW', 'Volvo']
    
    cars.sort() # Sort the list alphabetically:
    print(cars)
    # Output - ['BMW', 'Ford', 'Volvo']
    
    cars.sort(reverse=True) # Sort the list descending.
    # Output - ['Volvo', 'Ford', 'BMW']
    
    #### Use of functions ####
    def myFunc(e): # A function that returns the length of the value.
        return len(e)
    cars = ['Ford', 'Mitsubishi', 'BMW', 'VW']
    cars.sort(key=myFunc)
    print(cars)
    # Output - ['VW', 'BMW', 'Ford', 'Mitsubishi']
    
    def myFunc(e): # Sort a list of dictionaries based on the "year" value of the dictionaries
        return e['year']
    cars = [
        {'car': 'Ford', 'year': 2005},
        {'car': 'Mitsubishi', 'year': 2000},
        {'car': 'BMW', 'year': 2019},
        {'car': 'VW', 'year': 2011}
    ]
    cars.sort(key=myFunc)
    print(cars)
    # Output - [{'car': 'Mitsubishi', 'year': 2000}, {'car': 'Ford', 'year': 2005}, {'car': 'VW', 'year': 2011}, {'car': 'BMW', 'year': 2019}]
    
    def myFunc(e): # A function that returns the length of the value:
        return len(e)
    cars = ['Ford', 'Mitsubishi', 'BMW', 'VW']
    cars.sort(reverse=True, key=myFunc)
    print(cars)
    # Output - ['Mitsubishi', 'Ford'', 'BMW', 'VW']
    ````

---

[Dictionary Methods](https://www.notion.so/716e8ce7db3d4771ac9e51c3615bdbc1)

1. `clear()` - The `clear()` method removes all the elements from a dictionary.

    ````python
    car =	{
        "brand": "Ford",
        "model": "Mustang",
        "year": 1964
    }
    car.clear()
    print(car)
    # Output - {}
    ````

2. `copy()` - The `copy()` method returns a copy of the specified dictionary.

    ````python
    car = {
        "brand": "Ford",
        "model": "Mustang",
        "year": 1964
    }
    x = car.copy()
    print(x)
    # Output - {'brand': 'Ford', 'model': 'Mustang', 'year': 1964}
    ````

3. `fromkeys()` - The `fromkeys()` method returns a dictionary with the specified keys and values.

    **Syntax** - `dict.fromkeys(keys, value)`

    ````python
    x = ('key1', 'key2', 'key3') # iterable
    y = 0
    thisdict = dict.fromkeys(x, y) # Create a dictionary with 3 keys, all with the value 0.
    print(thisdict)
    # Output - ['key1': 0, 'key2': 0, 'key3': 0]
    
    thisdict = dict.fromkeys(x) # without specifying the value
    # Output - ['key1': None, 'key2': None, 'key3': None]
    ````

4. `get()` - The `get()` method returns the value of the item with the specified key.

    **Syntax** - `dictionary.get(keyname, value)`

    ````python
    "brand": "Ford",
        "model": "Mustang",
        "year": 1964
    }
    x = car.get("model")
    print(x)
    # Output - Mustang
    
    x = car.get("price", 15000)
    # Output - 15000
    ````

5. `items()` - The `items()` method returns a view object. The view object contains the key-value pairs of the dictionary, as tuples in a list.

    ````python
    car = {
        "brand": "Ford",
        "model": "Mustang",
        "year": 1964
    }
    x = car.items()
    print(x)
    # Output - dict_items([('brand', 'Ford'), ('model', 'Mustang'), ('year', 1964)])
    ````

6. `keys()` - The `keys()` method returns a view object. The view object contains the keys of the dictionary, as a list.

    ````python
    car = {
        "brand": "Ford",
        "model": "Mustang",
        "year": 1964
    }
    x = car.keys()
    car["color"] = "white"
    print(x)
    # Output - dict_keys(['brand', 'model', 'year', 'color'])
    ````

7. `pop()` - The `pop()` method removes the specified item from the dictionary.

    **Syntax** - `dictionary.pop(keyname, defaultvalue)`

    ````python
    car = {
        "brand": "Ford",
        "model": "Mustang",
        "year": 1964
    }
    car.pop("model")
    print(car)
    # Output - {'brand': 'Ford', 'year': 1964}
    ````

8. `popitem()` - The `popitem()` method removes the item that was last inserted into the dictionary. In versions before 3.7, the popitem() method removes a random item.

    ````python
    car = {
        "brand": "Ford",
        "model": "Mustang",
        "year": 1964
    }
    x = car.popitem()
    print(x)
    # Output - ('year', 1964)
    ````

9. `setdefault()` - The `setdefault()` method returns the value of the item with the specified key.

    **Syntax** - `dictionary.setdefault(keyname, value)`

    ````python
    car = {
        "brand": "Ford",
        "model": "Mustang",
        "year": 1964
    }
    x = car.setdefault("color", "White")
    print(x)
    # Output - White
    ````

10. `update()` - The `update()` method inserts the specified items to the dictionary. The specified items can be a dictionary, or an iterable object.

    ````python
    car = {
        "brand": "Ford",
        "model": "Mustang",
        "year": 1964
    }
    car.update({"color": "White"})
    print(car)
    # Output - {'brand': 'Ford', 'model': 'Mustang', 'year': 1964, 'color': 'White'}
    ````

11. `values()` - The `values()` method returns a view object. The view object contains the values of the dictionary, as a list.

    ````python
    car = {
        "brand": "Ford",
        "model": "Mustang",
        "year": 1964
    }
    x = car.values()
    car["year"] = 2018
    print(x)
    # Output - dict_values(['Ford', 'Mustang', 2018])
    ````

---

[Tuple Methods](https://www.notion.so/b4d17e07d78d4de28d26bcaa188fb1bb)

1. `count()` - The `count()` method returns the number of times a specified value appears in the tuple.

    ````python
    thistuple = (1, 3, 7, 8, 7, 5, 4, 6, 8, 5)
    x = thistuple.count(5)
    print(x)
    # Output - 2
    ````

2. `index()` - The `index()` method finds the first occurrence of the specified value.

    ````python
    thistuple = (1, 3, 7, 8, 7, 5, 4, 6, 8, 5)
    x = thistuple.index(8)
    print(x)
    # Output - 3
    ````

---

[Set Methods](https://www.notion.so/7931ec2b43af4e439e8eea7adf6ff4bc)

1. `add()` -  The `add()` method adds an element to the set.

    **Note** - If the element already exists, the add() method does not add the element.

    ````python
    thisset = {"apple", "banana", "cherry"}
    thisset.add("orange")
    print(thisset)
    # Output - {'orange', 'banana', 'apple', 'cherry'}
    ````

2. `difference()` - The `difference()` method returns a set that contains the difference between two sets. Its means the returned set contains items that exist only in the first set, and not in both sets.

    ````python
    x = {"apple", "banana", "cherry"}
    y = {"google", "microsoft", "apple"}
    z = x.difference(y) 
    print(z)
    # Output - {'banana', 'cherry'}
    ````

3. `difference_update()` - The `difference_update()` method removes the items that exist in both sets.

    **Note**- The `difference_update()` method is different from the `difference()` method, because the `difference()` method returns a new set, without the unwanted items, and the `difference_update()` method removes the unwanted items from the original set.

    ````python
    x = {"apple", "banana", "cherry"}
    y = {"google", "microsoft", "apple"}
    x.difference_update(y) 
    print(x)
    # Output - {'banana', 'cherry'}
    ````

4. `discard()` - The `discard()` method removes the specified item from the set. Where the `remove()` method will raise an error.

    ````python
    thisset = {"apple", "banana", "cherry"}
    thisset.discard("banana")
    print(thisset)
    # Output - {'cherry', 'apple'} 
    ````

5. `intersection()` - The `intersection()` method returns a set that contains the similarity between two or more sets. 

    **Syntax** -  `set.intersection(set1, set2 ... etc)`

    ````python
    x = {"apple", "banana", "cherry"}
    y = {"google", "microsoft", "apple"}
    z = x.intersection(y) 
    print(z)
    # Output - {'apple'}
    ````

6. `intersection_update()` -  The `intersection_update()` method removes the items that is not present in both sets (or in all sets if the comparison is done between more than two sets).

    ````python
    x = {"a", "b", "c"}
    y = {"c", "d", "e"}
    z = {"f", "g", "c"}
    x.intersection_update(y, z)
    print(x)
    # Output - {'c'}
    ````

7. `isdisjoint()` - The `isdisjoint()` method returns True if none of the items are present in both sets, otherwise it returns False.

    ````python
    x = {"apple", "banana", "cherry"}
    y = {"google", "microsoft", "facebook"}
    z = x.isdisjoint(y) 
    print(z)
    # Output - True
    ````

8. `issubset()` method returns True if all items in the set exists in the specified set, otherwise it returns False.

    ````python
    x = {"a", "b", "c"}
    y = {"f", "e", "d", "c", "b", "a"}
    z = x.issubset(y) 
    print(z)
    # Output - True
    ````

9. The `issuperset()` method returns True if all items in the specified set exists in the original set, otherwise it retuns False.

    ````python
    x = {"f", "e", "d", "c", "b"}
    y = {"a", "b", "c"}
    z = x.issuperset(y)
    print(z)
    # Output - False
    ````

10. `symmetric_difference()` - The `symmetric_difference()` method returns a set that contains all items from both set, but not the items that are present in both sets.

    ````python
    x = {"apple", "banana", "cherry"}
    y = {"google", "microsoft", "apple"}
    z = x.symmetric_difference(y) 
    print(z)
    # Output - {'cherry', 'microsoft', 'banana', 'google'}
    ````

11. `symmetric_difference_update()` - The `symmetric_difference_update()` method updates the original set by removing items that are present in both sets, and inserting the other items.

    ````python
    x = {"apple", "banana", "cherry"}
    y = {"google", "microsoft", "apple"}
    x.symmetric_difference_update(y) 
    print(x)
    # Output - {'microsoft', 'google', 'banana', 'cherry'}
    ````

12. `union()` - The `union()` method returns a set that contains all items from the original set, and all items from the specified sets.

    **Syntax** - `set.union(set1, set2...)`

    ````python
    x = {"apple", "banana", "cherry"}
    y = {"google", "microsoft", "apple"}
    z = x.union(y) 
    print(z)
    # Output - {'google', 'banana', 'microsoft', 'apple', 'cherry'}
    ````

---

[File Methods](https://www.notion.so/8acf931e90984c8f9cc94a403847c069)

1. `close()` - The `close()` method closes an open file.

    **Note** - You should always close your files, in some cases, due to buffering, changes made to a file may not show until you close the file.

    ````python
    f = open("demofile.txt", "r") # Opens the file in read form
    print(f.read()) # Returns the file content and printg it to the screen
    f.close()
    ````

2. `fileno()` method returns the file descriptor of the stream, as a number.  

    **Note** - Descriptor is just an integer number that uniquely represents an opened file in operating system.

    ````python
    f = open("demofile.txt", "r")
    print(f.fileno())
    ````

3. `flush()` method cleans out the internal buffer.

    **Note** - The flush operation forces the file data into the file cache in RAM, and from there it's the OS's job to actually send it to the disk.

4. `isatty()` method returns True if the file stream is interactive, example: connected to a terminal device. As python also supports interaction with operating system.
5. `read()` returns the file content.
6. `readable()` method returns True if the file is readable, False if not.
7. `readline()` returns one line from the file.
8. `readlines()` method returns a list containing each line in the file as a list item.

    **Syntax** - `file.readlines(hint)`

    **Note** - Use the hint parameter to limit the number of lines returned. If the total number of bytes returned exceeds the specified number, no more lines are returned.

    ````python
    # Example Output
    ['Hello! Welcome to demofile.txt\n', 'This file is for testing purposes.\n', 'Good Luck!']
    ````

9. `seek()` method sets the current file position in a file stream. The `seek()` method also returns the new position.

    **Syntax** - `seek(offset[, whence])`

    ````python
    f.seek(3) # starts reading from the 3rd character
    f.seek(2, 1) # move two characters ahead from the current position
    f.seek(-3, 2) # move to the 3rd character from the end of the file
    ````

10. `seekable()` method returns True if the file is seekable, False if not.
11. `tell()` method returns the current file position in a file stream.

    Tip - You can change the current file position with the seek() method. 

12. `truncate()` method resizes the file to the given number of bytes. If the size is not specified, the current position will be used.

    **Syntax** - `file.truncate(size)`

    **Note** - The size of the file (in bytes) after the truncate. Default None, which means the current file stream position.

13. `writable()` method returns True if the file is writable, False if not. 

    A file is writable if it is opened using "a" for append or "w" for write.

14. `write()` writes the specified string to the file.
15. `writelines()` writes a list of strings to the file

    **Syntax** - `file.writelines(list)`

    `"a"`: The texts will be inserted at the current file stream position, default at the end of the file.

    `"w"`: The file will be emptied before the texts will be inserted at the current file stream position, default 0.

    ````python
    f.writelines(["See you soon!", "Over and out."]) # Open the file with "a" for appending, then add a list of texts to append to the file
    ````

---

[Built in Functions](https://www.notion.so/d0abfd6822404bbda897d63385620692)

1. `abs()` function returns the absolute value of the specified number.

    ````python
    x = abs(-7.25)
    print(x)
    # Output - 7.25
    ````

2. `all()` function returns True if all items in an iterable are true, otherwise it returns False. If the iterable object is empty, the all() function also returns True.

    ````python
    mylist = [True, True, True]
    x = all(mylist)
    print(x)
    # Output - True
    ````

3. `any()` function returns True if any item in an iterable are true, otherwise it returns False.

    **Syntax** - `any(iterable)`

    ````python
    mylist = [False, True, False]
    x = any(mylist)
    print(x)
    # Output - True
    ````

4. `ascii()` function returns a readable version of any object (Strings, Tuples, Lists, etc).

    **Syntax** - `ascii(object)`

    **Note** - `ascii()` function will replace any non-ascii characters with escape characters. `å` will be replaced with `\xe5`.

    ````python
    x = ascii("My name is Ståle")
    print(x)
    # Output - 'My name is St\e5le'
    ````

5. `bin()` function returns the binary version of a specified integer.

    ````python
    x = bin(36) # The result will always have the prefix 0b
    print(x)
    # Output - 0b100100
    ````

6. `bool()` function returns the boolean value of a specified object.

    The object will always return True, unless:

    - The object is empty, like [], (), {}
    - The object is False
    - The object is 0
    - The object is None

    ````python
    x = bool(1)
    print(x)
    # Output - True
    ````

7. `bytearray()` function returns a bytearray object.

    **Syntax** - `bytearray(x, encoding, error)`

    - source (Optional) - source to initialize the array of bytes.
    - encoding (Optional) - if source is a string, the encoding of the string.
    - errors (Optional) - if source is a string, the action to take when the encoding conversion fails

    **Note** -  It can convert objects into bytearray objects, or create empty bytearray object of the specified size.

   <table class="tg">
     <tr>
       <th class="tg-0pky">Parameter</th>
       <th class="tg-0pky">Description</th>
     </tr>
     <tr>
       <td class="tg-0pky">x</td>
       <td class="tg-0pky">
       <ul>A source to use when creating the bytearray object.</ul> 
       <ul>If it is an integer, an empty bytearray object of the specified size will be created.</ul></td>
     </tr>
     <tr>
       <td class="tg-0pky">encoding</td>
       <td class="tg-0pky">The encoding of the string</td>
     </tr>
     <tr>
       <td class="tg-0pky">error</td>
       <td class="tg-0pky">Specifies what to do if the encoding fails.</td>
     </tr>
   </table>

    ````python
    string = "Python is interesting."
    arr = bytearray(string, 'utf-8') # Array of bytes from a string, string with encoding 'utf-8'
    print(arr)
    # Output - bytearray(b'Python is interesting.')
    
    size = 5
    arr = bytearray(size) # Array of bytes of given integer size
    print(arr)
    # Output - bytearray(b'\x00\x00\x00\x00\x00')
    
    rList = [1, 2, 3, 4, 5]
    arr = bytearray(rList) # Array of bytes from an iterable list
    print(arr)
    # Output - bytearray(b'\x01\x02\x03\x04\x05')
    ````

1. `bytes()` function returns a bytes object.

    **Syntax** - `bytes(x, encoding, error)`

    **Note** - The difference between `bytes()` and `bytearray()` is that `bytes()` returns an object that cannot be modified, and `bytearray()` returns an object that can be modified.

    ````python
    x = bytes(4)
    print(x)
    # Output - b'\x00\x00\x00\x00'
    ````

2. `callable()` function returns True if the specified object is callable, otherwise it returns False. A normal variable is not callable.

    ````python
    def x():
        a = 5
    print(callable(x))
    # Output - True
    ````

3.  `chr()` function returns the character that represents the specified unicode.

    **Syntax** - `chr(number)` 

    **Note** - An integer representing a valid Unicode code point

    ````python
    x = chr(97)
    print(x)
    # Output - a
    ````

4.  `compile()` function returns the specified source as a code object, ready to be executed.

    **Syntax** - `compile(source, filename, mode, flag, dont_inherit, optimize)`

    - `source` - a normal string, a byte string, or an AST object
    - `filename` - file from which the code was read. If it wasn't read from a file, you can give a name yourself
    - `mode` - Either `exec` or `eval` or `single`.
        - `eval` - accepts only a single expression.
        - `exec` - It can take a code block that has Python statements, class and functions and so on.
        - `single` - if it consists of a single interactive statement
    - `flags` (optional) and `dont_inherit` (optional) - controls which future statements affect the compilation of the source. Default Value: 0
    - `optimize` (optional) - optimization level of the compiler. Default value -1.

    ````python
    x = compile('print(55)\nprint(88)', 'test', 'exec')
    exec(x)
    """ Output - 
    55
    88 """
    ````

5.  `complex()` function returns a complex number by specifying a real number and an imaginary number.

    **Syntax** - `complex(real, imaginary)`

    - `real` - real part. If  is omitted, it defaults to 0.
    - `imaginary`- imaginary part. If  is omitted, it default to 0.

    ````python
    z = complex(2, -3)
    print(z)
    z = complex(1)
    z = complex()
    z = complex('5-9j')
    """ Output -
    (2-3j)
    (1+0j)
    0j
    (5-9j) """
    ````

6.  `delattr()` function will delete the specified attribute from the specified object.

    **Syntax** - `delattr(object, attribute)`

    ````python
    class Person:
        name = "John"
        age = 36
        country = "Norway"
    delattr(Person, 'age')
    # The Person object will no longer contain an "age" property
    ````

7.  `dict()` function creates a dictionary.
8.  `dir()` function returns all properties and methods of the specified object, without the values. This function will return all the properties and methods, even built-in properties which are default for all object.
9.  `divmod()` function returns a tuple containing the quotient and the remainder when argument1 (divident) is divided by argument2 (divisor).

    **Syntax** - `divmod(divident, divisor)`

    ````python
    x = divmod(5, 2)
    print(x)
    # Output - (2, 1)
    ````

10. `enumerate()` function takes a collection (e.g. a tuple) and returns it as an enumerate object.

    **Syntax** - `enumerate(iterable, start)`

    ````python
    x = ('apple', 'banana', 'cherry')
    y = enumerate(x)
    print(list(y))
    # Output - [(0, 'apple'), (1, 'banana'), (2, 'cherry')]
    
    y = enumerate(x, 10)
    print(list(y))
    # Output - [(10, 'apple'), (11, 'banana'), (12, 'cherry')]
    ````

11. `eval()` function evaluates the specified expression, if the expression is a legal Python statement, it will be executed.
12. `exec()` function executes the specified Python code.

    The `exec()` function accepts large blocks of code, unlike the `eval()` function which only accepts a single expression

    ````python
    program = 'a = 5\nb=10\nprint("Sum =", a+b)'
    exec(program)
    # Output - Sum = 15
    ````

13. `filter()` function returns an iterator were the items are filtered through a function to test if the item is accepted or not.

    **Syntax** - `filter(function, iterable)`

    ````python
    ages = [5, 12, 17, 18, 24, 32]
    def myFunc(x):
        if x < 18:
        return False
        else:
        return True
    adults = filter(myFunc, ages)
    for x in adults:
        print(x)
    """ Output - 
    18
    24
    32  """
    ````

14. `float()` function converts the specified value into a floating point number.
15. `frozenset()` function returns an unchangeable frozenset object (which is like a set object, only unchangeable).

    **Syntax** - `frozenset(iterable)`

16. `getattr()` function returns the value of the specified attribute from the specified object.

    **Syntax** - `getattr(object, attribute, default)`

    ````python
    class Person:
        name = "John"
        age = 36
        country = "Norway"
    x = getattr(Person, 'age') # Get the value of the "age" property of the "Person" object
    print(x)
    # Output - 36
    
    x = getattr(Person, 'page', 'my message') # Use the "default" parameter to write a message when the attribute does not exist
    # Output - my message
    ````

17. `globals()` function returns the global symbol table as a dictionary. A symbol table contains necessary information about the current program

    ````python
    x = globals()
    print(x["__file__"])
    # Output - demo_ref_globals2.py
    ````

18. `hasattr()` function returns True if the specified object has the specified attribute, otherwise False.

19. `hash()` returns the hash value of a specified object.

20. `help()` executes the built-in help system.

21. `hex()` converts a number into a hexadecimal value.

22.  The `id()` function returns a unique id for the specified object.
        - All objects in Python has its own unique id.
        - The id is assigned to the object when it is created.
        - The id is the object's memory address, and will be different for each time you run the program. (except for some object that has a constant unique id, like integers from -5 to 256)

23. `input()` allowing user input.

24. `int()` function converts the specified value into an integer number.

25. `isinstance()` function returns True if the specified object is of the specified type, otherwise False. If the type parameter is a tuple, this function will return True if the object is one of the types in the tuple.

    ````python
    x = isinstance(5, int)
    print(x)
    # Output - True
    
    x = isinstance("Hello", (str, float, int, str, list, dict, tuple)) # If is one of the types described in the type parameter:
    # Output - True
    
    class myObj:
        name = "John"
    y = myObj()
    x = isinstance(y, myObj)
    print(x)
    # Output - True
    ````

26. `issubclass()` function returns True if the specified object is a subclass of the specified object, otherwise False.

    ````python
    class myAge:
        age = 36
    class myObj(myAge):
        name = "John"
        age = myAge
    x = issubclass(myObj, myAge)
    print(x)
    # Output - True
    ````

27. `iter()` function returns an iterator object.

    If the object is a callable object the iteration will stop when the returned value is the same as the sentinel

    ````python
    x = iter(["apple", "banana", "cherry"])
    print(next(x))
    print(next(x))
    print(next(x))
    """ Output - 
    apple
    banana
    cherry """
    ````

28. `reversed()` function returns a reversed iterator object.

29. `next()` returns the next item in an iterable.

30. `len()` function returns the number of items in an object.

    **Note** - When the object is a string, the len() function returns the number of characters in the string.

31. `list()` returns a list.

32. `locals()` function returns the local symbol table as a dictionary. A symbol table contains necessary information about the current program.

33. `map()` function executes a specified function for each item in a iterable. The item is sent to the function as a parameter.

    **Syntax** - `map(function, iterables)`

    ````python
    def myfunc(a):
        return len(a)
    x = map(myfunc, ('apple', 'banana', 'cherry')) # Calculate the length of each word in the tuple.
    print(x)
    # Output - ['5', '6', '6']
    # convert the map into a list, for readability:
    print(list(x))
    
    def myfunc(a, b):
        return a + b
    x = map(myfunc, ('apple', 'banana', 'cherry'), ('orange', 'lemon', 'pineapple')) # Make new fruits by sending two iterable objects into the function
    print(x)
    # convert the map into a list, for readability:
    print(list(x))
    # Output - ['appleorange', 'bananalemon', 'cherrypineapple']
    ````

34. `max()` function returns the item with the highest value, or the item with the highest value in an iterable.

    **Syntax** - `max(n1, n2, n3, ...)` or `max(iterable)`

    **Note** - If the values are strings, an alphabetically comparison is done.

    ````python
    x = max(5, 10)
    print(x)
    # Output - 10
    
    x = max("Mike", "John", "Vicky") # Return the name with the highest value, ordered alphabetically.
    # Output - Vicky
    
    a = (1, 5, 3, 9)
    x = max(a) # Return the item in a tuple with the highest value.
    # Output - 9
    ````
       
35. `min()` returns the smallest item in an iterable.

36. `object()` function returns an empty object. This object is the base for all classes, it holds the built-in properties and methods which are default for all classes.
37. `oct()` converts a number into an octal.
38. `open()` opens a file and returns a file object.
39. `ord()` function returns the number representing the unicode code of a specified character.
40. `pow()` function returns the value of x to the power of y (x^y). If a third parameter is present, it returns x to the power of y, modulus z.

    **Syntax** - `pow(x, y, z)`

    ````python
    x = pow(4, 3) # Return the value of 4 to the power of 3 (same as 4  4  4).
    print(x)
    # Output - 64
    
    x = pow(4, 3, 5) # Return the value of 4 to the power of 3, modulus 5 (same as (4  4  4) % 5).
    # Output - 4
    ````

41. `print()` prints to the standard output device.

    **Syntax** - `property(fget, fset, fdel, doc)`

    - fget() – used to get the value of attribute.
    - fset() – used to set the value of attribute.
    - fdel() – used to delete the attribute value.
    - doc() – string that contains the documentation (docstring) for the attribute.
    - If no arguments are given, property() method returns a base property attribute that doesn’t contain any getter, setter or deleter.
    - If doc isn’t provided, property() method takes the docstring of the getter function.

    ````python
    # Python program to explain property() function 
    # Alphabet class 
    class Alphabet: 
        def __init__(self, value): 
            self._value = value 
        # getting the values 
        def getValue(self): 
            print('Getting value') 
            return self._value 
        # setting the values 
        def setValue(self, value): 
            print('Setting value to ' + value) 
            self._value = value 
        # deleting the values 
        def delValue(self): 
            print('Deleting value') 
            del self._value 
        value = property(getValue, setValue, delValue, ) 
    # passing the value 
    x = Alphabet('GeeksforGeeks') 
    print(x.value) 
    x.value = 'GfG'
    del x.value
    """ Output - 
    Getting value
    GeeksforGeeks
    Setting value to GfG
    Deleting value """
    ````

42. `range()` function returns a sequence of numbers, starting from 0 by default, and increments by 1 (by default), and ends at a specified number.

    **Syntax** - `range(start, stop, step)`

    ````python
    x = range(6) # Create a sequence of numbers from 0 to 5, and print each item in the sequence.
    for n in x:
    print(n)
    
    x = range(3, 6) # Create a sequence of numbers from 3 to 5, and print each item in the sequence.
    x = range(3, 20, 2) # Create a sequence of numbers from 3 to 19, but increment by 2 instead of 1.
    ````

43. `repr()` returns a readable version of an object.

    ````python
    s = 'Hello, Geeks.'
    print repr(s) 
    print repr(2.0/11.0)
    """ Output - 
    'Hello, Geeks.'
    0.18181818181818182 """
    ````

44. `round()` rounds the numbers.

    **Syntax** - `round(number, digits)`

    ````python
    x = round(5.76543, 2)
    print(x)
    # Output - 5.77
    
    x = round(5.76543)
    # Output - 6
    ````

45. `set()` returns a new set object.
46. `setattr()` function sets the value of the specified attribute of the specified object.

    **Syntax** - `setattr(object, attribute, value)`

    ````python
    class Person:
        name = "John"
        age = 36
        country = "Norway"
    setattr(Person, 'age', 40) # Change the value of the "age" property of the "person" object.
    x = getattr(Person, 'age')
    print(x)
    # Output - 40
    ````

47. `slice()` function returns a slice object.

    **Syntax** - `slice(start, end, step)`

    **Note** - A slice object is used to specify how to slice a sequence. You can specify where to start the slicing, and where to end. You can also specify the step, which allows you to e.g. slice only every other item.

    ````python
    a = ("a", "b", "c", "d", "e", "f", "g", "h")
    x = slice(3, 5) # Create a tuple and a slice object. Start the slice object at position 3, and slice to position 5, and return the result.
    print(a[x])
    # Output - ('d', 'e')
    
    a = ("a", "b", "c", "d", "e", "f", "g", "h")
    x = slice(0, 8, 3) # Create a tuple and a slice object. Use the step parameter to return every third item.
    print(a[x])
    # Output - ('a', 'd', 'g') 
    ````

48. `sorted()` function returns a sorted list of the specified iterable object.

    **Note** -  You cannot sort a list that contains BOTH string values AND numeric values.

    ````python
    a = (1, 11, 2)
    x = sorted(a)
    print(x)
    # Output - [1, 2, 11]
    
    a = ("h", "b", "a", "c", "f", "d", "e", "g") # Sort ascending.
    x = sorted(a)
    
    a = ("h", "b", "a", "c", "f", "d", "e", "g") # Sort descending.
    x = sorted(a, reverse=True)
    ````

49. `staticmethod()` built-in function returns a static method for a given function.

    **Syntax** - `staticmethod(function)`

    **Note** - Static methods, much like class methods, are methods that are bound to a class rather than its object. In newer versions of Python, you can use the Python decorator `@staticmethod` .

    ````python
    class Mathematics:
        def addNumbers(x, y):
            return x + y
    # create addNumbers static method
    Mathematics.addNumbers = staticmethod(Mathematics.addNumbers)
    print('The sum is:', Mathematics.addNumbers(5, 10))
    # Output - The sum is 15
    
    class Dates:
        def __init__(self, date):
            self.date = date  
        def getDate(self):
            return self.date
        @staticmethod
        def toDashDate(date):
            return date.replace("/", "-")
    date = Dates("15-12-2016")
    dateFromDB = "15/12/2016"
    dateWithDash = Dates.toDashDate(dateFromDB)
    if(date.getDate() == dateWithDash):
        print("Equal")
    else:
        print("Unequal")
    # Output - Equal
    ````

50. `classmethod()` converts a method into a class method.
51. `str()` returns a string object.
52. `tuple()` returns a tuple.
53. `sum()` function returns a number, the sum of all items in an iterable.

    **Syntax** - `sum(iterable, start)`

    ````python
    a = (1, 2, 3, 4, 5)
    x = sum(a) # Add all items in a tuple, and return the result.
    print(x)
    # Output - 15
    
    a = (1, 2, 3, 4, 5)
    x = sum(a, 7)
    # Output - 22
    ````

54. `super()` function is used to give access to methods and properties of a parent or sibling class. The `super()` function returns an object that represents the parent class.

    ````python
    class Parent:
        def __init__(self, txt):
        self.message = txt
        def printmessage(self):
        print(self.message)
    class Child(Parent):
        def __init__(self, txt):
        super().__init__(txt)
    x = Child("Hello, and welcome!")
    x.printmessage()
    # Output - Hello, and welcome!
    ````

55. `type()` returns the type of an object.
56. `vars()` function returns the dic attribute of an object. The dict attribute is a dictionary containing the object's changeable attributes.

    **Note** - calling the `vars()` function without parameters will return a dictionary containing the local symbol table.

57. `zip()` function returns a zip object, which is an iterator of tuples where the first item in each passed iterator is paired together, and then the second item in each passed iterator are paired together etc.

    **Syntax** - `zip(iterator1, iterator2, iterator3 ...)`

    **Note** - If one tuple contains more items, these items are ignored.

    ````python
    a = ("John", "Charles", "Mike")
    b = ("Jenny", "Christy", "Monica")
    x = zip(a, b)
    print(tuple(x)) #use the tuple() function to display a readable version of the result.
    # Output - (('John', 'Jenny'), ('Charles', 'Christy'), ('Mike', 'Monica'))
    ````

---

[Keywords](https://www.notion.so/6d04e6e92e2c4c679d0c9e202a7efee7)

1. `nonlocal` keyword is used to work with variables inside nested functions, where the variable should not belong to the inner function.

    ````python
        def myfunc1():
          x = "John"
          def myfunc2():
            nonlocal x
            x = "hello"
          myfunc2() 
          return x
        print(myfunc1())
        # hello
    ````

2. `assert` keyword is used when debugging code. The assert keyword lets you test if a condition in your code returns True, if not, the program will raise an AssertionError.

    ````python
        x = "hello"
        assert x == "hello" # if condition returns True, then nothing happens.
        assert x == "goodbye" # if condition returns False, AssertionError is raised.
        
        assert x == "goodbye", "x should be 'hello'" # if condition returns False, AssertionError is raised.
        """ Output - 
        assert x == "goodbye", "x should be 'hello'"
        AssertionError: x should be 'hello' """
    ````

3. `with` statement in Python is used in exception handling to make the code cleaner and much more readable. It simplifies the management of common resources like file streams.

[Random Module](https://www.notion.so/04e4dad285b446e6ba29fa76512e904b)

1. `getrandbits()` method returns an integer in the specified size (in bits).

    ````python
    import random
    print(random.getrandbits(8)) # Return an 8 bits sized integer.
    ````

2. `randrange()` method returns a randomly selected element from the specified range.

    **Syntax** - `random.randrange(start, stop, step)`

    - `step` - An integer specifying the incrementation.

    ````python
    import random
    print(random.randrange(3, 9)) # returns a number between 3 (included) and 9 (not included)
    ````

3. `randint()` method returns an integer number selected element from the specified range.

    ````python
    import random
    print(random.randint(3, 9)) # returns a number between 3 and 9 (both included)
    ````

4. `choice()` method returns a randomly selected element from the specified sequence. The sequence can be a string, a range, a list, a tuple or any other kind of sequence.

    ````python
    import random
    mylist = ["apple", "banana", "cherry"]
    print(random.choice(mylist)) # Return a random element from a list.
    # Output - banana
    
    x = "WELCOME"
    print(random.choice(x)) # Return a random character from a string.
    # Output - L
    ````

5. `choices()` method returns a list with the randomly selected element from the specified sequence.

    **Syntax** - `random.choices(sequence, weights=None, cum_weights=None, k=1)`

    - `sequence` like a list, a tuple, a range of numbers etc.
    - `weights` list were you can weigh the possibility for each value.
    - `cum_weights` list were you can weigh the possibility for each value, only this time the possibility is accumulated. Example: normal weights list: [2, 1, 1] is the same as this cum_weights list; [2, 3, 4].
    - `k` An integer defining the length of the returned list.

    ````python
    import random
    mylist = ["apple", "banana", "cherry"]
    print(random.choices(mylist, weights = [10, 1, 1], k = 14))
    # Output - [apple, apple, apple, apple, apple, apple, apple, apple, apple, apple, apple, apple, apple, apple]
    ````

6. `shuffle()` method takes a sequence (list, string, or tuple) and reorganize the order of the items.

    **Syntax** - `random.shuffle(sequence, function)`

    ````python
    import random
    mylist = ["apple", "banana", "cherry"]
    random.shuffle(mylist) # Shuffle a list (reorganize the order of the list items).
    print(mylist)
    # Output - ['cherry', 'apple', 'banana']
    
    def myfunction(): # The name of a function that returns a number between 0.0 and 1.0.
        return 0.1  
    mylist = ["apple", "banana", "cherry"]
    random.shuffle(mylist, myfunction)
    # Output - ["banana", "cherry", "apple"]
    ````

7. `sample()` method returns a list with a randomly selection of a specified number of items from a sequence.

    **Syntax** - `random.sample(sequence, k)`

    `k` - size of the returned list.

    `sequence` - Can be any sequence: list, set, range etc.

    ````python
    import random
    mylist = ["apple", "banana", "cherry"]
    print(random.sample(mylist, k=2)) # Return a list that contains any 2 of the items from a list.
    # Output - ['banana', 'apple']
    ````

8. `random()` method returns a random floating number between 0 and 1.

    ````python
    import random
    print(random.random()) # Return random number between 0.0 and 1.0.
    # Output - 0.3561814038588462
    ````

9. `uniform()` method returns a random floating number between the two specified numbers (both included).

    **Syntax** - `random.uniform(a, b)`

    ````python
    import random
    print(random.uniform(20, 60)) # Return a random number between, and included, 20 and 60.
    # Output- 47.78648754710303
    ````

10. `triangular()` method returns a random floating number between the two specified numbers (both included), but you can also specify a third parameter, the mode parameter.

    **Syntax** - `random.triangular(low, high, mode)`

    `mode` parameter gives you the opportunity to weigh the possible outcome closer to one of the other two parameter values.

    ````python
    import random
    print(random.triangular(20, 60, 30)) # Return a random number between, and included, 20 and 60, but most likely closer to 20.
    # Output - 38.258022361224484
    ````

---

# Request module in python

- The requests module allows you to send HTTP requests using Python.
- The HTTP request returns a Response Object with all the response data (content, encoding, status, etc).
- Use `pip install requests` to download.
- **Syntax** - `requests.methodname(params)` .

  [Module Methods](https://www.notion.so/bd87a7addbb0451a811ef3cc96b4f61d)

  [Response Object](https://www.notion.so/06c41f62ee8c492084e6376aacaac88a)

  [Parameter Values](https://www.notion.so/8c54dd12933449b7880ba9badfcb1cc0)

- `delete()` method sends a DELETE request to the specified url. DELETE requests are made for deleting the specified resource (file, record etc).

    **Syntax** - `requests.delete(url, args)`

    ````python
    import requests
    url = 'https://w3schools.com/python/demopage.php'
    x = requests.delete(url) # Make a request to a web page, and print the response text.
    print(x.text) # printing response object "text"
    ````
    
    Use the above `delete()` **Syntax** for all methods and objects.

---

# JSON in python

You can convert Python objects of the following types, into JSON strings:

- dict
- list
- tuple
- string
- int
- float
- True
- False
- None

   [Python objects are converted into the JSON (JavaScript) equivalent:](https://www.notion.so/9399e86dd87f43b09cc52de56c3e004a)

    ````python
    import json
    # Convert Python objects into JSON strings, and print the values:
    print(json.dumps({"name": "John", "age": 30}))
    print(json.dumps(["apple", "bananas"]))
    print(json.dumps(("apple", "bananas")))
    print(json.dumps("hello"))
    print(json.dumps(42))
    print(json.dumps(31.76))
    print(json.dumps(True))
    print(json.dumps(False))
    print(json.dumps(None))
    """ Ouput -
    {"name": "John", "age": 30}
    ["apple", "bananas"]
    ["apple", "bananas"]
    "hello"
    42
    31.76
    true
    false
    null
    """
    
    # Convert a Python object containing all the legal data types:
    import json
    x = {
      "name": "John",
      "age": 30,
      "married": True,
      "divorced": False,
      "children": ("Ann","Billy"),
      "pets": None,
      "cars": [
        {"model": "BMW 230", "mpg": 27.5},
        {"model": "Ford Edge", "mpg": 24.1}
      ]
    }
    y = json.dumps(x) # convert into JSON:
    print(y) # the result is a JSON string:
    # Output - {"name": "John", "age": 30, "married": true, "divorced": false, "children": ["Ann","Billy"], "pets": null, "cars": [{"model": "BMW 230", "mpg": 27.5}, {"model": "Ford Edge", "mpg": 24.1}]}
   ````
- The example above prints a JSON string, but it is not very easy to read, with no indentations and line breaks. Use four indents to make it easier to read the result:

    `print(json.dumps(x, indent=4))` . 

- You can also define the separators, default value is `(", ", ": ")`, which means using a comma and a space to separate each object, and a colon and a space to separate keys from values:

    `json.dumps(x, indent=4, separators=(". ", " = "))`

- Use the `sort_keys` parameter to specify if the result should be sorted or not:

    `json.dumps(x, indent=4, sort_keys=True)`

---

# Datetime in Python

- `datetime()` class requires three parameters to create a date: year, month, day.  `datetime()` class also takes parameters for time and timezone (hour, minute, second, microsecond, tzone), but they are optional, and has a default value of 0, (None for timezone).
- `strftime()` is a method for formatting date objects into readable strings.

    [A reference of all the legal format codes](https://www.notion.so/79547445e0bb4d77bea4a5384f311352)

    ````python
    import datetime
    x = datetime.datetime.now() # Import the datetime module and display the current date
    print(x)
    # Output - 2019-12-15 23:04:43.188440
    
    x = datetime.datetime(2020, 5, 17) # Create a date object
    # Output - 2020-05-17 00:00:00
    
    x = datetime.datetime(2018, 6, 1)
    print(x.strftime("%B")) # Display the name of the month.
    # Output - June
    ````

---

# Mysql in Python

- To use mysql in system install mysql and mysql workbench.
- To install mysql driver use `python -m pip install mysql-connector`
- Create connection and database.
    ````python
    import mysql.connector
    mydb = mysql.connector.connect(
        host="localhost",
        user="myusername",
        passwd="mypassword"
        database="mydatabase"
    )
    ````

- Execute mysql -
    ````python
    mycursor = mydb.cursor() 
    mycursor.execute(sql)
    
    #### Return a list of your system's databases ####
    mycursor = mydb.cursor()
    mycursor.execute("SHOW DATABASES")
    for x in mycursor:
    print(x)
    
    #### To fetch from table ####
    mycursor = mydb.cursor()
    mycursor.execute("SELECT  FROM customers")
    myresult = mycursor.fetchall() # fetchall for all columns and fetchone() for one column
    for x in myresult:
    print(x)
    ````

---
+---------------+---------------+--------------------+
| Fruit         | Price         | Advantages         |
+===============+===============+====================+
| Bananas       | $1.34         | - built-in wrapper |
|               |               | - bright color     |
+---------------+---------------+--------------------+
| Oranges       | $2.10         | - cures scurvy     |
|               |               | - tasty            |
+---------------+---------------+--------------------+