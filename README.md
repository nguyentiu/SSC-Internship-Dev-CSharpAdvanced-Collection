# SSC-Internship-Dev-CSharpAdvanced-Collection
# Hướng Dẫn về Collections trong C#
## 1. Giới Thiệu về Collections
Collections trong C# là các lớp giúp quản lý và thao tác với các tập hợp dữ liệu. Mỗi loại collection đều có những đặc điểm, thuộc tính và phương thức riêng biệt, phù hợp với các mục đích sử dụng khác nhau.

Trong bài viết này, chúng ta sẽ tìm hiểu các loại collection phổ biến trong C# bao gồm:

- ArrayList
- HashTable
- SortedList
- Stack (Ngăn xếp)
- Queue (Hàng đợi)
- List
## 2. ArrayList
ArrayList là một collection cho phép lưu trữ các phần tử mà không cần xác định trước kích thước của nó. Các phần tử trong ArrayList có thể có các kiểu dữ liệu khác nhau.

- Các Thuộc Tính Chính
  - Count: Trả về số phần tử có trong ArrayList.
  - Capacity: Lấy hoặc đặt số lượng phần tử mà ArrayList có thể chứa.
- Các Phương Thức Chính
  - Add(object value): Thêm một phần tử vào cuối của ArrayList.
  - Remove(object value): Xóa phần tử đầu tiên khớp với giá trị được chỉ định.
  - Insert(int index, object value): Thêm một phần tử vào ArrayList tại chỉ số xác định.
  - Clear(): Xóa tất cả các phần tử khỏi ArrayList.
  - Contains(object value): Kiểm tra xem ArrayList có chứa một phần tử cụ thể không.
Ví Dụ Minh Họa
```csharp
Copy code
using System;
using System.Collections;

class Program
{
    static void Main()
    {
        ArrayList arrayList = new ArrayList();
        arrayList.Add(1);
        arrayList.Add("Hello");
        arrayList.Add(3.14);

        Console.WriteLine("Initial ArrayList:");
        foreach (var item in arrayList)
        {
            Console.WriteLine(item);
        }

        arrayList.Remove(1); // Xóa phần tử 1
        Console.WriteLine("\nArrayList after removing 1:");
        foreach (var item in arrayList)
        {
            Console.WriteLine(item);
        }

        arrayList.Insert(1, 42); // Chèn 42 vào vị trí chỉ số 1
        Console.WriteLine("\nArrayList after inserting 42 at index 1:");
        foreach (var item in arrayList)
        {
            Console.WriteLine(item);
        }
    }
}
```
## 3. HashTable
HashTable là một collection lưu trữ dữ liệu dưới dạng các cặp khóa-giá trị (key-value). Các phần tử trong HashTable được truy xuất thông qua khóa của chúng.

- Các Thuộc Tính Chính
  - Count: Trả về số cặp khóa-giá trị có trong HashTable.
  - Keys: Trả về một tập hợp chỉ đọc các khóa trong HashTable.
  - Values: Trả về một tập hợp chỉ đọc các giá trị trong HashTable.
Các Phương Thức Chính
  - Add(object key, object value): Thêm một cặp khóa-giá trị vào HashTable.
  - Remove(object key): Xóa cặp khóa-giá trị tương ứng với khóa được chỉ định.
  - ContainsKey(object key): Kiểm tra xem HashTable có chứa khóa cụ thể không.
  - ContainsValue(object value): Kiểm tra xem HashTable có chứa giá trị cụ thể không.
  - Clear(): Xóa tất cả các cặp khóa-giá trị khỏi HashTable.
Ví Dụ Minh Họa
```csharp
Copy code
using System;
using System.Collections;

class Program
{
    static void Main()
    {
        Hashtable hashtable = new Hashtable();
        hashtable.Add(1, "One");
        hashtable.Add(2, "Two");
        hashtable.Add(3, "Three");

        Console.WriteLine("Initial HashTable:");
        foreach (DictionaryEntry entry in hashtable)
        {
            Console.WriteLine($"{entry.Key}: {entry.Value}");
        }

        hashtable.Remove(2); // Xóa khóa 2
        Console.WriteLine("\nHashTable after removing key 2:");
        foreach (DictionaryEntry entry in hashtable)
        {
            Console.WriteLine($"{entry.Key}: {entry.Value}");
        }

        Console.WriteLine("\nChecking if HashTable contains key 1:");
        Console.WriteLine(hashtable.ContainsKey(1)); // true
    }
}
```
## 4. SortedList
SortedList cũng là một collection lưu trữ dữ liệu dưới dạng các cặp khóa-giá trị, nhưng khác với HashTable, nó lưu trữ các cặp này theo thứ tự tăng dần của khóa.

