TCharacterSet Documentation

------------------------------------------------------------------------------



INITIALIZATION
    At least one of either type's initialization methods has to be called
    before you can use the character set.  Failure to do so will result in
    some type of exception being thrown, most likely a TNullObjectException.

RANGES NOTE
    Ranges in strings are formed in much the same was as character groups
    in regular expressions.  "x" specifies an individual character, "x-y"
    specifies a range of character.  You can escape hyphens and backslashes
    with backslashes.  If the hyphen is at the beginning or end of a range,
    such as "a--" or "--0" then it is counted as a regular character.

ENUMERATION
    When using a TCharacterSet for enumeration, it will create a linked list
    of strings for every character that the list contains using
    TCharacterSet#Characters().  This list is not cached, so consider storing
    it and iterating over the returned list instead if you find yourself doing
    this often.

------------------------------------------------------------------------------



TCharacterSet {

CREATION ---------------------------------------------------------------------
    Method such as TCharacterSet.ForWhitespace are implemented both in
    TCharacterSet and TMutableCharacterSet.  Each will return an instance of
    its respective type, be it mutable or immutable.

    + ForWhitespace:TCharacterSet
        See #InitWithWhitespace.
        
    + ForAlphanumeric:TCharacterSet
        See #InitWithAlphanumeric.
        
    + ForNewline:TCharacterSet
        See #InitWithNewline.
    
    + ForLetters:TCharacterSet
        See #InitWithLetters.
    
    + ForUppercaseLetters:TCharacterSet
        See #InitWithUppercaseLetters.
    
    + ForLowercaseLetters:TCharacterSet
        See #InitWithLowercaseLetters.
    
    + ForNumbers:TCharacterSet
        See #InitWithNumbers.
    
INITIALIZATION ---------------------------------------------------------------
    
    - Init:TCharacterSet
        Initializes an empty character set.
        
    - InitWithWhitespace:TCharacterSet
        Initializes a character set for carriage return, newline, tab, and
        space.
        
    - InitWithAlphanumeric:TCharacterSet
        Initializes a character set that matches [a-zA-Z0-9].
        
    - InitWithNewline:TCharacterSet
        Initializes a character set that only matches newline.
        
    - InitWithLetters:TCharacterSet
        Initializes a character set with lowercase and uppercase letters a-z
        and A-Z.
    
    - InitWithUppercaseLetters:TCharacterSet
        Initializes a character set with uppercase letters A-Z.
    
    - InitWithLowercaseLetters:TCharacterSet
        Initializes a character set with lowercase letters a-z.
        
    - InitWithNumbers:TCharacterSet
        Initializes a character set with numbers 0-9.
        
    - InitWithString:TCharacterSet(string)
        Initializes a character set that matches ranges specified in string.
        
    - InitWithRange:TCharacterSet(begin, length)
        Initializes a character set with a range of characters.
    
SEARCHING --------------------------------------------------------------------
    
    - FindInString:Int(string, from)
        Searches for the first instance of any character from the set inside
        of string, starting at the index specified by from.
    
    - FindLastInString:Int(string, from)
        Searches for the last instance of any character from the set inside of
        string, starting at the index specified by from.
    
    - Contains:Int(char)
        Returns true if the set contains char, otherwise false.
    
    MISCELLANEOUS
        Methods that may serve useful purposes in debugging, serialization, or
        other scenarios.
    
    - Characters:TList
        Returns a TList of each individual character in the set.
    
    - ToString:String
        Returns a string with each character in the set.
    
    COPYING
    
    - Copy:TCharacterSet
        Creates an immutable copy of the character set
        
    - MutableCopy:TMutableCharacterSet
        Creates a mutable copy of the character set
}

------------------------------------------------------------------------------



TMutableCharacterSet : TCharacterSet {

MODIFYING THE SET ------------------------------------------------------------

    - AddRange(begin, length)
        Adds a range of characters to the set.
        
    - AddRangesWithString(string)
        Adds characters based on the ranges in string to the set.
    
    - AddChar(char)
        Adds a single character to the set.
}
