---
title: '&lt;map&gt; operators | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7df02b9f-701c-44ed-834a-a819badc5bd0
caps.latest.revision: 7
manager: ghogen
translationtype: Human Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 5721a3bb5c74c6609fd001d5e5759b4f153915d2

---
# &lt;map&gt; operators
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|[operator&gt;=](#operator_gt__eq)|  
|[operator&lt;](#operator_lt_)|[operator&lt;=](#operator_lt__eq)|[operator==](#operator_eq_eq)|  
|[operator!= (multimap)](#operator_neq_multimap)|[operator&gt;](#operator_gt_multimap)|[operator&gt;=](#operator_gt__eq_multimap)|  
|[operator&lt;](#operator_lt_multimap)|[operator&lt;=](#operator_lt__eq_multimap)|[operator==](#operator_eq_eq_multimap)|  
  
##  <a name="operator_neq"></a>  operator!=  
 Tests if the map object on the left side of the operator is not equal to the map object on the right side.  
  
```
bool operator!=(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### Parameters  
 `left`  
 An object of type **map**.  
  
 `right`  
 An object of type **map**.  
  
### Return Value  
 **true** if the maps are not equal; **false** if maps are equal.  
  
### Remarks  
 The comparison between map objects is based on a pairwise comparison of their elements. Two maps are equal if they have the same number of elements and their respective elements have the same values. Otherwise, they are unequal.  
  
### Example  
  
```cpp  
// map_op_ne.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1, m2, m3;  
   int i;  
   typedef pair <int, int> Int_Pair;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 != m2 )  
      cout << "The maps m1 and m2 are not equal." << endl;  
   else  
      cout << "The maps m1 and m2 are equal." << endl;  
  
   if ( m1 != m3 )  
      cout << "The maps m1 and m3 are not equal." << endl;  
   else  
      cout << "The maps m1 and m3 are equal." << endl;  
}  
\* Output:   
The maps m1 and m2 are not equal.  
The maps m1 and m3 are equal.  
*\  
```  
  
##  <a name="operator_lt_"></a>  operator&lt;  
 Tests if the map object on the left side of the operator is less than the map object on the right side.  
  
```
bool operator<(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### Parameters  
 `left`  
 An object of type **map**.  
  
 `right`  
 An object of type **map**.  
  
### Return Value  
 **true** if the map on the left side of the operator is strictly less than the map on the right side of the operator; otherwise **false**.  
  
### Remarks  
 The comparison between map objects is based on a pairwise comparison of their elements. The less-than relationship between two objects is based on a comparison of the first pair of unequal elements.  
  
### Example  
  
```cpp  
// map_op_lt.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map<int, int> m1, m2, m3;  
   int i;  
   typedef pair<int, int> Int_Pair;  
  
   for ( i = 1 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
   }  
  
   if ( m1 < m2 )  
      cout << "The map m1 is less than the map m2." << endl;  
   else  
      cout << "The map m1 is not less than the map m2." << endl;  
  
   if ( m1 < m3 )  
      cout << "The map m1 is less than the map m3." << endl;  
   else  
      cout << "The map m1 is not less than the map m3." << endl;  
}  
\* Output:   
The map m1 is less than the map m2.  
The map m1 is not less than the map m3.  
*\  
```  
  
##  <a name="operator_lt__eq"></a>  operator&lt;=  
 Tests if the map object on the left side of the operator is less than or equal to the map object on the right side.  
  
```
bool operator<=(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### Parameters  
 `left`  
 An object of type **map**.  
  
 `right`  
 An object of type **map**.  
  
### Return Value  
 **true** if the map on the left side of the operator is less than or equal to the map on the right side of the operator; otherwise **false**.  
  
### Example  
  
```cpp  
// map_op_le.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1, m2, m3, m4;  
   int i;  
   typedef pair <int, int> Int_Pair;  
  
   for ( i = 1 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
      m4.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 <= m2 )  
      cout << "The map m1 is less than or equal to the map m2." << endl;  
   else  
      cout << "The map m1 is greater than the map m2." << endl;  
  
   if ( m1 <= m3 )  
      cout << "The map m1 is less than or equal to the map m3." << endl;  
   else  
      cout << "The map m1 is greater than the map m3." << endl;  
  
   if ( m1 <= m4 )  
      cout << "The map m1 is less than or equal to the map m4." << endl;  
   else  
      cout << "The map m1 is greater than the map m4." << endl;  
}  
\* Output:   
The map m1 is less than or equal to the map m2.  
The map m1 is greater than the map m3.  
The map m1 is less than or equal to the map m4.  
*\  
```  
  
##  <a name="operator_eq_eq"></a>  operator==  
 Tests if the map object on the left side of the operator is equal to the map object on the right side.  
  
```
bool operator==(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### Parameters  
 `left`  
 An object of type **map**.  
  
 `right`  
 An object of type **map**.  
  
### Return Value  
 **true** if the map on the left side of the operator is equal to the map on the right side of the operator; otherwise **false**.  
  
### Remarks  
 The comparison between map objects is based on a pairwise comparison of their elements. Two maps are equal if they have the same number of elements and their respective elements have the same values. Otherwise, they are unequal.  
  
### Example  
  
```cpp  
// map_op_eq.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map < int, int > m1, m2, m3;  
   int i;  
   typedef pair < int, int > Int_Pair;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 == m2 )  
      cout << "The maps m1 and m2 are equal." << endl;  
   else  
      cout << "The maps m1 and m2 are not equal." << endl;  
  
   if ( m1 == m3 )  
      cout << "The maps m1 and m3 are equal." << endl;  
   else  
      cout << "The maps m1 and m3 are not equal." << endl;  
}  
\* Output:   
The maps m1 and m2 are not equal.  
The maps m1 and m3 are equal.  
*\  
```  
  
##  <a name="operator_gt_"></a>  operator&gt;  
 Tests if the map object on the left side of the operator is greater than the map object on the right side.  
  
```
bool operator>(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### Parameters  
 `left`  
 An object of type **map**.  
  
 `right`  
 An object of type **map**.  
  
### Return Value  
 **true** if the map on the left side of the operator is greater than the map on the right side of the operator; otherwise **false**.  
  
### Remarks  
 The comparison between map objects is based on a pairwise comparison of their elements. The greater-than relationship between two objects is based on a comparison of the first pair of unequal elements.  
  
### Example  
  
```cpp  
// map_op_gt.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map < int, int > m1, m2, m3;  
   int i;  
   typedef pair < int, int > Int_Pair;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
   }  
  
   if ( m1 > m2 )  
      cout << "The map m1 is greater than the map m2." << endl;  
   else  
      cout << "The map m1 is not greater than the map m2." << endl;  
  
   if ( m1 > m3 )  
      cout << "The map m1 is greater than the map m3." << endl;  
   else  
      cout << "The map m1 is not greater than the map m3." << endl;  
}  
\* Output:   
The map m1 is not greater than the map m2.  
The map m1 is greater than the map m3.  
*\  
```  
  
##  <a name="operator_gt__eq"></a>  operator&gt;=  
 Tests if the map object on the left side of the operator is greater than or equal to the map object on the right side.  
  
```
bool operator>=(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### Parameters  
 `left`  
 An object of type **map**.  
  
 `right`  
 An object of type **map**.  
  
### Return Value  
 **true** if the map on the left side of the operator is greater than or equal to the map on the right side of the list; otherwise **false**.  
  
### Example  
  
```cpp  
// map_op_ge.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map < int, int > m1, m2, m3, m4;  
   int i;  
   typedef pair < int, int > Int_Pair;  
  
   for ( i = 1 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
      m4.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 >= m2 )  
      cout << "Map m1 is greater than or equal to map m2." << endl;  
   else  
      cout << "The map m1 is less than the map m2." << endl;  
  
   if ( m1 >= m3 )  
      cout << "Map m1 is greater than or equal to map m3." << endl;  
   else  
      cout << "The map m1 is less than the map m3." << endl;  
  
   if ( m1 >= m4 )  
      cout << "Map m1 is greater than or equal to map m4." << endl;  
   else  
      cout << "The map m1 is less than the map m4." << endl;  
}  
\* Output:   
The map m1 is less than the map m2.  
Map m1 is greater than or equal to map m3.  
Map m1 is greater than or equal to map m4.  
*\  
```  
  
##  <a name="operator_neq_multimap"></a>  operator!= (multimap)  
 Tests if the multimap object on the left side of the operator is not equal to the multimap object on the right side.  
  
```
bool operator!=(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### Parameters  
 `left`  
 An object of type `multimap`.  
  
 `right`  
 An object of type `multimap`.  
  
### Return Value  
 **true** if the multimaps are not equal; **false** if multimaps are equal.  
  
### Remarks  
 The comparison between multimap objects is based on a pairwise comparison of their elements. Two multimaps are equal if they have the same number of elements and their respective elements have the same values. Otherwise, they are unequal.  
  
### Example  
  
```cpp  
// multimap_op_ne.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int> m1, m2, m3;  
   int i;  
   typedef pair <int, int> Int_Pair;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 != m2 )  
      cout << "The multimaps m1 and m2 are not equal." << endl;  
   else  
      cout << "The multimaps m1 and m2 are equal." << endl;  
  
   if ( m1 != m3 )  
      cout << "The multimaps m1 and m3 are not equal." << endl;  
   else  
      cout << "The multimaps m1 and m3 are equal." << endl;  
}  
\* Output:   
The multimaps m1 and m2 are not equal.  
The multimaps m1 and m3 are equal.  
*\  
```  
  
##  <a name="operator_lt_multimap"></a>  operator&lt;  
 Tests if the multimap object on the left side of the operator is less than the multimap object on the right side.  
  
```
bool operator<(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### Parameters  
 `left`  
 An object of type `multimap`.  
  
 `right`  
 An object of type `multimap`.  
  
### Return Value  
 **true** if the multimap on the left side of the operator is strictly less than the multimap on the right side of the operator; otherwise **false**.  
  
### Remarks  
 The comparison between multimap objects is based on a pairwise comparison of their elements. The less-than relationship between two objects is based on a comparison of the first pair of unequal elements.  
  
### Example  
  
```cpp  
// multimap_op_lt.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap < int, int > m1, m2, m3;  
   int i;  
   typedef pair < int, int > Int_Pair;  
  
   for ( i = 1 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
   }  
  
   if ( m1 < m2 )  
      cout << "The multimap m1 is less than the multimap m2." << endl;  
   else  
      cout << "The multimap m1 is not less than the multimap m2." << endl;  
  
   if ( m1 < m3 )  
      cout << "The multimap m1 is less than the multimap m3." << endl;  
   else  
      cout << "The multimap m1 is not less than the multimap m3." << endl;  
}  
\* Output:   
The multimap m1 is less than the multimap m2.  
The multimap m1 is not less than the multimap m3.  
*\  
```  
  
##  <a name="operator_lt__eq_multimap"></a>  operator&lt;=  
 Tests if the multimap object on the left side of the operator is less than or equal to the multimap object on the right side.  
  
```
bool operator<=(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### Parameters  
 `left`  
 An object of type `multimap`.  
  
 `right`  
 An object of type `multimap`.  
  
### Return Value  
 **true** if the multimap on the left side of the operator is less than or equal to the multimap on the right side of the operator; otherwise **false**.  
  
### Example  
  
```cpp  
// multimap_op_le.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int> m1, m2, m3, m4;  
   int i;  
   typedef pair <int, int> Int_Pair;  
  
   for ( i = 1 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
      m4.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 <= m2 )  
      cout << "m1 is less than or equal to m2" << endl;  
   else  
      cout << "m1 is greater than m2" << endl;  
  
   if ( m1 <= m3 )  
      cout << "m1 is less than or equal to m3" << endl;  
   else  
      cout << "m1 is greater than m3" << endl;  
  
   if ( m1 <= m4 )  
      cout << "m1 is less than or equal to m4" << endl;  
   else  
      cout << "m1 is greater than m4" << endl;  
}  
\* Output:   
m1 is less than or equal to m2  
m1 is greater than m3  
m1 is less than or equal to m4  
*\  
```  
  
##  <a name="operator_eq_eq_multimap"></a>  operator==  
 Tests if the multimap object on the left side of the operator is equal to the multimap object on the right side.  
  
```
bool operator==(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### Parameters  
 `left`  
 An object of type `multimap`.  
  
 `right`  
 An object of type `multimap`.  
  
### Return Value  
 **true** if the multimap on the left side of the operator is equal to the multimap on the right side of the operator; otherwise **false**.  
  
### Remarks  
 The comparison between multimap objects is based on a pairwise comparison of their elements. Two multimaps are equal if they have the same number of elements and their respective elements have the same values. Otherwise, they are unequal.  
  
### Example  
  
```cpp  
// multimap_op_eq.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap<int, int> m1, m2, m3;  
   int i;  
   typedef pair<int, int> Int_Pair;  
  
   for (i = 0; i < 3; i++)  
   {  
      m1.insert(Int_Pair(i, i));  
      m2.insert(Int_Pair(i, i*i));  
      m3.insert(Int_Pair(i, i));  
   }  
  
   if ( m1 == m2 )  
      cout << "m1 and m2 are equal" << endl;  
   else  
      cout << "m1 and m2 are not equal" << endl;  
  
   if ( m1 == m3 )  
      cout << "m1 and m3 are equal" << endl;  
   else  
      cout << "m1 and m3 are not equal" << endl;  
}  
\* Output:   
m1 and m2 are not equal  
m1 and m3 are equal  
*\  
```  
  
##  <a name="operator_gt_multimap"></a>  operator&gt;  
 Tests if the multimap object on the left side of the operator is greater than the multimap object on the right side.  
  
```
bool operator>(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### Parameters  
 `left`  
 An object of type `multimap`.  
  
 `right`  
 An object of type `multimap`.  
  
### Return Value  
 **true** if the multimap on the left side of the operator is greater than the multimap on the right side of the operator; otherwise **false**.  
  
### Remarks  
 The comparison between multimap objects is based on a pairwise comparison of their elements. The greater-than relationship between two objects is based on a comparison of the first pair of unequal elements.  
  
### Example  
  
```cpp  
// multimap_op_gt.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap < int, int > m1, m2, m3;  
   int i;  
   typedef pair < int, int > Int_Pair;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
   }  
  
   if ( m1 > m2 )  
      cout << "The multimap m1 is greater than the multimap m2." << endl;  
   else  
      cout << "Multimap m1 is not greater than multimap m2." << endl;  
  
   if ( m1 > m3 )  
      cout << "The multimap m1 is greater than the multimap m3." << endl;  
   else  
      cout << "The multimap m1 is not greater than the multimap m3." << endl;  
}  
\* Output:   
Multimap m1 is not greater than multimap m2.  
The multimap m1 is greater than the multimap m3.  
*\  
```  
  
##  <a name="operator_gt__eq_multimap"></a>  operator&gt;=  
 Tests if the multimap object on the left side of the operator is greater than or equal to the multimap object on the right side.  
  
```
bool operator>=(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### Parameters  
 `left`  
 An object of type `multimap`.  
  
 `right`  
 An object of type `multimap`.  
  
### Return Value  
 **true** if the multimap on the left side of the operator is greater than or equal to the multimap on the right side of the list; otherwise **false**.  
  
### Example  
  
```cpp  
// multimap_op_ge.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap < int, int > m1, m2, m3, m4;  
   int i;  
   typedef pair < int, int > Int_Pair;  
  
   for ( i = 1 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
      m4.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 >= m2 )  
      cout << "The multimap m1 is greater than or equal to the multimap m2." << endl;  
   else  
      cout << "The multimap m1 is less than the multimap m2." << endl;  
  
   if ( m1 >= m3 )  
      cout << "The multimap m1 is greater than or equal to the multimap m3." << endl;  
   else  
      cout << "The multimap m1 is less than the multimap m3." << endl;  
  
   if ( m1 >= m4 )  
      cout << "The multimap m1 is greater than or equal to the multimap m4." << endl;  
   else  
      cout << "The multimap m1 is less than the multimap m4." << endl;  
}  
\* Output:   
The multimap m1 is less than the multimap m2.  
The multimap m1 is greater than or equal to the multimap m3.  
The multimap m1 is greater than or equal to the multimap m4.  
*\  
```  
  
## See Also  
 [\<map>](../standard-library/map.md)






<!--HONumber=Jan17_HO2-->


