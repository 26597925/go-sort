插入排序
====

## 说明
插入排序的工作原理是通过构建有序序列，对于未排序数据，在已排序序列中从后向前扫描，找到相应位置并插入。

## 步骤
1. 从第一个元素开始，该元素可以认为已经被排序
2. 取出下一个元素，在已经排序的元素序列中从后向前扫描
3. 如果该元素（已排序）大于新元素，将该元素移到下一位置
4. 重复步骤3，直到找到已排序的元素小于或者等于新元素的位置
5. 将新元素插入到该位置后
6. 重复步骤2~5

## 图片示例
![](example.gif)

## 程序示例（go）

```go 
//SortInt 插入排序
func SortInt(a []int) ([]int, int) {
	n := 0
	aLen := len(a)

	//从i=1开始，第一个数不用排序，一个数相当于已经有序了
	for i := 1; i < aLen; i++ {
		//取出新数（类似摸牌）
		tmp := a[i]

		//将新数和之前的数从后往前（从大到小）一次比较，如果新数更小,就将以前的数往后移一位
		j := i
		for ; (j > 0) && (tmp < a[j-1]); j-- {
			n++
			a[j] = a[j-1] //后移一位
		}
		//新数插入
		a[j] = tmp

	}
	return a, n
}
```