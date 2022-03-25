# Subband coding and JPEG 2000
把图像信号分成高频和低频，低频在整个图片的范围内都dominate our perception. Recursively devide low pass output into high and low frequencies.

Low pass: average
High pass: difference

适用于实时的网速变换。compressed once, sending different size of data depending on the bandwidth. JPEG need to recompress if the compress rate changes.
## Making a standard around this
random access: zoom in

## Dithering
make sure the average grey intensity is the same as the input. 

- block size matters. bigger block gives you more pixels in it to play with but also lower the resolution.

## Video compression
what is the difference between video compression and image compression?

