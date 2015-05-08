## set\_line\_color(line,color) ##
Set the color of a line at(line)
## Use ##
set\_line\_color(line,col)

  * Arguments
    * unsigned char line : line number  0 - 13
    * unsigned char color : color
```
#define	COL_RED	    0x03	/* Red	   0000_0011B	*/
#define	COL_GRN	    0x0C	/* Green   0000_1100B	*/
#define	COL_BLU	    0x30	/* Blue	   0011_0000B	*/
#define	COL_YEL	    0x0F	/* Yellow  0000_1111B	*/
#define	COL_CYA	    0x3C	/* Cyan    0011_1100B	*/
#define	COL_MAG	    0x33	/* Magenta 0011_0011B	*/
#define	COL_WHI	    0x3F	/* White   0011_1111B	*/

Blue-2bit   Green-2bit  Re-2bit    2^6=64 color
bit5 bit4 | bit3 bit2 | bit1 bit0
```

![http://arduino-vgaout.googlecode.com/svn/trunk/VGA13_PinLO.jpg](http://arduino-vgaout.googlecode.com/svn/trunk/VGA13_PinLO.jpg)