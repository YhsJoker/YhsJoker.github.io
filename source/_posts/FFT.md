---
title: 多项式乘法（FFT）
date: 2023-10-18 23:17:14
tags:
  - [笔记打卡]
categories: 笔记
description: 笔记打卡活动。
---

## 一、概念概述

快速傅里叶变换 (fast Fourier transform), 即利用计算机计算离散傅里叶变换（DFT)的高效、快速计算方法的统称，简称FFT。快速傅里叶变换是1965年由J.W.库利和T.W.图基提出的。采用这种算法能使计算机计算离散傅里叶变换所需要的乘法次数大为减少，特别是被变换的抽样点数N越多，FFT算法计算量的节省就越显著。

离散傅里叶变换（Discrete Fourier Transform，缩写为 DFT），是傅里叶变换在时域和频域上都呈离散的形式，将信号的时域采样变换为其 DTFT 的频域采样。

FFT 是一种高效实现 DFT 的算法，称为快速傅立叶变换（Fast Fourier Transform，FFT）。它对傅里叶变换的理论并没有新的发现，但是对于在计算机系统或者说数字系统中应用离散傅立叶变换，可以说是进了一大步。快速数论变换 (NTT) 是快速傅里叶变换（FFT）在数论基础上的实现。

在 1965 年，Cooley 和 Tukey 发表了快速傅里叶变换算法。事实上 FFT 早在这之前就被发现过了，但是在当时现代计算机并未问世，人们没有意识到 FFT 的重要性。一些调查者认为 FFT 是由 Runge 和 König 在 1924 年发现的。但事实上高斯早在 1805 年就发明了这个算法，但一直没有发表。

## 二、FFT算法概述

考虑对两个多项式做乘法，如果运用系数表示法，显然需要 $O(n^2)$ 的时间复杂度，而如果已知两个多项式的点值表示法，则只需要 $O(n)$ 的时间复杂度。因为只需要将对应的点值纵坐标相乘就可以了。但是我们将一个多项式从系数表示法改为点值表示法（称为求值）需要 $O(n^2)$ 的复杂度（因为每个横坐标都需要 $O(n)$ 的时间去计算），

而将一个点值表示法改为系数表示法（称为插值）则需要 $O(n^3)$ 的复杂度来做高斯消元。但是只要我们将这两步都优化至低于 $O(n^2)$ 的复杂度，就可以得到一个比直接用系数表示法乘更优的做法。

而求出一个 $n$ 次多项式在每个 $n$ 次单位根下的点值的过程，被称为离散傅里叶变换，而将这些点值重新插值成系数表示法的过程，叫做离散傅里叶逆变换。

## 三、理论知识

设一个 $n$ 次多项式

$$A(x)=a_0+a_1x+a_2x^2+\dots +a_{n-1}x^{n-1}$$

将其每项按所在位置的奇偶性分成两部分，得

$$A(x)=(a_0+a_2x^2+\dots +a_{n-2}x^{n-2})+(a_1x+a_3x^3+\dots+a_{n-1}x^{n-1})$$

设

$$A_1(x)=a_0+a_2x+\dots +a_{n-2}x^{\frac{n}{2}-1}$$

$$A_2(x)=a_1+a_3x+\dots +a_{n-2}x^{\frac{n}{2}-1}$$

那么有

$$A(x)=A_1(x^2)+xA_2(x^2)$$

假设 $0\le k< \frac{n}{2}$ ，将 $x = w^k_n$ 代入，得

$$A(w^k_n)=A_1(w^{2k}_n)+w^k_nA_2(w^{2k}_n)$$

将 $x = w^{k+\frac{n}{2}}_n$ 代入，得

$$A(w^{k+\frac{n}{2}}_n)=A_1(w^{2k}_n)-w^k_nA_2(w^{2k}_n)$$

因此，我们在求 $A(w^k_n)$ 时，可以 $O(1)$ 得到第二个式子的值。

第一个式子在求出前半段时，第二个式子刚好求过后半段，并且因为子问题还满足原问题的性质，因此可以递归分治求解，总时间复杂度为 $O(n\log n)$ 。

## 四、代码实现

```cpp
using ll = long long;
using db = double;

const db pi = acos(-1);

struct cpx{
	db x, y;
	cpx operator + (const cpx& r){
		return {x + r.x, y + r.y};
	}
	cpx operator - (const cpx& r){
		return {x - r.x, y - r.y};
	}
	cpx operator * (const cpx& r){
		return {x * r.x - y * r.y, x * r.y + y * r.x};
	}
};

void fft(cpx a[], int inv, int rev[], int tot){
	for(int i = 0; i < tot; i++){
		if(i < rev[i]){
			swap(a[i], a[rev[i]]);
		}
	}
	for(int mid = 1; mid < tot; mid <<= 1){
		auto w1 = cpx({cos(pi / mid), inv * sin(pi / mid)});
		for(int i = 0; i < tot; i += mid * 2){
			auto wk = cpx({1, 0});
			for(int j = 0; j < mid; j++, wk = wk * w1){
				auto x = a[i + j], y = wk * a[i + j + mid];
				a[i + j] = x + y, a[i + j + mid] = x - y;
			}
		}
	}
}

void fftmul(vector<ll>& a, vector<ll>& b){
	static cpx c[N * 4], d[N * 4];
	static int rev[N * 4];
	int bit = 0, tot = 0;
	int n = a.size() - 1, m = b.size() - 1;
	while((1 << bit) < n + m + 1) bit++;
	tot = 1 << bit;
	for(int i = 0; i < tot; i++) rev[i] = 0;
	for(int i = 0; i < tot; i++){
		rev[i] = (rev[i >> 1] >> 1) | ((i & 1) << (bit - 1));
	}
	for(int i = 0; i <= n; i++) c[i].x = a[i], c[i].y = 0;
	for(int i = n + 1; i < tot; i++) c[i] = {0, 0};
	for(int i = 0; i <= m; i++) d[i].x = b[i], d[i].y = 0;
	for(int i = m + 1; i < tot; i++) d[i] = {0, 0};
	fft(c, 1, rev, tot), fft(d, 1, rev, tot);
	for(int i = 0; i < tot; i++) c[i] = c[i] * d[i];
	fft(c, -1, rev, tot);
	a.resize(n + m + 1);
	for(int i = 0; i <= n + m; i++) a[i] = (int)(c[i].x / tot + 0.5);
}
```



