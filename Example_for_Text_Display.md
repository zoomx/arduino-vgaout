# Example for Text Display #
![http://arduino-vgaout.googlecode.com/svn/trunk/TextDisplay.jpg](http://arduino-vgaout.googlecode.com/svn/trunk/TextDisplay.jpg)
```

#include "SYSdef.h"
#include "CRTdef.h"
#include "INTdef.h"
#include "CSLdef.h"

/*==========================================================================*/
/*  Program                                                                 */
/*==========================================================================*/
CSYS objSYS;
CCRT objCRT;
CCSL objCSL;
CINT objINT;

void setup()
{
    objSYS.Ini();               /* re-initialize after Arduini IDE init()   */
    objCRT.ChangeMode( CRT_TEXT );
    sei();                      /* interrupt enable                         */
}

void loop()
{
    vram_data[8*0+0] = 'H';     /* line 1   */
    vram_data[8*0+1] = 'a';
    vram_data[8*0+2] = 'p';
    vram_data[8*0+3] = 'p';
    vram_data[8*0+4] = 'y';
    
    vram_data[8*1+0] = 'N';     /* line 2   */
    vram_data[8*1+1] = 'e';
    vram_data[8*1+2] = 'w';
    
    vram_data[8*2+0] = 'y';     /* line 3   */
    vram_data[8*2+1] = 'e';
    vram_data[8*2+2] = 'a';
    vram_data[8*2+3] = 'r';
    vram_data[8*2+4] = '!';
    
    LineColor[0] = COL_RED;
    LineColor[1] = COL_GRN;
    LineColor[2] = COL_BLU;
}

```