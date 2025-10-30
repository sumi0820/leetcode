# step2: 他の方の解答を見る
- 参考
  - https://github.com/kt-from-j/leetcode/pull/10
  - https://github.com/nanae772/leetcode-arai60/pull/14
  - https://github.com/akmhmgc/arai60/pull/10

## 解答

#### アプローチ 1
気づいたこと/ memo
- pythonだとsetを使ってintersectionを見つけるメソッドがある
	- `set(nums1).intersection(nums2)`
- pythonだと`set(nums1) & set(nums2)`とも解けるよう
	- これをtypescriptに応用できそう？
		- nums1とnums2のsetで初期化
		- num1を展開したものをloopして、num2と比較？
		- でもこれだと一緒step1と同じになる...
	- filterを使って配列を返す方法が使えそう?

---
気づいたこと
- typescriptのSetについて改めて理解を深める
	- 勘違いポイント：Setで初期化した際に値が重複していてもそのまま -> 初期化した時点でユニークな値しか保持されない
		- >`Set` objects are collections of values. A value in the set **may only occur once**; it is unique in the set's collection. You can iterate through the elements of a set in insertion order.
		- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set
何を考えて解いていたか
- pythonの解答からヒントを得てsetとfilterを組み合わせる
	- forがなくなるのでかなりスッキリして書けてコードの流れも追いやすい
- ユニークな値になったnums1内にnums2の値があるかを検証
解法
```typescript
function intersection(nums1: number[], nums2: number[]): number[] {
  const set1 = new Set(nums1);
  const set2 = new Set(nums2);
  return [...set1].filter((num) => set2.has(num));
};
```
