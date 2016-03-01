# PyFFmpeg #

## Notice ##

**NEW PROJECT PAGE CAN BE FOUND HERE: https://mhaller.github.io/pyffmpeg/**

Due to major changes in the API, it won't compile with modern versions of ffmpeg.

There is no exact equivalent of pyffmpeg existing, but we do recommend that you have a look at projects like OpenCV and Media Lovin Toolkit - as they are generally able to similar features.

## Description ##

[FFmpeg](http://ffmpeg.mplayerhq.hu/) is a software package containing libraries and utilities for encoding, decoding and converting audio and video files. It includes libavcodec, a leading audio/video codec library that can work with most video and audio formats. This library generally uses its own codec. And thus it does not depend on your operating system installed libraries. Using FFmpeg and libavcodec you can develop applications that can parse and display video files and be sure they will work on most platform, including of course Linux, Macintosh, and Windows boxes.

The libavcodec and libavformat libraries of the FFmpeg project are quite complex to use, especially from Python. PyFFmpeg provides a simple object oriented interface to those libraries. PyFFmpeg is a wrapper around FFmpeg's libavcodec, libavformat and libavutil libraries whose main purpose is to provide access to individual frames of video files of various [formats and codecs](http://www.ffmpeg.org/general.html) (such as mpg, mp4, mov, avi, flv, mkv, wmf, and webm). It also provides access to audio data.

### Mailing Lists ###

The project has a [user questions](http://groups.google.com/group/pyffmpeg) and a [development discussions](http://groups.google.com/group/pyffmpeg-dev) mailing lists.

# PyFFmpeg 2.2 alpha #

Support for [FFmpeg version git-35d7d6f](http://git.ffmpeg.org/?p=ffmpeg.git;a=snapshot;h=35d7d6f7489c75aaa2fcb39820fb25b0fd44524b;sf=tgz) (Mar 2011) is provided by the [PyFFmpeg 2.2 alpha development version](https://github.com/mhaller/pyffmpeg).

# PyFFmpeg 2.1 #

We have recenlty performed a complete rewrite of PyFFmpeg. Now, PyFFmpeg can work with NumPy, Python Imaging Library (PIL), and Cairo. It supports **video and audio decoding**. It also supports reading from internet streams.

[Download PyFFmpeg 2.1](http://code.google.com/p/pyffmpeg/downloads/list)

### Usage Examples ###
Here is a usage example for PyFFmpeg:

```
from pyffmpeg import FFMpegReader

## create the reader object
mp=FFMpegReader()

## open an audio-video file
mp.open("your file.mpg")
tracks=mp.get_tracks()

## define a function to be called back each time a frame is read...
def obs(f):
  display(f[2]) # you have to write your display function

tracks[0].set_observer(obs)

mp.run()
```

Other examples can be found in the example directory of the package.

### PIL ###

PyFFmpeg supports [Python Imaging Library (PIL)](http://www.pythonware.com/products/pil/), but functionality is limited to RGB color space for frames and audio decoding is not possible while PIL support is activated.

### NumPy ###

[NumPy](http://numpy.scipy.org/) as the  scientific computing package for Python is required for audio and video decoding with PyFFmpeg. However, the dependency of PyFFmpeg on NumPy is optional, so that PyFFmpeg can be used only with PIL for easy access to frames of a video track in RGB without audio decoding.


# PyFFmpeg 1.0 #

PyFFmpeg has stayed in minimal status where it could be used to extract individual frames from video files and create [PIL](http://www.pythonware.com/products/pil/) image objects from them.

While there were several Python libraries that offer to play video files most
of them did not provide any API to extract individual frames, and this is the
reason PyFFmpeg was created.

A more complex wrapper around FFmpeg has been implemented within [PyMedia](http://pymedia.org/).  However, PyMEDIA is now based on and old version of FFmpeg, and probably also need some minor rewrites.

### Example ###

Here's a simple example that extracts the first frame from a video file and saves it in .png format. You'll need [PIL](http://www.pythonware.com/products/pil/) to run it.

```
import pyffmpeg

stream = pyffmpeg.VideoStream()
stream.open('myvideo.avi')
image = stream.GetFrameNo(0)
image.save('firstframe.png')
```