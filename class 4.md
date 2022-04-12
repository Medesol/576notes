VCompress only data but preserve information
- data: a stream of bits
- information: the organization of data

Claude Shannon:
1. How can we efficiently communicate?
2. How can we reliably communicate?

source → encoder → channel → decoder → receiver

## Lowest average code length(ACL)

$$H=-\sum{p_i\log{p_i}}$$
## Lossless compression
- Compression is **not guaranteed**.
- Variable bit rate(VBR)
	- sometimes the buffer will be overflow

Algorithms:
- Removing repetition
	- run length
	- repetition suppression
- Pattern based
	- LZW algorithm(GIF)
- Statistical
	- Huffman
	- Arithmetic 
	- Shannon fano
	- Goulomb

### Runlength encoding
aaaaabbbbaaabbbbbab -> 5a4b3a5b1a1b
behave well when the entropy is **low**.
### LZW
Build a dictionary of patterns to encode. Used in G-zip.

Considerations:
- The dictionary needs to stop somewhere: index 12-13 bits
- Rebuild the dictionary from the encoded stream.
### Huffman 
- They are prefix code, so works.
- The decoder will get the binary tree or probability or the dictionary.
- The coding is not unique. We can randomly flip each branch to get different coding.
- Guaranteed to get a ACL of H+1.
- ACL=H的情况：
	- 完全平衡树
	- 完全不平衡树

### Arithmetic coding
Map the given string to a unique number.

问题：
- 不能无限往下走，因为小数精度有限
	- block of symbols and convert it to a number。把一个string拆分成多个block
	- 现实中都是数据流，也无法等到所有数据到手上再encode。
	- 需要补齐后面的0来保证是前缀码。
- 如何找到least number of bits to represent the threshold.

## Lossy compression
Designing a lossy compression algorithm is much more difficult than designing a lossless one. Very hard to decide what to throw away. Choose lossy compression if possible.

- Compression is **guaranteed**.
- Constant bit rate(CBR)

Algorithms:
- Signal importance
	- quantization
	- filtering
	- subsampling
- Prediction based
	- DPCM 
	- motion compensation (video compression)
- Frequency domain based
	- DFT
	- DCT
	- DST
	- wavelets
	- KLT
- Hybrid: Use one of the lossy method and use statistical method to compress it again
	- JPEG
	- MPEG

### DPCM
Store differences between samples and requantize them. 还可以做更完善的预测来减小difference的range。同时做差之后的结果entropy更低，无损压缩时平均码长更小。

问题是error会被积累，$y_n=y_{n-1}+\sum{e_i}$. In order to address that, we need to introduce closed loop. Let $d_2=y_2-\hat{y_1}$ instead of $d_2=y_2-y_1$, then the error will not get accumulated.
### Vector Quantization
以vector为单位，将codebook中不同的code vector编一个index，然后接受input vector，对于每一个input vector做vector search来判断它和哪个code vector最接近。最终得到一系列index。
### Transform coding
Used in image compression. Transform from the given domain into another domain whose entropy is lower. 

- Not quantize all frequencies.
- Put more bits to important frequencies and less bits to those not important.

### Subband coding


