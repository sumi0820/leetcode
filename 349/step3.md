# step3: 3回ミスなく書く

## 解答
- シンプルでコードの流れが追いやすいsetを使用した記述で実装

```typescript
function intersection(nums1: number[], nums2: number[]): number[] {
  const set1 = new Set(nums1);
  const set2 = new Set(nums2);
  return [...set1].filter((num) => set2.has(num));
};
```

- 反省
	- 二分探索や時間計算量、空間計算量などの意識が全然なかった
	- 他の方の解答を見ると自分の発想力の幅が限定的だと感じたので、そこをどのように拡張していくかが課題だと思った
