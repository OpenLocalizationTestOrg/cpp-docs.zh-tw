---
title: '&lt;string&gt; operators | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33ce8f05-06c7-45d3-a0cb-bcd27cf93910
caps.latest.revision: 11
manager: ghogen
translationtype: Human Translation
ms.sourcegitcommit: 31a7a65ed759ec552e11f2eccc5d425c2b2b765d
ms.openlocfilehash: 3772b1a90b699d2deb6a573c54b802122109fbf1

---
# &lt;string&gt; operators
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|[operator&gt;&gt;](#operator_gt__gt_)|  
|[operator&gt;=](#operator_gt__eq)|[operator&lt;](#operator_lt_)|[operator&lt;&lt;](#operator_lt__lt_)|  
|[operator&lt;=](#operator_lt__eq)|[operator+](#operator_add)|[operator==](#operator_eq_eq)|  
  
##  <a name="operator_add"></a>  operator+  
 Concatenates two string objects.  
  
```  
template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,  
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,  
    const CharType* right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,  
    const CharType right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator> operator+(
    const CharType* left,  
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator> operator+(
    const CharType left,  
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>& left,  
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,  
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,  
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,  
    const CharType* right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,  
    CharType right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator>&& operator+(
    const CharType* left,  
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>  
basic_string<CharType, Traits, Allocator>&& operator+(
    CharType left,  
    const basic_string<CharType, Traits, Allocator>&& right);
```  
  
### Parameters  
 ` left`  
 A C-style string or an object of type `basic_string` to be concatenated.  
  
 ` right`  
 A C-style string or an object of type `basic_string` to be concatenated.  
  
### Return Value  
 The string that is the concatenation of the input strings.  
  
### Remarks  
 The functions each overload `operator+` to concatenate two objects of template class [basic_string Class](../standard-library/basic-string-class.md). All effectively return `basic_string`\< **CharType**, **Traits**, **Allocator**>(_ *Left*). [append](../standard-library/basic-string-class.md#basic_string__append)(\_ *Right*).  
  
### Example  
  
```cpp  
// string_op_con.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   // Declaring an object of type basic_string<char>  
   string s1 ( "anti" );  
   string s2 ( "gravity" );  
   cout << "The basic_string s1 = " << s1 << "." << endl;  
   cout << "The basic_string s2 = " << s2 << "." << endl;  
  
   // Declaring a C-style string  
   char *s3 = "heroine";  
   cout << "The C-style string s3 = " << s3 << "." << endl;  
  
   // Declaring a character constant  
   char c1 = '!';  
   cout << "The character constant c1 = " << c1 << "." << endl;  
  
   // First member function: concatenates an  object  
   // of type basic_string with an object of type basic_string  
   string s12 = s1 + s2;  
   cout << "The string concatenating s1 & s2 is: " << s12 << endl;  
  
   // Second & fourth member functions: concatenate an object  
   // of type basic_string with an object of C-syle string type  
   string s1s3 = s1 + s3;  
   cout << "The string concatenating s1 & s3 is: " << s1s3 << endl;  
  
   // Third & fifth member functions: concatenate an object  
   // of type basic_string with a character constant  
   string s1s3c1 = s1s3 + c1;  
   cout << "The string concatenating s1 & s3 is: " << s1s3c1 << endl;  
}  
```  
  
```Output  
The basic_string s1 = anti.  
The basic_string s2 = gravity.  
The C-style string s3 = heroine.  
The character constant c1 = !.  
The string concatenating s1 & s2 is: antigravity  
The string concatenating s1 & s3 is: antiheroine  
The string concatenating s1 & s3 is: antiheroine!  
```  
  
##  <a name="operator_neq"></a>  operator!=  
 Tests if the string object on the left side of the operator is not equal to the string object on the right side.  
  
```  
template <class CharType, class Traits, class Allocator>  
bool operator!=(
    const basic_string<CharType, Traits, Allocator>& left, 
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
bool operator!=(
    const basic_string<CharType, Traits, Allocator>& left, 
const CharType* right);

template <class CharType, class Traits, class Allocator>  
bool operator!=(
    const CharType* left, 
    const basic_string<CharType, Traits, Allocator>& right);
```  
  
### Parameters  
 ` left`  
 A C-style string or an object of type `basic_string` to be compared.  
  
 ` right`  
 A C-style string or an object of type `basic_string` to be compared.  
  
### Return Value  
 **true** if the string object on the left side of the operator is not lexicographically equal to the string object on the right side; otherwise **false**.  
  
### Remarks  
 The comparison between string objects is based on a pairwise lexicographical comparison of their characters. Two strings are equal if they have the same number of characters and their respective character values are the same. Otherwise, they are unequal.  
  
### Example  
  
```cpp  
// string_op_ne.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // Declaring an objects of type basic_string<char>  
   string s1 ( "pluck" );  
   string s2 ( "strum" );  
   cout << "The basic_string s1 = " << s1 << "." << endl;  
   cout << "The basic_string s2 = " << s2 << "." << endl;  
  
   // Declaring a C-style string  
   char *s3 = "pluck";  
   cout << "The C-style string s3 = " << s3 << "." << endl;  
  
   // First member function: comparison between left-side object  
   // of type basic_string & right-side object of type basic_string  
   if ( s1 != s2 )  
      cout << "The strings s1 & s2 are not equal." << endl;  
   else  
      cout << "The strings s1 & s2 are equal." << endl;  
  
   // Second member function: comparison between left-side object  
   // of type basic_string & right-side object of C-syle string type  
   if ( s1 != s3 )  
      cout << "The strings s1 & s3 are not equal." << endl;  
   else  
      cout << "The strings s1 & s3 are equal." << endl;  
  
   // Third member function: comparison between left-side object  
   // of C-syle string type & right-side object of type basic_string  
   if ( s3 != s2 )  
      cout << "The strings s3 & s2 are not equal." << endl;  
   else  
      cout << "The strings s3 & s2 are equal." << endl;  
}  
```  
  
```Output  
The basic_string s1 = pluck.  
The basic_string s2 = strum.  
The C-style string s3 = pluck.  
The strings s1 & s2 are not equal.  
The strings s1 & s3 are equal.  
The strings s3 & s2 are not equal.  
```  
  
##  <a name="operator_eq_eq"></a>  operator==  
 Tests if the string object on the left side of the operator is equal to the string object on the right side.  
  
```  
template <class CharType, class Traits, class Allocator>  
bool operator==(
    const basic_string<CharType, Traits, Allocator>& left, 
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
bool operator==(
    const basic_string<CharType, Traits, Allocator>& left, 
    const CharType* right);

template <class CharType, class Traits, class Allocator>  
bool operator==(
    const CharType* left, 
    const basic_string<CharType, Traits, Allocator>& right);
```  
  
### Parameters  
 ` left`  
 A C-style string or an object of type `basic_string` to be compared.  
  
 ` right`  
 A C-style string or an object of type `basic_string` to be compared.  
  
### Return Value  
 **true** if the string object on the left side of the operator is lexicographically equal to the string object on the right side; otherwise **false**.  
  
### Remarks  
 The comparison between string objects is based on a pairwise lexicographical comparison of their characters. Two strings are equal if they have the same number of characters and their respective character values are the same. Otherwise, they are unequal.  
  
### Example  
  
```cpp  
// string_op_eq.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // Declaring an objects of type basic_string<char>  
   string s1 ( "pluck" );  
   string s2 ( "strum" );  
   cout << "The basic_string s1 = " << s1 << "." << endl;  
   cout << "The basic_string s2 = " << s2 << "." << endl;  
  
   // Declaring a C-style string  
   char *s3 = "pluck";  
   cout << "The C-style string s3 = " << s3 << "." << endl;  
  
   // First member function: comparison between left-side object  
   // of type basic_string & right-side object of type basic_string  
   if ( s1 == s2 )  
      cout << "The strings s1 & s2 are equal." << endl;  
   else  
      cout << "The strings s1 & s2 are not equal." << endl;  
  
   // Second member function: comparison between left-side object  
   // of type basic_string & right-side object of C-syle string type  
   if ( s1 == s3 )  
      cout << "The strings s1 & s3 are equal." << endl;  
   else  
      cout << "The strings s1 & s3 are not equal." << endl;  
  
   // Third member function: comparison between left-side object  
   // of C-syle string type & right-side object of type basic_string  
   if ( s3 == s2 )  
      cout << "The strings s3 & s2 are equal." << endl;  
   else  
      cout << "The strings s3 & s2 are not equal." << endl;  
}  
```  
  
```Output  
The basic_string s1 = pluck.  
The basic_string s2 = strum.  
The C-style string s3 = pluck.  
The strings s1 & s2 are not equal.  
The strings s1 & s3 are equal.  
The strings s3 & s2 are not equal.  
```  
  
##  <a name="operator_lt_"></a>  operator&lt;  
 Tests if the string object on the left side of the operator is less than to the string object on the right side.  
  
```  
template <class CharType, class Traits, class Allocator>  
bool operator<(
    const basic_string<CharType, Traits, Allocator>& left, 
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
bool operator<(
    const basic_string<CharType, Traits, Allocator>& left, 
    const CharType* right);

template <class CharType, class Traits, class Allocator>  
bool operator<(
    const CharType* left, 
    const basic_string<CharType, Traits, Allocator>& right);
```  
  
### Parameters  
 ` left`  
 A C-style string or an object of type `basic_string` to be compared.  
  
 ` right`  
 A C-style string or an object of type `basic_string` to be compared.  
  
### Return Value  
 **true** if the string object on the left side of the operator is lexicographically less than the string object on the right side; otherwise **false**.  
  
### Remarks  
 A lexicographical comparison between strings compares them character by character until:  
  
-   It finds two corresponding characters unequal, and the result of their comparison is taken as the result of the comparison between the strings.  
  
-   It finds no inequalities, but one string has more characters than the other, and the shorter string is considered less than the longer string.  
  
-   It finds no inequalities and finds that the strings have the same number of characters, and so the strings are equal.  
  
### Example  
  
```cpp  
// string_op_lt.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   // Declaring an objects of type basic_string<char>  
   string s1 ( "strict" );  
   string s2 ( "strum" );  
   cout << "The basic_string s1 = " << s1 << "." << endl;  
   cout << "The basic_string s2 = " << s2 << "." << endl;  
  
   // Declaring a C-style string  
   char *s3 = "strict";  
   cout << "The C-style string s3 = " << s3 << "." << endl;  
  
   // First member function: comparison between left-side object  
   // of type basic_string & right-side object of type basic_string  
   if ( s1 < s2 )  
      cout << "The string s1 is less than the string s2." << endl;  
   else  
      cout << "The string s1 is not less than the string s2." << endl;  
  
   // Second member function: comparison between left-hand object  
   // of type basic_string & right-hand object of C-syle string type  
   if ( s1 < s3 )  
      cout << "The string s1 is less than the string s3." << endl;  
   else  
      cout << "The string s1 is not less than the string s3." << endl;  
  
   // Third member function: comparison between left-hand object  
   // of C-syle string type & right-hand object of type basic_string  
   if ( s3 < s2 )  
      cout << "The string s3 is less than the string s2." << endl;  
   else  
      cout << "The string s3 is not less than the string s2." << endl;  
}  
```  
  
```Output  
The basic_string s1 = strict.  
The basic_string s2 = strum.  
The C-style string s3 = strict.  
The string s1 is less than the string s2.  
The string s1 is not less than the string s3.  
The string s3 is less than the string s2.  
```  
  
##  <a name="operator_lt__eq"></a>  operator&lt;=  
 Tests if the string object on the left side of the operator is less than or equal to the string object on the right side.  
  
```  
template <class CharType, class Traits, class Allocator>  
bool operator<=(
    const basic_string<CharType, Traits, Allocator>& left, 
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
bool operator<=(
    const basic_string<CharType, Traits, Allocator>& left, 
    const CharType* right);

template <class CharType, class Traits, class Allocator>  
bool operator<=(
    const CharType* left, 
    const basic_string<CharType, Traits, Allocator>& right);
```  
  
### Parameters  
 ` left`  
 A C-style string or an object of type `basic_string` to be compared.  
  
 ` right`  
 A C-style string or an object of type `basic_string` to be compared.  
  
### Return Value  
 **true** if the string object on the left side of the operator is lexicographically less than or equal to the string object on the right side; otherwise **false**.  
  
### Remarks  
 A lexicographical comparison between strings compares them character by character until:  
  
-   It finds two corresponding characters unequal, and the result of their comparison is taken as the result of the comparison between the strings.  
  
-   It finds no inequalities, but one string has more characters than the other, and the shorter string is considered less than the longer string.  
  
-   It finds no inequalities and finds that the strings have the same number of characters, so the strings are equal.  
  
### Example  
  
```cpp  
// string_op_le.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // Declaring an objects of type basic_string<char>  
   string s1 ( "strict" );  
   string s2 ( "strum" );  
   cout << "The basic_string s1 = " << s1 << "." << endl;  
   cout << "The basic_string s2 = " << s2 << "." << endl;  
  
   // Declaring a C-style string  
   char *s3 = "strict";  
   cout << "The C-style string s3 = " << s3 << "." << endl;  
  
   // First member function: comparison between left-side object  
   // of type basic_string & right-side object of type basic_string  
   if ( s1 <= s2 )  
      cout << "The string s1 is less than or equal to "  
           << "the string s2." << endl;  
   else  
      cout << "The string s1 is greater than "  
           << "the string s2." << endl;  
  
   // Second member function: comparison between left-side object  
   // of type basic_string & right-side object of C-syle string type  
   if ( s1 <= s3 )  
      cout << "The string s1 is less than or equal to "  
           << "the string s3." << endl;  
   else  
      cout << "The string s1 is greater than "  
           << "the string s3." << endl;  
  
   // Third member function: comparison between left-side object  
   // of C-syle string type  & right-side object of type basic_string  
   if ( s2 <= s3 )  
      cout << "The string s2 is less than or equal to "  
           << "the string s3." << endl;  
   else  
      cout << "The string s2 is greater than "  
           << "the string s3." << endl;  
}  
```  
  
```Output  
The basic_string s1 = strict.  
The basic_string s2 = strum.  
The C-style string s3 = strict.  
The string s1 is less than or equal to the string s2.  
The string s1 is less than or equal to the string s3.  
The string s2 is greater than the string s3.  
```  
  
##  <a name="operator_lt__lt_"></a>  operator&lt;&lt;  
 A template function that writes a string into the output stream.  
  
```  
template <class CharType, class Traits, class Allocator>  
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& _Ostr, 
    const basic_string<CharType, Traits, Allocator>& str);
```  
  
### Parameters  
 _Ostr  
 The output stream being written to.  
  
 ` str`  
 The string to be entered into the output stream.  
  
### Return Value  
 Writes the value of the specified string to the output stream `_Ostr`.  
  
### Remarks  
 The template function overloads **operator<<** to insert an object _ *Str* of template class [basic_string](../standard-library/basic-string-class.md) into the stream \_ *Ostr.* The function effectively returns \_ *Ostr*. **write**( \_ *Str*. [c_str](../standard-library/basic-string-class.md#basic_string__c_str), \_ *Str*. [size](../standard-library/basic-string-class.md#basic_string__size)).  
  
##  <a name="operator_gt_"></a>  operator&gt;  
 Tests if the string object on the left side of the operator is greater than to the string object on the right side.  
  
```  
template <class CharType, class Traits, class Allocator>  
bool operator>(
    const basic_string<CharType, Traits, Allocator>& left, 
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
bool operator>(
    const basic_string<CharType, Traits, Allocator>& left, 
    const CharType* right);

template <class CharType, class Traits, class Allocator>  
bool operator>(
    const CharType* left, 
    const basic_string<CharType, Traits, Allocator>& right);
```  
  
### Parameters  
 ` left`  
 A C-style string or an object of type `basic_string` to be compared.  
  
 ` right`  
 A C-style string or an object of type `basic_string` to be compared.  
  
### Return Value  
 **true** if the string object on the left side of the operator is lexicographically greater than the string object on the right side; otherwise **false**.  
  
### Remarks  
 A lexicographical comparison between strings compares them character by character until:  
  
-   It finds two corresponding characters unequal, and the result of their comparison is taken as the result of the comparison between the strings.  
  
-   It finds no inequalities, but one string has more characters than the other, and the shorter string is considered less than the longer string.  
  
-   It finds no inequalities and finds that the strings have the same number of characters, and so the strings are equal.  
  
### Example  
  
```cpp  
// string_op_gt.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // Declaring an objects of type basic_string<char>  
   string s1 ( "strict" );  
   string s2 ( "strum" );  
   cout << "The basic_string s1 = " << s1 << "." << endl;  
   cout << "The basic_string s2 = " << s2 << "." << endl;  
  
   // Declaring a C-style string  
   char *s3 = "stricture";  
   cout << "The C-style string s3 = " << s3 << "." << endl;  
  
   // First member function: comparison between left-side object  
   // of type basic_string & right-side object of type basic_string  
   if ( s1 > s2 )  
      cout << "The string s1 is greater than "  
           << "the string s2." << endl;  
   else  
      cout << "The string s1 is not greater than "  
           << "the string s2." << endl;  
  
   // Second member function: comparison between left-side object  
   // of type basic_string & right-side object of C-syle string type  
   if ( s3 > s1 )  
      cout << "The string s3 is greater than "  
           << "the string s1." << endl;  
   else  
      cout << "The string s3 is not greater than "  
           << "the string s1." << endl;  
  
   // Third member function: comparison between left-side object  
   // of C-syle string type & right-side object of type basic_string  
   if ( s2 > s3 )  
      cout << "The string s2 is greater than "  
           << "the string s3." << endl;  
   else  
      cout << "The string s2 is not greater than "  
           << "the string s3." << endl;  
}  
```  
  
```Output  
The basic_string s1 = strict.  
The basic_string s2 = strum.  
The C-style string s3 = stricture.  
The string s1 is not greater than the string s2.  
The string s3 is greater than the string s1.  
The string s2 is greater than the string s3.  
```  
  
##  <a name="operator_gt__eq"></a>  operator&gt;=  
 Tests if the string object on the left side of the operator is greater than or equal to the string object on the right side.  
  
```  
template <class CharType, class Traits, class Allocator>  
bool operator>=(
    const basic_string<CharType, Traits, Allocator>& left, 
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>  
bool operator>=(
    const basic_string<CharType, Traits, Allocator>& left, 
    const CharType* right);

template <class CharType, class Traits, class Allocator>  
bool operator>=(
    const CharType* left, 
    const basic_string<CharType, Traits, Allocator>& right);
```  
  
### Parameters  
 ` left`  
 A C-style string or an object of type `basic_string` to be compared.  
  
 ` right`  
 A C-style string or an object of type `basic_string` to be compared.  
  
### Return Value  
 **true** if the string object on the left side of the operator is lexicographically greater than or equal to the string object on the right side; otherwise **false**.  
  
### Remarks  
 A lexicographical comparison between strings compares them character by character until:  
  
-   It finds two corresponding characters unequal, and the result of their comparison is taken as the result of the comparison between the strings.  
  
-   It finds no inequalities, but one string has more characters than the other, and the shorter string is considered less than the longer string.  
  
-   It finds no inequalities and finds the strings have the same number of characters, and so the strings are equal.  
  
### Example  
  
```cpp  
// string_op_ge.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // Declaring an objects of type basic_string<char>  
   string s1 ( "strict" );  
   string s2 ( "strum" );  
   cout << "The basic_string s1 = " << s1 << "." << endl;  
   cout << "The basic_string s2 = " << s2 << "." << endl;  
  
   // Declaring a C-style string  
   char *s3 = "stricture";  
   cout << "The C-style string s3 = " << s3 << "." << endl;  
  
   // First member function: comparison between left-side object  
   // of type basic_string & right-side object of type basic_string  
   if ( s1 >= s2 )  
      cout << "The string s1 is greater than or equal to "  
           << "the string s2." << endl;  
   else  
      cout << "The string s1 is less than "  
           << "the string s2." << endl;  
  
   // Second member function: comparison between left-side object  
   // of type basic_string & right-side object of C-syle string type  
   if ( s3 >= s1 )  
      cout << "The string s3 is greater than or equal to "  
           << "the string s1." << endl;  
   else  
      cout << "The string s3 is less than "  
           << "the string s1." << endl;  
  
   // Third member function: comparison between left-side object  
   // of C-syle string type & right-side object of type basic_string  
   if ( s2 >= s3 )  
      cout << "The string s2 is greater than or equal to "  
           << "the string s3." << endl;  
   else  
      cout << "The string s2 is less than "  
           << "the string s3." << endl;  
}  
```  
  
```Output  
The basic_string s1 = strict.  
The basic_string s2 = strum.  
The C-style string s3 = stricture.  
The string s1 is less than the string s2.  
The string s3 is greater than or equal to the string s1.  
The string s2 is greater than or equal to the string s3.  
```  
  
##  <a name="operator_gt__gt_"></a>  operator&gt;&gt;  
 A template function that reads a string from an input stream.  
  
```  
template <class CharType, class Traits, class Allocator>  
basic_istream<CharType, Traits>& operator>>(
    basic_istream<CharType, Traits>& _Istr,  
    basic_string<CharType, Traits, Allocator>& right);
```  
  
### Parameters  
 `_Istr`  
 The input stream used to extract the sequence  
  
 ` right`  
 The string that is being extracted from the input stream.  
  
### Return Value  
 Reads the value of the specified string from `_Istr` and returns it into ` right.`  
  
### Remarks  
 The operator skips the leading white spaces unless the `skipws` flag is set. It reads all the following characters until the next character is a white space or the end of the file is reached.  
  
 The template function overloads **operator>>** to replace the sequence controlled by ` right` with a sequence of elements extracted from the stream `_Istr`. Extraction stops:  
  
-   At end of file.  
  
-   After the function extracts `_Istr`. **width** elements, if that value is nonzero.  
  
 After the function extracts `_Istr`. [max_size](../standard-library/basic-string-class.md#basic_string__max_size) elements.  
  
-   After the function extracts an element *ch* for which [use_facet](../standard-library/basic-filebuf-class.md#basic_filebuf__open)< **ctype**\< **CharType**> >( `getloc`). **is**( **ctype**\< **CharType**>:: **space**, *ch*) is true, in which case the character is put back.  
  
 If the function extracts no elements, it calls [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)( `ios_base::failbit`). In any case, it calls **istr**. **width**(0) and returns \* **this**.  
  
### Example  
  
```cpp  
// string_op_read_.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   string c0;  
   cout << "Input a string c0 ( try: Fibonacci numbers ): ";  
   cin >> c0;  
   cout << "The string entered is c0 = " << c0 << endl;  
}  
```  
  
## See Also  
 [\<string>](../standard-library/string.md)



<!--HONumber=Jan17_HO1-->


