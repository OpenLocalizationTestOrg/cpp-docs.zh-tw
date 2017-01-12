---
title: Labeled Statements | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- goto
- case
dev_langs:
- C++
helpviewer_keywords:
- labeled statement
- statements, labeled
ms.assetid: 456a26d5-0fcc-4d1a-b71f-fa9ff3d73b91
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 02c0b6b4260b748a7fd5de051c9b0281728ee562

---
# Labeled Statements
Labels are used to transfer program control directly to the specified statement.  
  
```  
identifier :  statement  
case constant-expression :  statement  
default :  statement  
```  
  
 The scope of a label is the entire function in which it is declared.  
  
## Remarks  
 There are three types of labeled statements. All use a colon to separate some type of label from the statement. The case and default labels are specific to case statements.  
  
```cpp  
#include <iostream>   
using namespace std;   
  
void test_label(int x) {  
  
    if (x == 1){  
        goto label1;  
    }  
    goto label2;  
  
label1:  
    cout << "in label1" << endl;  
    return;  
  
label2:  
    cout << "in label2" << endl;  
    return;  
}  
  
int main() {  
    test_label(1);  // in label1   
    test_label(2);  // in label2  
}  
  
```  
  
 **The goto statement**  
  
 The appearance of an *identifier* label in the source program declares a label. Only a [goto](../cpp/goto-statement-cpp.md) statement can transfer control to an *identifier* label. The following code fragment illustrates use of the `goto` statement and an *identifier* label:  
  
 A label cannot appear by itself but must always be attached to a statement. If a label is needed by itself, place a null statement after the label.  
  
 The label has function scope and cannot be redeclared within the function. However, the same name can be used as a label in different functions.  
  
```  
// labels_with_goto.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   using namespace std;  
   goto Test2;  
  
   cout << "testing" << endl;  
  
   Test2:  
      cerr << "At Test2 label." << endl;  
}  
  
//Output: At Test2 label.  
```  
  
 **The case statement**  
  
 Labels that appear after the **case** keyword cannot also appear outside a `switch` statement. (This restriction also applies to the **default** keyword.) The following code fragment shows the correct use of **case** labels:  
  
```  
// Sample Microsoft Windows message processing loop.  
switch( msg )  
{  
   case WM_TIMER:    // Process timer event.  
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );  
      ShowWindow( hWnd, SW_SHOWNA );  
      nIcon %= 14;  
      Yield();  
      break;  
  
   case WM_PAINT:  
      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );  
      hDC = BeginPaint( hWnd, &ps );   
      EndPaint( hWnd, &ps );  
      break;  
  
   default:  
      // This choice is taken for all messages not specifically  
      //  covered by a case statement.  
  
      return DefWindowProc( hWnd, Message, wParam, lParam );  
      break;  
}  
```  
  
## Labels in the case statement  
 Labels that appear after the **case** keyword cannot also appear outside a `switch` statement. (This restriction also applies to the **default** keyword.) The following code fragment shows the correct use of **case** labels:  
  
```  
// Sample Microsoft Windows message processing loop.  
switch( msg )  
{  
   case WM_TIMER:    // Process timer event.  
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );  
      ShowWindow( hWnd, SW_SHOWNA );  
      nIcon %= 14;  
      Yield();  
      break;  
  
   case WM_PAINT:  
      // Obtain a handle to the device context.  
      // BeginPaint will send WM_ERASEBKGND if appropriate.  
  
      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );  
      hDC = BeginPaint( hWnd, &ps );  
  
      // Inform Windows that painting is complete.  
  
      EndPaint( hWnd, &ps );  
      break;  
  
   case WM_CLOSE:  
      // Close this window and all child windows.  
  
      KillTimer( hWnd, TIMER1 );  
      DestroyWindow( hWnd );  
      if ( hWnd == hWndMain )  
         PostQuitMessage( 0 );  // Quit the application.  
      break;  
  
   default:  
      // This choice is taken for all messages not specifically  
      //  covered by a case statement.  
  
      return DefWindowProc( hWnd, Message, wParam, lParam );  
      break;  
}  
```  
  
## Labels in the goto statement  
 The appearance of an *identifier* label in the source program declares a label. Only a [goto](../cpp/goto-statement-cpp.md) statement can transfer control to an *identifier* label. The following code fragment illustrates use of the `goto` statement and an *identifier* label:  
  
 A label cannot appear by itself but must always be attached to a statement. If a label is needed by itself, place a null statement after the label.  
  
 The label has function scope and cannot be redeclared within the function. However, the same name can be used as a label in different functions.  
  
```  
// labels_with_goto.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   using namespace std;  
   goto Test2;  
  
   cout << "testing" << endl;  
  
   Test2:  
      cerr << "At Test2 label." << endl;  
// At Test2 label.  
}  
  
```  
  
## See Also  
 [Overview of C++ Statements](../cpp/overview-of-cpp-statements.md)   
 [switch Statement (C++)](../cpp/switch-statement-cpp.md)


<!--HONumber=Jan17_HO2-->


