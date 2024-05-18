# 請寫出heap sort搜尋樹的演算法
- 堆積排序（Heap Sort）是一種利用堆積（Heap）結構來完成排序的演算法。

- 以下是堆積排序的主要步驟：

## 建立最大堆積（Max Heap）：
- 將待排序的陣列製作成最大堆積。
- 最大堆積是一種近似完全二元樹，其中每個節點的值都大於或等於其子節點的值。
- 透過遞迴或迭代，將陣列轉換為最大堆積。

## 排序：
- 取出最大堆積的根節點（即最大值）。
- 將根節點與最後一個節點交換位置。
- 排除已排序的最大值，重新調整剩餘節點，使其仍保持最大堆積的性質。
- 重複上述步驟，直到所有節點都被取出並排序。

## 時間複雜度：
- 堆積排序的平均和最壞情況時間複雜度均為 O(nlogn)

Python 實作：
Python

def adjust(arr, i, n):
    child = 2 * i
    item = arr[i - 1]

    while child <= n:
        if child < n and arr[child - 1] < arr[child]:
            child += 1

        if item >= arr[child - 1]:
            break

        arr[(child // 2) - 1] = arr[child - 1]
        child *= 2

    arr[int(child // 2) - 1] = item

def heapify(arr, n):
    for i in range(int(n // 2), 0, -1):
        adjust(arr, i, len(arr))

def heapSort(arr, n):
    heapify(arr, len(arr))

    for i in range(n, 1, -1):
        arr[i - 1], arr[0] = arr[0], arr[i - 1]
        adjust(arr, 1, i - 1)

    return arr

# Example usage:
arr = [5, 10, 2, 7, 1]
sorted_arr = heapSort(arr, len(arr))
print("排序後:", sorted_arr)
