# Audio Compression
## Sound is Waveform
1. DPCM
	1. Level 0 prediction
	2. Level 1 prediction (linear)
	3. ...
2. Delta modulation (represent difference by $\Delta$, in which $\Delta$ can be some small value)
	1. $+\Delta$ represented by 1
	2. $-\Delta$ represented by 0
	3. works well when the signal changes fast. Higher frequency leads to lower difference between samples.
3. ADPCM (Adaptive DPCM, adaptive bits used to represent the difference)
4. Companding
	1. A Law 13bits
	2. $\mu$ Law 12bits
## Sound is Perceived
In the video domain, quantization table does not change, but in the audio domain, quantization table is dynamic.
## Sound is Produced
Synthesize sound. Mainly used in human voice compression.
### LPC: linear predictive coding
Compute parameters $\alpha_1, \alpha_2 ... \alpha_p$ so that:
$$x(i)=\sum_{k=1}^{p}{\alpha_i}x(|i-k|)$$
This only works on voiced window. 
- voiced window: frequency between 0-4kHz
- unvoiced window: frequency outside the voiced one.

### Decoder
#### voiced 
give the LPC parameters into impulse train to get the $s_1, s_2 ... s_{239}$
#### unvoiced 
Random noise generator.

A vocal track model will be used to choose from voiced and unvoiced sample to produce final speech.
## Sound is Performed
midi format. Good for representing music but not good for speech.
## Coding standards
- MPEG
	- MPEG 1 (3 layers are backward compatible)
		- Layer 1
		- Layer 2
		- Layer 3(MP-3)
			- came at the internet bandwidth increased to 100kb/s
			- made audio streaming possible
			- 提升主要来自modified DCT, Huffman coding and buffer
			- MDCT会一个block一个block单独处理，低bitrate的情况下，block之间会有很大误差(discontinuity)，在音频里尤其明显，会有明显的click
				- increase bitrate
				- MDCT: make blocks overlap
			- Huffman coding: variable bitrate so need a buffer.
			- When the buffer is getting full, it sends to bit allocation to quantize more, so that the buffer can get empty
		- The complexity arises from the additional computation.
		- Why there is bitrate allocation encoder in audio compression but not in video compression? Bitrate allocation is dynamic in audio compression 
	- MPEG 2 theatre style surrounding sound
		- AAC: Advanced audio codec
			- Non-backward compatible: because the bitrate syntax must change
- Dolby (proprietary standard 专利标准) 
	- Create the best sounding sound.
	- Doesn't scale coefficients, represents them as float numbers.
	- Mostly the same as MPEG
- ITU
	- G.711 designed for telephone bandwidth
	- G.722 designed for teleconference
	- G.726/G.727 based on ADPCM 
	- G.729/G.723 based on LPC
