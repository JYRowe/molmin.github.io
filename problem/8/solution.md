考虑求出取 $l\leq i\leq r$，对于任意的 $l\leq k\leq r$，都满足 $s_i\mid s_k$ 的 $i$ 的个数，再用 $r-l+1$ 减去求出的数量即可。

根据条件，$s_i\mid s_l,\ s_i\mid s_{l+1},\ \cdots,\ s_i\mid s_r$，则 $s_i\mid\gcd_{k=l}^rs_k$，又因为 $s_i$ 也在 $\{s_l,\ s_{l+1},\ \cdots,\ s_r\}$ 中，则 $s_i=\gcd_{k=l}^rs_k=\min_{k=l}^rs_k$。

使用线段树维护区间最大公因数，以及区间中等于最小值的数的个数，故还需要维护区间最小值。每次询问，判断区间最小值是否等于区间最大公因数，如果等于，设 $t$ 为区间中等于最小值的数的个数，则答案为 $r-l+1-t$，否则，区间中不存在既为最小值又为最大公因数的数，答案为 $r-l+1$。

时间复杂度 $\Theta(t\log n)$。