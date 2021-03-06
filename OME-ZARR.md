# Description

This plugin provides a reader for zarr backed OME-NGFF images in napari. The reader
will inspect the `.zattrs` metadata provided and pass any relevant metadata, including channel, scale and colormap metadata. 

<!-- <iframe width="560" height="315" 
    src="https://www.youtube.com/embed/xtzV8Yf0a0U" 
    title="YouTube video player" 
    frameborder="0" 
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
    allowfullscreen>
</iframe> -->

<video width="560" height="315" autoplay loop muted playsinline>
  <source src="https://github.com/DragaDoncila/napari-hub-exemplars/blob/master/ome-zarr-example.mp4?raw=true" 
        type="video/mp4">
  Your browser does not support the video tag.
</video>
The example above uses the image at http://idr.openmicroscopy.org/webclient/?show=image-6001240

# Who is This For?

This plugin is designed to allow bioimaging researchers and analysts to explore their
multi-resolution images stored in Zarr filesets (according to the [OME zarr spec](https://ngff.openmicroscopy.org/latest/))
without needing an intricate understanding of zarr, or the spec itself.

This plugin supports reading all images recognised as ome-zarr, namely, containing
well-formed `.zattrs` and `.zgroup` files, as well as the appropriate directory 
hierarchy as described in the [spec](https://ngff.openmicroscopy.org/latest/). 
The image metadata from OMERO will be used to set channel names, colormaps and rendering settings in napari.

# Usage

You can open local or remote images using `napari` at the terminal and the path to your file:

```
$ napari 'https://s3.embassy.ebi.ac.uk/idr/zarr/v0.1/6001240.zarr/'

# also works with local files
$ napari 6001240.zarr
```

OR in python:

```python
import napari

viewer = napari.Viewer()
viewer.open('https://s3.embassy.ebi.ac.uk/idr/zarr/v0.1/6001240.zarr/')
napari.run()
```
If a single zarray is passed to the plugin, it will be opened without the use of
the metadata:

```
$ napari '/tmp/6001240.zarr/0'
```

If an image group contains labels, they will also be opened, and added as a 
separate layer in napari.

When the labels group metadata additionally contains `"rgba"` and `"properties"` keys, 
the labels will be given appropriate colors and the properties will be displayed 
in the status bar.

For more detail on command-line usage of `ome-zarr` and its utility functions, please see our [package documentation](https://pypi.org/project/ome-zarr/).

# Getting Help

If you discover a bug with the plugin, or would like to request a new feature, please
raise an issue on our repository at https://github.com/ome/ome-zarr-py.

If you would like assistance with using the plugin, or converting images to
ome-zarr format, please reach out on [image.sc](https://forum.image.sc/).

# How to Cite

## To cite OME-NGFF:

[Next-generation file format (NGFF) specifications for storing bioimaging data in the cloud](https://ngff.openmicroscopy.org/0.1/). J. Moore, et al. Editors. Open Microscopy Environment Consortium, 20 November 2020. This edition of the specification is https://ngff.openmicroscopy.org/0.1/. The latest edition is available at https://ngff.openmicroscopy.org/latest/. ([doi:10.5281/zenodo.4282107](https://doi.org/10.5281/zenodo.4282107))

## To cite this plugin:

[ome-zarr-py: Experimental implementation of next-generation file format (NGFF) specifications for storing bioimaging data in the cloud.](https://doi.org/10.5281/zenodo.4113931) OME; et al. 06 October 2020. URL: https://doi.org/10.5281/zenodo.4113931