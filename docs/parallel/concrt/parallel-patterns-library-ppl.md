---
title: Parallel Patterns Library (PPL) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Parallel Patterns Library (PPL)
ms.assetid: 40fd86b2-69fa-45e5-93d8-98a75636c242
caps.latest.revision: 27
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
ms.sourcegitcommit: ef43c6d070fbfa9acc9ae75e2b81b031cb76942a
ms.openlocfilehash: 8088b57e6d4e0c0c93f45144a92c0acd14754972

---
# Parallel Patterns Library (PPL)
The Parallel Patterns Library (PPL) provides an imperative programming model that promotes scalability and ease-of-use for developing concurrent applications. The PPL builds on the scheduling and resource management components of the Concurrency Runtime. It raises the level of abstraction between your application code and the underlying threading mechanism by providing generic, type-safe algorithms and containers that act on data in parallel. The PPL also lets you develop applications that scale by providing alternatives to shared state.  
  
 The PPL provides the following features:  
  
- *Task Parallelism*: a mechanism that works on top of the Windows ThreadPool to execute several work items (tasks) in parallel  
  
- *Parallel algorithms*: generic algorithms that works on top of the Concurrency Runtime to act on collections of data in parallel  
  
- *Parallel containers and objects*: generic container types that provide safe concurrent access to their elements  
  
## Example  
 The PPL provides a programming model that resembles the Standard Template Library (STL). The following example demonstrates many features of the PPL. It computes several Fibonacci numbers serially and in parallel. Both computations act on a [std::array](../../standard-library/array-class-stl.md) object. The example also prints to the console the time that is required to perform both computations.  
  
 The serial version uses the STL [std::for_each](http://msdn.microsoft.com/Library/8cb2ae72-bef6-488b-b011-0475c0787e33) algorithm to traverse the array and stores the results in a [std::vector](../../standard-library/vector-class.md) object. The parallel version performs the same task, but uses the PPL [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorithm and stores the results in a [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) object. The `concurrent_vector` class enables each loop iteration to concurrently add elements without the requirement to synchronize write access to the container.  
  
 Because `parallel_for_each` acts concurrently, the parallel version of this example must sort the `concurrent_vector` object to produce the same results as the serial version.  
  
 Note that the example uses a naïve method to compute the Fibonacci numbers; however, this method illustrates how the Concurrency Runtime can improve the performance of long computations.  
  
 [!code-cpp[concrt-parallel-fibonacci#1](../../parallel/concrt/codesnippet/cpp/parallel-patterns-library-ppl_1.cpp)]  
  
 The following sample output is for a computer that has four processors.  
  
```Output  
serial time: 9250 ms  
parallel time: 5726 ms  
 
fib(24): 46368  
fib(26): 121393  
fib(41): 165580141  
fib(42): 267914296  
```  
  
 Each iteration of the loop requires a different amount of time to finish. The performance of `parallel_for_each` is bounded by the operation that finishes last. Therefore, you should not expect linear performance improvements between the serial and parallel versions of this example.  
  
## Related Topics  
  
|Title|Description|  
|-----------|-----------------|  
|[Task Parallelism](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Describes the role of tasks and task groups in the PPL.|  
|[Parallel Algorithms](../../parallel/concrt/parallel-algorithms.md)|Describes how to use parallel algorithms such as `parallel_for` and `parallel_for_each`.|  
|[Parallel Containers and Objects](../../parallel/concrt/parallel-containers-and-objects.md)|Describes the various parallel containers and objects that are provided by the PPL.|  
|[Cancellation in the PPL](cancellation-in-the-ppl.md)|Explains how to cancel the work that is being performed by a parallel algorithm.|  
|[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)|Describes the Concurrency Runtime, which simplifies parallel programming, and contains links to related topics.|




<!--HONumber=Jan17_HO1-->


