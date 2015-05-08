## Example2 for Text Display ##
<a href='http://www.youtube.com/watch?feature=player_embedded&v=pI6c_gY1jZc' target='_blank'><img src='http://img.youtube.com/vi/pI6c_gY1jZc/0.jpg' width='425' height=344 /></a>
```

/*****************************************************************************
    System Name : Simple Analog RGB 2013
    File Name   : VGA13_0216.pde
    Content     : 
    Version     : 0.0
    CPU board   : Arduino Duemilanove
    Compiler    : 
    History     :2013/02/16
*****************************************************************************/
/*----------------------------------------------------------------------------
;  Copyleft Nabe_RMC
;---------------------------------------------------------------------------*/

/*==========================================================================*/
/*  Includes                                                                */
/*==========================================================================*/
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
	Serial.begin(9600);
    objSYS.Ini();               /* re-initialize after Arduini IDE init()   */
    objCRT.ChangeMode( CRT_TEXT );
    sei();                      /* interrupt enable                         */
}

void loop()
{
	int i;
	unsigned char data;
	unsigned char ReadData;
	unsigned char ColorData[7] ={	COL_RED, COL_GRN, COL_BLU, COL_YEL,
									COL_CYA, COL_MAG, COL_WHI };
	
    objCSL.put_char( 0, 0, 'A' );   objSYS.delay66( 5 );
    objCSL.put_char( 1, 0, 'r' );   objSYS.delay66( 5 );
    objCSL.put_char( 2, 0, 'd' );   objSYS.delay66( 5 );
    objCSL.put_char( 3, 0, 'u' );   objSYS.delay66( 5 );
    objCSL.put_char( 4, 0, 'i' );   objSYS.delay66( 5 );
    objCSL.put_char( 5, 0, 'n' );   objSYS.delay66( 5 );
    objCSL.put_char( 6, 0, 'o' );   objSYS.delay66( 10 );
	
	data = 0x80;
	while( data <= 0x8B ){
		for( i = 0; i < 5; i++ ){
			objCSL.put_char( 0, 0, data );	objCSL.put_char( 1, 0, data+1 );
			objSYS.delay66( 5 );
			objCSL.put_char( 0, 0, data+2 );	objCSL.put_char( 1, 0, data+3 );
			objSYS.delay66( 5 );
			objCSL.set_line_color( 0, ColorData[i] );
		}
		data +=4;
	}
	
	objCSL.set_cursor( 0, 1 );
	objCSL.print("2013\n");			objSYS.delay66( 20 );
	objCSL.print("Nabe_RMC\n");		objSYS.delay66( 20 );
	objCSL.set_cursor( 0, 5 );
	objCSL.print("Menu\n");
	objCSL.print("1:C.Gene");
	objCSL.print("2:Key in");
	objCSL.print("!:return\n");
	objCSL.set_cursor( 5, 5 );

	while( Serial.available() <= 0 ){
	}
	ReadData = Serial.read();
	if( ReadData == '1' ){
		objCSL.clear_screen();
		objCSL.set_cursor( 0, 0 );
		while( ReadData != '~' ){
			objCSL.put_char( i );
			i++;
			objSYS.delay66( 2 );
			if( Serial.available() > 0 ){
				ReadData = Serial.read( );
			}
		}
		objCSL.clear_screen();
        }
	else if( ReadData == '2' ){
		objCSL.clear_screen();
		objCSL.set_cursor( 0, 0 );
		while( ReadData!= '!' ){
			if( Serial.available() > 0 ){
				ReadData = Serial.read( );
				objCSL.put_char( ReadData );
				Serial.print( ReadData);
			}
		}
	}
	objCSL.clear_screen();

}

```