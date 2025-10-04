# step1:  何も見ずに解く

## 解答

何を考えて解いていたか
- シンプルに問題文に沿って深く考えすに実装した
- 書き終えて冗長、かつこの実装だと無駄にpushしてしまうのでその辺りを改善しようと思考する

解法１
```typescript
function intersection(nums1: number[], nums2: number[]): number[] {
  const set1 = new Set(nums1);
  const result = [];
  for (let i = 0; i < nums2.length; i++) {
    if (set1.has(nums2[i])) {
      result.push(nums2[i]);
    }
  }
  return [...new Set(result)];
};
```

---
何を考えて解いていたか
- 解法１だとfor loop時に無邪気にpushしており、冗長だと感じif文の条件の中で追加済みの値を弾くようにした
- 最後にresultを展開しないといけないのがモヤる（arrayにしてincludeで探索してresultをする方がパッと見はわかりやすい？そもそも、もっとスマートなやり方がありそう）

解法２
```typescript
function intersection(nums1: number[], nums2: number[]): number[] {
  const set1 = new Set(nums1);
  const result = new Set<number>();
  for (let i = 0; i < nums2.length; i++) {
    if (set1.has(nums2[i]) && !result.has(nums2[i])) {
      result.add(nums2[i]);
    }
  }
  return [...result];
};
```

---
何を考えて解いていたか
- Setを使わずにarrayで実装をしてみる
- for文も冗長だったので、for ofがあったことを思い出し適用させる

解法３
```typescript
function intersection(nums1: number[], nums2: number[]): number[] {
  const result: number[] = [];
  for (const num of nums2) {
    if (nums1.includes(num) && !result.includes(num)) {
      result.push(num);
    }
  }
  return result;
};
```
