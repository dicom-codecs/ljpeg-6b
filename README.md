# ljpeg-6b

Lossless extension to IJG libjpeg-v6b done by Ken Murchison.  
This repo was created from Ken's original code from https://sourceforge.net/projects/jpeg/files/ftp.oceana.com/

## Building

> ./configure
> make

## Modifications
* Added missing function declarations needed to make it compile with modern 
  compilers that are strict about this
* Modified jmorecfg.h so it only defined BITS_IN_JSAMPLE if it wasn't already
  defined allow it to be set externally

## Notes:
* The JPEG Lossless standard supports both huffman and arithmetic encoding.  
  This library (and most others) do not support arithmetic encoding due to
  patent issues.
* This code should work for 8 and 12 bit jpeg lossless as well since it is
  based on IJGv6b.  Unfortunately you need separate builds for each 
  (8 bit lossy, 12 bit lossy, 16 bit lossless) since the library isn't designed
  to handle more than one.  If you need to support more than one in the same
  code module (e.g. static linking or dll), you need to modify the symbols
  to avoid conflicts.  You can find the list of symbols in jpeglib.h 
