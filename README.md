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
`ArrayList` là một collection cho phép lưu trữ các phần tử mà không cần xác định trước kích thước của nó. Các phần tử trong `ArrayList` có thể có các kiểu dữ liệu khác nhau.

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
Trong ví dụ trên, chúng ta khởi tạo một `ArrayList` và thêm các phần tử với các kiểu dữ liệu khác nhau. `ArrayList` linh hoạt nhưng không an toàn về kiểu dữ liệu, vì vậy nếu bạn biết trước kiểu dữ liệu sẽ được lưu trữ, hãy cân nhắc sử dụng `List<T>`.
## 3. HashTable
`HashTable` là một collection lưu trữ dữ liệu dưới dạng các cặp khóa-giá trị (key-value). Các phần tử trong `HashTable` được truy xuất thông qua khóa của chúng.

- Các Thuộc Tính Chính
  - Count: Trả về số cặp khóa-giá trị có trong HashTable.
  - Keys: Trả về một tập hợp chỉ đọc các khóa trong HashTable.
  - Values: Trả về một tập hợp chỉ đọc các giá trị trong HashTable.
- Các Phương Thức Chính
  - Add(object key, object value): Thêm một cặp khóa-giá trị vào HashTable.
  - Remove(object key): Xóa cặp khóa-giá trị tương ứng với khóa được chỉ định.
  - ContainsKey(object key): Kiểm tra xem HashTable có chứa khóa cụ thể không.
  - ContainsValue(object value): Kiểm tra xem HashTable có chứa giá trị cụ thể không.
  - Clear(): Xóa tất cả các cặp khóa-giá trị khỏi HashTable.
Ví Dụ Minh Họa
```csharp

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
`HashTable` phù hợp khi bạn cần lưu trữ và truy xuất dữ liệu dựa trên một khóa duy nhất.
## 4. SortedList
`SortedList` cũng là một collection lưu trữ dữ liệu dưới dạng các cặp khóa-giá trị, nhưng khác với `HashTable`, nó lưu trữ các cặp này theo thứ tự tăng dần của khóa.

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
`SortedList` hữu ích khi bạn cần lưu trữ dữ liệu dưới dạng các cặp key-value và yêu cầu thứ tự sắp xếp của các khóa.
## 5. Stack - Ngăn Xếp
`Stack` là một collection tuân theo nguyên tắc LIFO (Last In, First Out), nghĩa là phần tử cuối cùng được thêm vào sẽ là phần tử đầu tiên được lấy ra.

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
`Stack` thường được sử dụng trong các thuật toán như duyệt cây hoặc thực hiện quay lui (backtracking).
## 6. Queue - Hàng Đợi
`Queue` là một collection tuân theo nguyên tắc FIFO (First In, First Out), nghĩa là phần tử đầu tiên được thêm vào sẽ là phần tử đầu tiên được lấy ra.
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
`Queue` thường được sử dụng trong các tình huống như hàng đợi xử lý dữ liệu, hàng đợi yêu cầu trong mạng.
## 7. List
`List` là một collection kiểu generic, cho phép lưu trữ các phần tử theo kiểu dữ liệu cụ thể. `List` cung cấp các phương thức mạnh mẽ để thêm, xóa và tìm kiếm các phần tử.

- Các Thuộc Tính Chính
  - Count: Trả về số phần tử có trong List.
  - Capacity: Lấy hoặc đặt số lượng phần tử mà List có thể chứa.
  - Item[int index]: Truy cập phần tử tại chỉ số xác định.
- Các Phương Thức Chính
  - Add(T item): Thêm một phần tử vào cuối của List.
  - Remove(T item): Xóa phần tử đầu tiên khớp với giá trị được chỉ định.
  - Insert(int index, T item): Thêm một phần tử vào List tại chỉ số xác định.
  - Clear(): Xóa tất cả các phần tử khỏi List.
  - Contains(T item): Kiểm tra xem List có chứa một phần tử cụ thể không.
  - IndexOf(T item): Trả về chỉ số của phần tử đầu tiên khớp với giá trị được chỉ định.
  - RemoveAt(int index): Xóa phần tử tại chỉ số xác định.
  - Sort(): Sắp xếp các phần tử trong List.
Ví Dụ Minh Họa
```csharp

using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        List<string> list = new List<string>();
        list.Add("Apple");
        list.Add("Banana");
        list.Add("Cherry");

        Console.WriteLine("Initial List:");
        foreach (var item in list)
        {
            Console.WriteLine(item);
        }

        list.Remove("Banana"); // Xóa phần tử "Banana"
        Console.WriteLine("\nList after removing 'Banana':");
        foreach (var item in list)
        {
            Console.WriteLine(item);
        }

        list.Insert(1, "Blueberry"); // Chèn "Blueberry" vào vị trí chỉ số 1
        Console.WriteLine("\nList after inserting 'Blueberry' at index 1:");
        foreach (var item in list)
        {
            Console.WriteLine(item);
        }

        list.Sort(); // Sắp xếp danh sách
        Console.WriteLine("\nSorted List:");
        foreach (var item in list)
        {
            Console.WriteLine(item);
        }
    }
}
```
`List<T>` là một lựa chọn phổ biến khi bạn cần một danh sách các phần tử kiểu dữ liệu giống nhau với khả năng thay đổi kích thước tự động.
## 8. Tổng Kết
Trong C#, các collections cung cấp những công cụ mạnh mẽ để làm việc với tập hợp dữ liệu. Mỗi loại collection có những đặc điểm và phương thức riêng, cho phép bạn lựa chọn giải pháp phù hợp với nhu cầu của mình.
