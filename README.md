# clui
Get the description, code point(s) and UTF encoding of Unicode characters and sequences, in a variety of formats and encodings with clui (Command Line Unicode Information) for macOS

Check out [blog entries on clui at brunerd.com](https://www.brunerd.com/blog/category/projects/clui/)

## clui usage
`./clui -u` for usage/help output in `less`
```
clui (1.0) - Command Line Unicode Info (https://github.com/brunerd/clui)
Usage: clui [options] <input> ...

Input can be:
  * Unicode characters, space or comma delimited (use -x to expand non-delimited strings)
  * Hexadecimal codepoint representations (U+hhhhh or 0xhhhhh), double-quoted muti-point sequences
  * Hyphenated ranges (ascending or descending): z-a, U+A1-U+BF or 0x20-0x7E
  * Category or Group names (see Alternate Input Options)
  * Descriptive words or phrases (see Alternate Input Options)

Output Options

 Encoding style for UTF
  -E <encoding>
     h*   Capitalized space delimited UTF-8 hexadecimal (NN) (default)
     0    Octal UTF-8 with leading 0 (\0nnn)
     o    Octal UTF-8 (\nnn)
     x    Shell style UTF-8 hex(\xnn)
     u    JS style UTF-16 (\unnnn)
     U    zsh style UTF-32 Unicode Code Point (\Unnnnnnnn)
     w    Web/URL UTF-8 encoding (%nn)

 -f <char size, info size>  set font size of characters and info in RTF output (default: 256,32)
 -F  Remove Fitzpatrick skin tone modifier, get description, then process normally as-is

 -h  Hide headers for CSV output
 -H  Hide characters lacking descriptions

 Output format 
  -O <output format>
     C*   CSV (default)
     c    Character-only, space delimited
     j    JSON output (array of objects)
     J    JSON Sequence output (objects delimited by 0x1E and 0x0A)
     p    Plain output (no field descriptions)
     r    RTF output (plain output with large sized characters)
     y    YAML output
          
 -x  Expand, describe each individual code point in a sequence
 -X  Expand plus display original sequence prior to expansion
     
Alternate Input Options

 -C <Category>[,Subsection]
      Treat input as a Category name with possible a subsection

 -G <Group>[,Category]
      Treat input as a Group name with possible category name

 Search mode
  -S <mode>  
     d    Description search
     c    Search for character usage in other sequences
     C    Search for character usage plus "related characters"

 -V  Verbatim, process input as-is without delimitation or conversion of code points
  
Other Modes

 List categories and groups
  -L <mode>  List categories or groups in CSV (use -h to suppress header)
     c    Category list (* after a name denotes subsections)
     C    Category list, with subsections expanded
     g    Groups of categories, top level name
     G    Group name with member categories expanded
     
     Use -C or -G to retrieve members of the categories or groups, respectively

 -u  Display usage info (aka help) with less (press q to quit)
  
Examples:

  Search for characters a to z plus "related characters" and output as CSV (default)
  clui -SC a-z

  Look up all available Categories
  clui -Lc

  Get every character in Emoji category and output in RTF to a file
  clui -Or -C Emoji > Emoji.rtf

  Search descriptions for substring "family" and expand multi-code point ZWJ sequences 
  clui -X -Sd "family"
```
