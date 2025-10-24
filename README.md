//Question1: Implement a Generic Storage Class 
//Write a program to create a class that can store a single value of any type. 
//    This class should use generics so it can store integers, strings, or any other type. 
//Task: 
//1.Create a generic class called Storage<T> where T is the type of the stored value. 
//2.	Implement a property Item that allows getting and setting the stored value. 
//3.	Test the class by storing an integer, a string, and a double. 





//using System;
//using System.Collections.Generic;

//namespace GenericStorageDemo
//{
//    public class Storage<T>
//    {
//        public T Item { get; set; }
//        public Storage(T item)
//        {
//            Item = item;
//        }
//    }

//    class Program
//    {
//        static void Main(string[] args)
//        {
//            Storage<int> intStorage = new Storage<int>(100);
//            Console.WriteLine("Stored integer: " + intStorage.Item);

//            Storage<string> stringStorage = new Storage<string>("MANMOHAN SINGH YADUVANSHI");
//            Console.WriteLine("Stored string: " + stringStorage.Item);

//            Storage<double> doubleStorage = new Storage<double>(99.99);
//            Console.WriteLine("Stored double: " + doubleStorage.Item);
//        }
//    }
//}


//Output: //Stored integer: 100
//Stored string: MANMOHAN SINGH YADUVANSHI
//Stored double: 99.99





//Question2: Implement a Generic Pair Class 
//Implement a class that stores a pair of values, where each value can be of a different type. 
//Task: 
//1.Create a generic class called Pair<T1, T2>, where T1 is the type of the first value and T2 is the type of the second value. 
//2.	Add properties First and Second to store the pair of values. 
//3.	Write a method PrintPair() to display both values. 
//4.	Test the class by creating pairs of different types, such as an integer and a string, or a string and a double. 


//using System;
//using System.Diagnostics;

//namespace GenericPairDemo
//{
//    public class Pair<T1, T2>
//    {
//        public T1 First { get; set; }
//        public T2 Second { get; set; }
//        public Pair(T1 first, T2 second)
//        {
//            First = first;
//            Second = second;
//        }
//        public void PrintPair()
//        {
//            Console.WriteLine($"First: {First}, Second: {Second}");
//        }
//    }

//    class Program
//    {
//        static void Main(string[] args)
//        {
//            Pair<int, string> pair1 = new Pair<int, string>(1, "Mango");
//            pair1.PrintPair();
//            Pair<string, double> pair2 = new Pair<string, double>("Price", 19.99);
//            pair2.PrintPair();
//            Pair<bool, char> pair3 = new Pair<bool, char>(true, 'L');
//            pair3.PrintPair();
//        }
//    }
//}



////Output: First: 1, Second: Mango
////First: Price, Second: 19.99
////First: True, Second: L




////Question3: Generic Calculator Class
////Implement a generic calculator class that works with numbers of any type (like int, double, float). 
////Task: 
////1.Create a generic class Calculator<T> that has methods for basic arithmetic operations (addition, subtraction, multiplication, and division). 
////2.	The class should work only for numeric types (use a constraint to ensure that T is a numeric type). 
////3.	Test the class with integers and doubles. 





//using System;

//public class Calculator<T>
//{
//    public T Add(T a, T b) => (dynamic)a + (dynamic)b;
//    public T Subtract(T a, T b) => (dynamic)a - (dynamic)b;
//    public T Multiply(T a, T b) => (dynamic)a * (dynamic)b;
//    public T Divide(T a, T b)
//    {
//        if ((dynamic)b == 0)
//            throw new DivideByZeroException("Cannot divide by zero.");
//        return (dynamic)a / (dynamic)b;
//    }
//}

//class Program
//{
//    static void Main()
//    {
//        var intCalc = new Calculator<int>();
//        Console.WriteLine("Int Add: " + intCalc.Add(10, 3));

//        var doubleCalc = new Calculator<double>();
//        Console.WriteLine("Double Divide: " + doubleCalc.Divide(22.5, 7.5));
//    }
//}


////Output: Int Add: 13
////Double Divide: 3.0




////Question4: Implementing a Generic Stack with an Indexer 
////Implement a generic stack (Stack<T>) that can store elements of any data type and allows users to access the elements using an indexer.
////The stack should follow the LIFO (Last In, First Out) principle. 

////Task: 
////1.Implement a generic class Stack<T> that supports standard stack operations: 
////•	Push(T item) to add an item to the stack. 
////•	Pop() to remove the top item from the stack. 
////2.	Implement an indexer to allow users to access the stack elements based on their position in the stack
////(i.e., index 0 represents the bottom of the stack, and the last index represents the top). 
////3.	Ensure exception handling for invalid index access. 




//using System;
//using System.Collections;
//using System.Collections.Generic;
//using System.Reflection;

