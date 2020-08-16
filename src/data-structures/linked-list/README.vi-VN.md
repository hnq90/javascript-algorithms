# Danh sách liên kết

_Đọc bài này ở các ngôn ngữ khác:_
[_English_](README.md),
[_简体中文_](README.zh-CN.md),
[_Русский_](README.ru-RU.md),
[_日本語_](README.ja-JP.md),
[_Português_](README.pt-BR.md)

Trong khoa học máy tính, một  **danh sách liên kết (linked list)** là một tập hợp tuyến tính của các phần tử dữ liệu, trong đó thứ tự tuyến tính không được cung cấp bởi vị trí vật lý của chúng trong bộ nhớ. Thay vào đso, mỗi phần tử trỏ đến phần tử tiếp theo. Nó là một cấu trúc dữ liệu bao gồm một nhóm các nút (node) cùng đại diện cho một chuỗi. Dưới dạng đơn giản nhất, mỗi nút (node) bao gồm dữ liệu và một tham chiếu (nói cách khác đó là một liên kết) đến nút (node) tiếp theo trong chuỗi. Cấu trúc này cho phép chèn hoặc loại bỏ các phần tử một cách hiệu quả từ một vị trí bất kỳ trong chuỗi trong quá trình lặp lại. Các biến thể phức tạp hơn thêm các liên kết bổ sung, cho phép chèn hoặc xoá một cách hiệu quả từ các tham chiếu của một phần tử bất kỳ. Một hạn chế của **danh sách liên kết (linked list)** là thời gian truy cập là tuyến tính (và khó để thực hiện song song (pipeline)). Truy cập nhanh hơn, chẳng hạn như truy cập ngẫu nhiên, là không khả thi. Mảng có vị trí bộ nhớ cache tốt hơn so với **danh sách liên kết (linked list)**.

![Danh sách liên kết](https://upload.wikimedia.org/wikipedia/commons/6/6d/Singly-linked-list.svg)

## Giả mã cho các thao tác cơ bản

### Chèn

```text
Add(value)
  Pre: value is the value to add to the list
  Post: value has been placed at the tail of the list
  n ← node(value)
  if head = ø
    head ← n
    tail ← n
  else
    tail.next ← n
    tail ← n
  end if
end Add
```

```text
Prepend(value)
 Pre: value is the value to add to the list
 Post: value has been placed at the head of the list
 n ← node(value)
 n.next ← head
 head ← n
 if tail = ø
   tail ← n
 end
end Prepend
```

### Tìm kiếm

```text
Contains(head, value)
  Pre: head is the head node in the list
       value is the value to search for
  Post: the item is either in the linked list, true; otherwise false
  n ← head
  while n != ø and n.value != value
    n ← n.next
  end while
  if n = ø
    return false
  end if
  return true
end Contains
```

### Xoá

```text
Remove(head, value)
  Pre: head is the head node in the list
       value is the value to remove from the list
  Post: value is removed from the list, true, otherwise false
  if head = ø
    return false
  end if
  n ← head
  if n.value = value
    if head = tail
      head ← ø
      tail ← ø
    else
      head ← head.next
    end if
    return true
  end if
  while n.next != ø and n.next.value != value
    n ← n.next
  end while
  if n.next != ø
    if n.next = tail
      tail ← n
    end if
    n.next ← n.next.next
    return true
  end if
  return false
end Remove
```

### Duyệt

```text
Traverse(head)
  Pre: head is the head node in the list
  Post: the items in the list have been traversed
  n ← head
  while n != ø
    yield n.value
    n ← n.next
  end while
end Traverse
```

### Duyệt theo chiều ngược lại

```text
ReverseTraversal(head, tail)
  Pre: head and tail belong to the same list
  Post: the items in the list have been traversed in reverse order
  if tail != ø
    curr ← tail
    while curr != head
      prev ← head
      while prev.next != curr
        prev ← prev.next
      end while
      yield curr.value
      curr ← prev
    end while
   yield curr.value
  end if
end ReverseTraversal
```

## Độ phức tạp

### Độ phức tạp về thời gian

| Truy cập    | Tìm kiếm    | Chèn | Xoá  |
| :-------: | :-------: | :-------: | :-------: |
| O(n)      | O(n)      | O(1)      | O(n)      |

### Độ phức tạp về bộ nhớ

O(n)

## Dẫn chứng

- [Wikipedia](https://en.wikipedia.org/wiki/Linked_list)
- [YouTube](https://www.youtube.com/watch?v=njTh_OwMljA&index=2&t=1s&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
