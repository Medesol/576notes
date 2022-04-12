# Subband coding and JPEG 2000
## JPEG 2000
From a single bit stream, JPEG 2000 allows extraction of:
- Different resolution 
- Different pixel fidelities
- Different regions of interest
- Different color component

### Reasons that JPEG 2000 will be welcomed in the future
- Random access 
- Better quality at same bitrate as JPEG 
- Compressed image domain manipulation
- Encode once and decode on different platform


把图像信号分成高频和低频，低频在整个图片的范围内都dominate our perception. Recursively devide low pass output into high and low frequencies.

Low pass: average
High pass: difference

适用于实时的网速变换。compressed once, sending different size of data depending on the bandwidth. JPEG need to recompress if the compress rate changes.
## Making a standard around this
random access: zoom in

## Dithering
When the device has fewer intensities than the image, how can we reproduce the image?
make sure the average grey intensity is the same as the input. 

- Quantize from N to n levels
- When $n=2$
	- Halftoning
	- Dithering 
	- Error Diffusion

### Halftoning 
Represent image by an array of circles with diameter proportional to blackness (1-Intensity).

Because human visual system performs *spatial integration*. 
### Dithering 
让显示图片像素点周围的平均值等于原图片该点的intensity.
### Error Diffusion 
将error扩张到像素点的周围，让整张图的总体error接近0.

- block size matters. bigger block gives you more pixels in it to play with but also lower the resolution.

## Video compression
what is the difference between video compression and image compression?