//public class Stack<T>
//{
//    private List<T> items = new List<T>();

//    // Push: Add item to top
//    public void Push(T item)
//    {
//        items.Add(item);
//    }

//    // Pop: Remove and return top item
//    public T Pop()
//    {
//        if (items.Count == 0)
//        {
//            throw new InvalidOperationException("Stack is empty.");
//        }

//        T top = items[items.Count - 1];
//        items.RemoveAt(items.Count - 1);
//        return top;
//    }

//    // Indexer: Access item by index (0 = bottom, Count - 1 = top)
//    public T this[int index]
//    {
//        get
//        {
//            if (index < 0 || index >= items.Count)
//            {
//                throw new IndexOutOfRangeException("Invalid index.");
//            }

//            return items[index];
//        }
//    }

//    // Property to get number of elements
//    public int Count
//    {
//        get { return items.Count; }
//    }
//}

//class Program
//{
//    static void Main()
//    {
//        // Create a stack of integers
//        Stack<int> stack = new Stack<int>();

//        // Push items
//        stack.Push(10);
//        stack.Push(20);
//        stack.Push(30);

//        Console.WriteLine("Stack elements (from bottom to top):");
//        for (int i = 0; i < stack.Count; i++)
//        {
//            Console.WriteLine($"Index {i}: {stack[i]}");
//        }

//        // Pop the top item
//        int popped = stack.Pop();
//        Console.WriteLine($"\nPopped: {popped}");

//        Console.WriteLine("\nStack after popping:");
//        for (int i = 0; i < stack.Count; i++)
//        {
//            Console.WriteLine($"Index {i}: {stack[i]}");
//        }

//        // Uncomment to test exception handling:
//        // Console.WriteLine(stack[5]); // Invalid index
//        // stack.Pop(); stack.Pop(); stack.Pop(); // Too many pops
//    }
//}



//// Output:
////Stack elements(from bottom to top):
////Index 0: 10
////Index 1: 20
////Index 2: 30

////Popped: 30

////Stack after popping:
////Index 0: 10
////Index 1: 20



////Question5: Implementing a Generic Queue with an Indexer 
////Implement a generic queue (Queue<T>) that can store elements of any data type and allows users to access the elements using an indexer. The queue should follow the FIFO (First In, First Out) principle. 
////Task: 
////1.Implement a generic class Queue<T> that supports standard queue operations: 
////•	Enqueue(T item) to add an item to the queue. 
////•	Dequeue() to remove the first item from the queue. 
////2.	Implement an indexer to access the queue elements based on their position in the queue (i.e., index 0 represents the first element to be dequeued, and the last index represents the most recently added element). 
////3.	Ensure exception handling for invalid index access. 



using System;
using System.Collections;
using System.Collections.Generic;

public class Queue<T>
{
    private List<T> items = new List<T>();

    // Enqueue: Add to the end of the queue
    public void Enqueue(T item)
    {
        items.Add(item);
    }

    // Dequeue: Remove and return the first item (FIFO)
    public T Dequeue()
    {
        if (items.Count == 0)
        {
            throw new InvalidOperationException("Queue is empty.");
        }

        T front = items[0];
        items.RemoveAt(0);
        return front;
    }

    // Indexer: Access elements by position (0 = front, Count - 1 = rear)
    public T this[int index]
    {
        get
        {
            if (index < 0 || index >= items.Count)
            {
                throw new IndexOutOfRangeException("Invalid index.");
            }

            return items[index];
        }
    }

    // Property to get the number of elements
    public int Count
    {
        get { return items.Count; }
    }
}

class Program
{
    static void Main()
    {
        // Create a queue of strings
        Queue<string> queue = new Queue<string>();

        // Enqueue items
        queue.Enqueue("First");
        queue.Enqueue("Second");
        queue.Enqueue("Third");

        Console.WriteLine("Queue elements (from front to rear):");
        for (int i = 0; i < queue.Count; i++)
        {
            Console.WriteLine($"Index {i}: {queue[i]}");
        }

        // Dequeue an item
        string removed = queue.Dequeue();
        Console.WriteLine($"\nDequeued: {removed}");

        Console.WriteLine("\nQueue after dequeue:");
        for (int i = 0; i < queue.Count; i++)
        {
            Console.WriteLine($"Index {i}: {queue[i]}");
        }

        // Uncomment to test error handling
        // Console.WriteLine(queue[10]); // Invalid index
        // queue.Dequeue(); queue.Dequeue(); queue.Dequeue(); // Queue empty
    }
}


//// Output:
////Queue elements(from front to rear):
////Index 0: First
////Index 1: Second
////Index 2: Third

////Dequeued: First

////Queue after dequeue:
////Index 0: Second
////Index 1: Third
