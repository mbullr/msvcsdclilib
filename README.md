# winsdclilib
 Windows port of qmclilib for String Database (sd)
  
  START-HISTORY (winSDclilib):
  
  Windows port, using Visual Studio 2022
  
  This port does not include the call function, but instead the Callx / Getarg functions of newer client versions.
  
  Warning: winsdclilib does not maintain a storage area for Getarg parameters for each session. Using Callx will "overwrite" the previous Callx
   parameters regardless of session number.
  
  Notes: There seems to be an issue with char vs unsigned char when using the memchr c function (void *memchr(const void *str, int c, size_t n).
  If passing the int c parameter as a char, characters > 127 cannot be found (interpreted as a neg integer?).
  The gcc compiler & linux libraries seems to be fine with it, not so with C++ Builder / Windows. Need to use unsigned Char.
	  
  I cannot find where the transfer buffer "buff" is freed, need to test for memory leak to see if this is really the case.
  For now I have added code to disconnect() to free buff if there are no more remaining active connections.
  
  For now I have commented out #include "sddefs.h" and pulled the required information from the include file into winsdclilib.c
  There is a bunch of stuff in sddefs.h that will not resolve with Visual Studio 2022 some of the int defines, bigended stuff. Lazy on my part, yes.
  
  This port was made with Visual Studio 2022.

  To build:  

  Clone (or download zip) this repo.  
  Add err.h and revstamp.h (from sd64/gplsrc) to folder containing winsdclilib.c source.    
  Open Visual Studio 2022  
  Select Open a project or solution.  
  Locate the winsdclilib.sin file and open    
  Select Build from the menu, then Build Solution      
  
  This is a work in progress.......
