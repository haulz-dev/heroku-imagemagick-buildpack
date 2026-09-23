# haulz-imagemagick-buildpack

Heroku buildpack for ImageMagick 7.1.0-53 Q16-HDRI, compiled for **heroku-22** (Ubuntu 22.04 / gcc 11.3).

Binary sourced from a working production slug. Pinned to this version for stability.

## Usage

```bash
heroku buildpacks:add --index 1 https://github.com/haulz-dev/heroku-imagemagick-buildpack --app YOUR_APP
```

## Version

- ImageMagick 7.1.0-53 Q16-HDRI x86_64
- Stack: heroku-22
- Delegates: bzlib djvu fontconfig freetype heic jbig jng jp2 jpeg lcms lqr lzma png tiff webp xml zip zlib

## Ghostscript

Not installed here. PDF/PS/EPS decoding shells out to a bare `gs` on `PATH`, which
comes from the heroku-22 stack image (`/usr/bin/gs`, 9.55.0).

## Configuration

`MAGICK_CONFIGURE_PATH` must point at `vendor/imagemagick/etc/ImageMagick-7`, where
the tarball puts `colors.xml` and `delegates.xml`. It previously pointed at `$HOME/.magick`,
a directory nothing ever created, which logged `UnableToOpenConfigureFile` on every
invocation and fell back to compiled-in defaults.

