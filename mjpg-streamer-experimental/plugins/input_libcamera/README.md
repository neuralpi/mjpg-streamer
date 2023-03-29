mjpg-streamer input plugin: input_libcamera
============================================

This plugin provides JPEG data from libcamera.

Improving low-resolution images
=========

When the resolution is set low (e.g., 640x480), libcamera does not return expected images. 

For example, it shows low-quality images (camera module v.1) or a very narrow area as if it were cropped from a larger image (camera modules v2 and 3),

To fix this problem, a new option "-camver" was added. 

By giving the version number of your camera module (i.e., 1, 2, or 3) to "camver", the quality of low-resolution images improves.


```
./mjpg_streamer -i "input_libcamera.so -camver 1 -r 640x480 -f 30 -s 640x480" -o "output_http.so -w ./www"
```

Usage
=====

```
./mjpg_streamer -i "input_libcamera.so -h"

 ---------------------------------------------------------------
 Help for input plugin..: Libcamera Input plugin
 ---------------------------------------------------------------
 The following parameters can be passed to this plugin:

 [-r | --resolution ]...: the resolution of the video device,
                          can be one of the following strings:
                          QQVGA QCIF CGA QVGA CIF PAL VGA 
                          SVGA XGA HD SXGA UXGA FHD 

                          or a custom value like the following
                          example: 640x480
 [-f | --fps ]..........: frames per second
 [-b | --buffercount ]...: Set the number of request buffers.
 [-q | --quality ] .....: set quality of JPEG encoding
 [-s | --snapshot ] .....: Set the snapshot resolution, if not set will default to the maximum resolution.
 ---------------------------------------------------------------
 Optional parameters (may not be supported by all cameras):

 [-br ].................: Set image brightness (integer)
 [-co ].................: Set image contrast (integer)
 [-sa ].................: Set image saturation (integer)
 [-ex ].................: Set exposure (integer)
 [-gain ]...............: Set gain (integer)
 ---------------------------------------------------------------
```

Example
=========

```
./mjpg_streamer -i "input_libcamera.so -r 1920x1080 -f 30 -b 4 -s 4656x3496" -o "output_http.so -w ./www"
```
