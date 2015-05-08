## Example1 for Text Display ##
<a href='http://www.youtube.com/watch?feature=player_embedded&v=K0CX7m1389Q' target='_blank'><img src='http://img.youtube.com/vi/K0CX7m1389Q/0.jpg' width='425' height=344 /></a>
```
void setup()
{
    objSYS.Ini();               /* re-initialize after Arduini IDE init()   */
    objCRT.ChangeMode( CRT_TEXT );
    randomSeed(analogRead(0));
    sei();                      /* interrupt enable                         */
}

void loop()
{
    int i,j,k;
    unsigned char LineColor;

    SetColor();
    objCSL.put_char( 0, 0, 'A' );   objSYS.delay66( 5 );    /* line 1   */
    objCSL.put_char( 1, 0, 'r' );   objSYS.delay66( 5 );
    objCSL.put_char( 2, 0, 'd' );   objSYS.delay66( 5 );
    objCSL.put_char( 3, 0, 'u' );   objSYS.delay66( 5 );
    objCSL.put_char( 4, 0, 'i' );   objSYS.delay66( 5 );
    objCSL.put_char( 5, 0, 'n' );   objSYS.delay66( 5 );
    objCSL.put_char( 6, 0, 'o' );   objSYS.delay66( 20 );
    
    objCSL.put_char( 0, 1, 'V' );   objSYS.delay66( 2 );    /* line 2   */
    objCSL.put_char( 1, 1, 'G' );   objSYS.delay66( 3 );
    objCSL.put_char( 2, 1, 'A' );   objSYS.delay66( 4 );
    objCSL.put_char( 3, 1, '_' );   objSYS.delay66( 5 );
    objCSL.put_char( 4, 1, 'o' );   objSYS.delay66( 6 );
    objCSL.put_char( 5, 1, 'u' );   objSYS.delay66( 7 );
    objCSL.put_char( 6, 1, 't' );   objSYS.delay66( 8 );
    
    objCSL.put_char( 0, 2, '2' );   objSYS.delay66( 5 );      /* line 3   */
    objCSL.put_char( 1, 2, '0' );   objSYS.delay66( 5 );
    objCSL.put_char( 2, 2, '1' );   objSYS.delay66( 5 );
    objCSL.put_char( 3, 2, '3' );   objSYS.delay66( 10 );
    
    objCSL.put_char( 0, 3, 'N' );      /* line 4   */
    objCSL.put_char( 1, 3, 'a' );
    objCSL.put_char( 2, 3, 'b' );
    objCSL.put_char( 3, 3, 'e' );
    objCSL.put_char( 4, 3, '_' );
    objCSL.put_char( 5, 3, 'R' );
    objCSL.put_char( 6, 3, 'M' );
    objCSL.put_char( 7, 3, 'C' );   objSYS.delay66( 10 );
    
    objCSL.put_char( 0, 13, 0x0E );
    objCSL.put_char( 1, 13, 0x0F );objSYS.delay66( 5 );
    objCSL.put_char( 3, 13, 0x10 );
    objCSL.put_char( 4, 13, 0x11 );objSYS.delay66( 5 ); 
    objCSL.put_char( 6, 13, 0x0E );
    objCSL.put_char( 7, 13, 0x0F );objSYS.delay66( 5 );
    
    while(1){
        for( i = 0; i < 10; i++ ){
            SetRndPosition();
            
            for( k = 0; k<14; k++ ){
                objCSL.set_line_color( k, (unsigned char)random(0, 63) );
            }
            
            for( i = 4*COL_MAX; i < (13*COL_MAX-1); i++ ){
                vram_data[i] = 0x20;
            }
            
            for( j = 0; j <4; j++ ){
                objCSL.put_char( x_typH, y_typH, 0x12 );
                objCSL.put_char( x_typH+1, y_typH, 0x13 );
                objCSL.put_char( x_typA, y_typA, 0x00 );
                objCSL.put_char( x_typA+1, y_typA, 0x01 );
                objCSL.put_char( x_typB, y_typB, 0x04 );
                objCSL.put_char( x_typB+1, y_typB, 0x05 );
                objCSL.put_char( x_typC, y_typC, 0x08 );
                objCSL.put_char( x_typC+1, y_typC, 0x09 );
                objSYS.delay66( 2 );
                
                objCSL.put_char( x_typH, y_typH, 0x12 );
                objCSL.put_char( x_typH+1, y_typH, 0x13 );
                objCSL.put_char( x_typA, y_typA, 0x02 );
                objCSL.put_char( x_typA+1, y_typA, 0x03 );
                objCSL.put_char( x_typB, y_typB, 0x06 );
                objCSL.put_char( x_typB+1, y_typB, 0x07 );
                objCSL.put_char( x_typC, y_typC, 0x0A );
                objCSL.put_char( x_typC+1, y_typC, 0x0B );  
                objSYS.delay66( 5 );
            }
        }
    }

}

void SetColor(void)
{
    objCSL.set_line_color( 0, COL_RED );
    objCSL.set_line_color( 1, COL_GRN );
    objCSL.set_line_color( 2, COL_BLU );
    objCSL.set_line_color( 3, COL_YEL );
    objCSL.set_line_color( 4, COL_MAG );
    objCSL.set_line_color( 5, COL_CYA );
    objCSL.set_line_color( 6, COL_WHI );
    objCSL.set_line_color( 7, 0x2B );     /*  0010_1011B  */
    objCSL.set_line_color( 8, 0x2E );     /*  0010_1110B  */
    objCSL.set_line_color( 9, 0x3A );     /*  0011_1010B  */
    objCSL.set_line_color( 10, 0x2F );    /*  0010_1111B  */
    objCSL.set_line_color( 11, 0x3E );    /*  0011_1110B  */
    objCSL.set_line_color( 12, 0x3B );    /*  0011_1011B  */
    objCSL.set_line_color( 13, 0x2E );    /*  0010_1111B  */
}

void SetRndPosition(void)
{
    x_typH = (unsigned char)random( 0, 6 );
    y_typH = (unsigned char)random( 4, 12 );
    x_typA = (unsigned char)random( 0, 6 );
    y_typA = (unsigned char)random( 4, 12 );
    x_typB = (unsigned char)random( 0, 6 );
    y_typB = (unsigned char)random( 4, 12 );
    x_typC = (unsigned char)random( 0, 6 );
    y_typC = (unsigned char)random( 4, 12 );
}


```