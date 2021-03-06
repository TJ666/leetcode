# JavaScript实现LeetCode第67题：二进制求和
https://blog.csdn.net/woaily1346/article/details/80834236
## 题目描述
给定两个二进制字符串，返回他们的和（用二进制表示）。

输入为非空字符串且只包含数字 1 和 0。

示例 1:

输入: a = "11", b = "1"
输出: "100"
示例 2:

输入: a = "1010", b = "1011"
输出: "10101"
## 思路
错误思路：
二进制和十进制之间的转换
[百度百科](https://baike.baidu.com/item/%E5%8D%81%E8%BF%9B%E5%88%B6%E8%BD%AC%E4%BA%8C%E8%BF%9B%E5%88%B6/393189)

二进制转十进制
要从右到左用二进制的每个数去乘以2的相应次方,小数点后则是从左往右
```js
1101.01（2）=1*2^0 + 0*2^1 + 1*2^2 + 1*2^3 + 0*2^-1 + 1*2^-2 = 1+0+4+8+0+0.25 = 13.25
```
十进制整数转换为二进制整数
除2取余，逆序排列
最开始的想法是先转成十进制， 计算完成之后再转成二进制,但是没有考虑到数字类型是有长度限制的，因此这种思路不正确
```js
/**
 * @param {string} a
 * @param {string} b
 * @return {string}
 */

var addBinary = function(a, b) {
    const num1 = parseInt(a, 10);
    const num2 = parseInt(b, 10);
    return (num1+num2).toString(2);
};
```

正确的思路：
二进制字符串的加法和十进制的加法很相似， 一个是逢2进1， 一个是逢十进1

新建一个char数组，用来存放二进制的值；将a和b都转化为char数组；设置一个temp标识进位，从末尾开始遍历，分别去a对应的char、b对应的char和进位char，判断四种情况；遍历结束转化为String型结果进行输出