- Các Thuộc Tính Chính
  - Count: Trả về số cặp khóa-giá trị có trong SortedList.
  - Keys: Trả về một tập hợp các khóa trong SortedList.
  - Values: Trả về một tập hợp các giá trị trong SortedList.
- Các Phương Thức Chính
  - Add(object key, object value): Thêm một cặp khóa-giá trị vào SortedList.
  - Remove(object key): Xóa cặp khóa-giá trị tương ứng với khóa được chỉ định.
  - GetByIndex(int index): Lấy giá trị tại vị trí chỉ số được chỉ định.
  - IndexOfKey(object key): Trả về chỉ số của một khóa cụ thể.
  - Clear(): Xóa tất cả các cặp khóa-giá trị khỏi SortedList.
Ví Dụ Minh Họa
```csharp
Copy code
using System;
using System.Collections;

class Program
{
    static void Main()
    {
        SortedList sortedList = new SortedList();
        sortedList.Add(3, "Three");
        sortedList.Add(1, "One");
        sortedList.Add(2, "Two");

        Console.WriteLine("Initial SortedList:");
        foreach (DictionaryEntry entry in sortedList)
        {
            Console.WriteLine($"{entry.Key}: {entry.Value}");
        }

        sortedList.Remove(1); // Xóa khóa 1
        Console.WriteLine("\nSortedList after removing key 1:");
        foreach (DictionaryEntry entry in sortedList)
        {
            Console.WriteLine($"{entry.Key}: {entry.Value}");
        }

        Console.WriteLine("\nValue at index 0:");
        Console.WriteLine(sortedList.GetByIndex(0)); // Two
    }
}
```
## 5. Stack - Ngăn Xếp
Stack là một collection tuân theo nguyên tắc LIFO (Last In, First Out), nghĩa là phần tử cuối cùng được thêm vào sẽ là phần tử đầu tiên được lấy ra.

- Các Thuộc Tính Chính
  - Count: Trả về số phần tử có trong Stack.
- Các Phương Thức Chính
  - Push(object obj): Thêm một phần tử vào đỉnh của Stack.
  - Pop(): Xóa và trả về phần tử ở đỉnh của Stack.
  - Peek(): Trả về phần tử ở đỉnh của Stack mà không xóa nó.
  - Contains(object obj): Kiểm tra xem Stack có chứa một phần tử cụ thể không.
  - Clear(): Xóa tất cả các phần tử khỏi Stack.
Ví Dụ Minh Họa
```csharp
Copy code
using System;
using System.Collections;

class Program
{
    static void Main()
    {
        Stack stack = new Stack();
        stack.Push(10);
        stack.Push(20);
        stack.Push(30);

        Console.WriteLine("Initial Stack:");
        foreach (var item in stack)
        {
            Console.WriteLine(item);
        }

        Console.WriteLine("\nTop element in Stack (Peek):");
        Console.WriteLine(stack.Peek()); // 30

        stack.Pop(); // Xóa phần tử ở đỉnh
        Console.WriteLine("\nStack after Pop:");
        foreach (var item in stack)
        {
            Console.WriteLine(item);
        }

        Console.WriteLine("\nChecking if Stack contains 20:");
        Console.WriteLine(stack.Contains(20)); // true
    }
}
```
## 6. Queue - Hàng Đợi
Queue là một collection tuân theo nguyên tắc FIFO (First In, First Out), nghĩa là phần tử đầu tiên được thêm vào sẽ là phần tử đầu tiên được lấy ra.
- Các Thuộc Tính Chính
  - Count: Trả về số phần tử có trong Queue.
- Các Phương Thức Chính
  - Enqueue(object obj): Thêm một phần tử vào cuối của Queue.
  - Dequeue(): Xóa và trả về phần tử ở đầu của Queue.
  - Peek(): Trả về phần tử ở đầu của Queue mà không xóa nó.
  - Contains(object obj): Kiểm tra xem Queue có chứa một phần tử cụ thể không.
  - Clear(): Xóa tất cả các phần tử khỏi Queue.
Ví Dụ Minh Họa
```csharp
Copy code
using System;
using System.Collections;

class Program
{
    static void Main()
    {
        Queue queue = new Queue();
        queue.Enqueue(100);
        queue.Enqueue(200);
        queue.Enqueue(300);

        Console.WriteLine("Initial Queue:");
        foreach (var item in queue)
        {
            Console.WriteLine(item);
        }

        Console.WriteLine("\nFirst element in Queue (Peek):");
        Console.WriteLine(queue.Peek()); // 100

        queue.Dequeue(); // Xóa phần tử ở đầu hàng đợi
        Console.WriteLine("\nQueue after Dequeue:");
        foreach (var item in queue)
        {
            Console.WriteLine(item);
        }

        Console.WriteLine("\nChecking if Queue contains 200:");
        Console.WriteLine(queue.Contains(200)); // true
    }
}
```
