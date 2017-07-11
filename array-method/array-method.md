# 常用方法
### Array 方法
`var a = [1,2,3,4,5]`



| 方法 | 用法 | 返回值 | 原数组a  | 说明 |
| ----- | ---- | ----- | ---- | ---- | ---- |
| concat |  a.concat(['a','b','c','d','e'])  | [1, 2, 3, 4, 5, "a", "b", "c", "d", "e"] | 不变 |合并两个数组为一个新数组 |
| join | a.join('-')  | "1-2-3-4-5" | 不变 | 通过连字符生成字符串 |
| sort | a.sort() a.sort(function(){}) | 排序好的a | 排序好的a | 默认的函数一般不用，定义新函数替代，返回0相等，返回负数，第一个在前，返回正数，第二个在前 |
| pop | a.pop() | 5 | [1,2,3,4]| 移除a中最后一个元素，并返回该元素，a为空则返回undefined |
| shift | a.shift() | 1 | [2,3,4,5] | 移除a中第一个元素，并返回该元素，a为空则返回undefined,比POP慢很多 |
| push |  a.push(['a','b','c','d','e']) | 6 | [1, 2, 3, 4, 5, ["a", "b", "c", "d", "e"]] | 将b作为一个数组元素加到a中，返回a的长度 |
| unshift | a.unshift('a','b')  | 7 | ["a", "b", 1, 2, 3, 4, 5] | 和push类似，把元素插入到a的头部，返回新a的长度 |
| reverse | a.reverse() | [5, 4, 3, 2, 1] | [5, 4, 3, 2, 1] | 返回修改后的数组 |
| slice | a.slice(start,end) a.slice(1,3) | [2,3] | 不变 | 从a[start]开始，到a[end],结束复制出一个新数组, 无end则end默认为a.length, end<0,则为end = a.length+end |
| splice |  a.splice(start, deleteCount) a.splice(1,2) | [2,3] | [1,4,5]| 从a中移除多个元素，返回包含移除元素的数组，start为开始位置，deleteCount为移除个数 |
| splice |  a.splice(start, deleteCount, item...) a.splice(1,2,'yoyo','haha') | [2,3] | [1,'yoyo','haha',4,5] | 从a中移除多个元素，返回包含移除元素的数组，start为开始位置，deleteCount为移除个数, 把插入的item放在start的位置|


