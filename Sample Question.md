## 1
1. Because according the Nyquist theorem, the sample rate should at least be twice as the maximum frequency of the signal. Because the low-pass filter can't ideally cut the signal to 20kHz, so CD uses a little bit higher than 40kHz to sample it. Nyquist rate for human speech is 8kHz.
2. 


## 当采样率低于$2\times f$时的观测频率
观测频率为$f_a$, 令$N$为让$N\times f_{sample}$最接近$f$的整数。则有
$$f_a = |f-N\times f_{sample}|$$