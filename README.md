[![PyPI version shields.io](https://img.shields.io/pypi/v/img2texture.svg)](https://pypi.python.org/pypi/img2texture/)
[![Generic badge](https://img.shields.io/badge/Python-3.7+-blue.svg)](#)
[![Generic badge](https://img.shields.io/badge/OS-Windows%20|%20macOS%20|%20Linux-blue.svg)](#)
[![Downloads](https://pepy.tech/badge/img2texture/month)](https://pepy.tech/project/img2texture)

# [img2texture](https://github.com/rtmigo/img2texture#readme)

Command line utility for converting images to seamless tiles.
It overlays images with an alpha gradient.

The resulting tiles can be used as textures in games, compositing and 3D modeling applications, etc.



*⚠️ If the images below are not displayed, check out the 
[original of this document on GitHub](https://github.com/rtmigo/img2texture#readme).*

### Original image x4

![Source tiled](docs/1_orion_src_2x2.jpg)

Orion galaxy by NASA/ESA, in four copies side by side. 

We cannot use the original image as an endless space background: the seams are visible.

### Converted image x4

![Converted tiled](docs/2_orion_seamless_2x2.jpg)

The result of `img2texture`, in four copies side by side. 

The image is slightly reduced in size and the edges are modified with 
alpha-blending.

The converted image can be tiled and panned in any 
direction. It will feel endless and seamless.

# Install

The easiest way is to download and extract a [binary executable](https://github.com/rtmigo/img2texture/releases):

* [for macOS](https://github.com/rtmigo/img2texture/releases/latest/download/img2texture_darwin_amd64.tgz)
* [for Linux](https://github.com/rtmigo/img2texture/releases/latest/download/img2texture_linux_amd64.tgz)
* [for Windows](https://github.com/rtmigo/img2texture/releases/latest/download/img2texture_windows_amd64.zip)

Or install as a Python package:

```bash
pip3 install img2texture
```

# Run

Create new `seamless.jpg` from `source.jpg`.
```bash
img2texture /path/to/source.jpg /path/to/seamless.jpg 
```

## --overlap

The `--overlap` option determines how much of the image will be used to hide the seams.

For example, the following command uses 25% of the width and 25% of the height 
of the original image:

```bash
img2texture source.jpg seamless.jpg --overlap 0.25 
```

Increasing the value makes the seam less visible. However, the image becomes smaller.

<details>
  <summary>Sample images</summary>

*⚠️ If the images below are not displayed, check out the 
[original of this document on GitHub](https://github.com/rtmigo/img2texture#readme).*

# Direct Usage

```python
from PIL import Image
from img2texture import img2tex
from img2texture._tiling import tile

image = Image.open('/content/input_.png')

texture = img2tex(iamge, target=None, pct=0.5)

tiled_texture = tile(texture, tile_filename(source), horizontal=2, vertical=2)
```


### --overlap 0.05

5% of the width and 5% of the height are used to mask the seam.

![--overlap 0.05](docs/3_orion_05_2x2.jpg)



### --overlap 0.4

40% of the width and 40% of the height are used to mask the seam.

![--overlap 40](docs/3_orion_40_2x2.jpg)

</details>

## --tile

The `--tile` option will create a 2x2 tiled version in addition to the converted image.

The following command will create `seamless.jpg` and `seamless_2x2.jpg`. 

```bash
img2texture source.jpg seamless.jpg --tile 
```

All the samples on this page were created with `--tile`.

# License

Copyright © 2021 [Artsiom iG](https://github.com/rtmigo).
Released under the [MIT License](LICENSE).
