Lossless extension to IJG libjpeg-v6b
-------------------------------------

This patch adds lossless JPEG support (per the original spec -- not JPEG-LS)
to IJG libjpeg-v6b.  The code has been tested on IRIX 6.x and Solaris 2.x
using the JPEG reference data and compliance images and has been verified at
the pixel level.  This extension can be obtained by downloading one of the
following three files:

ljpeg-patch.v6b.tar.gz	- patches to jpegsrc.v6b source files
ljpegsrc.v6b.tar.gz	- full ljpeg source as a gzipped tar archive
ljpegsrc.v6b.zip	- full ljpeg source as a zip archive


Notes on compiling and use:
* The lossless support is a compile time option which can be set in
  jmorecfg.h (the patch turns it on by default).
* I have only modified makefile.cfg, so if you're not using a UNIX box
  or configure, then you'll have to modify the appropriate makefile.
* There are no changes to the existing API, so that no application code
  needs to be changed (only a recompile).
* The only addition to the API is jpeg_simple_lossless() for creating
  lossless images (see libjpeg.doc).
* A -lossless option has been added to cjpeg(1) for creating lossless
  images (see man page for use).
* You can use a 8-bit library to decompress a 12-bit lossless image (unlike
  the lossy implementation), with the output scaled down to 8 bits.  If
  you do not want this behavior, compile a 12-bit version of the library!
* Read structure.doc for the internal changes to the library.

Other stuff:
* No warranties are expressed or implied, use this code at your own
  risk.  If you misdiagnose a medical image as a result of using this code,
  I am NOT responsible in any way.
* Although I did all of the coding on this project, it would not have
  been possible without all of the help that I received from Tom Lane. 
  Thanks Tom!
* The documentation for the lossless stuff is by no means complete.  I
  have taken a quick whack at the big stuff, but the best documentation is
  the source itself.
* Because of the extra level of indirection added to the internal
  structure, performance of the lossy codec may suffer slightly.  I would
  be interested in any feedback on this subject.

Please direct all comments/questions/suggestions/bug reports/patches to
me (ken@oceana.com).  Do NOT bother Tom Lane with this stuff -- he is not
responsible for this code (at least not yet ;-).

Regards,
Ken Murchison