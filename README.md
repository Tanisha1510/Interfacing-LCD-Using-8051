# Interfacing-LCD-Using-8051

## Aim:
To interface a 16x2 LCD with an 8051 microcontroller and display your name.

## Apparatus Required:
•	Laptop with Keil uVision software</br>
•	Proteus Design Suite</br>

## Algorithm:
1.Configure LCD in 4-bit mode.</br>
2.Initialize LCD with commands.</br>
3.Move the cursor direction.</br>
4.Display ON</br>
5.Set cursor position to the beginning (optional).</br>
6.Send each character of the string "NAME" to the LCD one by one using data mode.</br>
7.Continuously run the program to keep displaying the message.</br>

## Program :
```
#include <reg51.h>

sbit rs = P1^0;
sbit rw = P1^1;
sbit en = P1^2;

void lcdcmd(unsigned char);
void lcddat(unsigned char);
void delay();

void main()
{
    P2 = 0x00;

    while(1)
    {
        lcdcmd(0x38);   // 5x7 matrix, 2 line
        delay();

        lcdcmd(0x01);   // clear display
        delay();

        lcdcmd(0x10);   // cursor move
        delay();

        lcdcmd(0x0C);   // display ON, cursor OFF
        delay();

        lcdcmd(0x81);   // first line, first position
        delay();

        lcddat('T');
        delay();

        lcddat('A');
        delay();

        lcddat('N');
        delay();

        lcddat('I');
        delay();

        lcddat('S');
        delay();

        lcddat('H');
        delay();

        lcddat('A');
        delay();
    }
}

void lcdcmd(unsigned char val)
{
    P2 = val;
    rs = 0;
    rw = 0;
    en = 1;
    delay();
    en = 0;
}

void lcddat(unsigned char val)
{
    P2 = val;
    rs = 1;
    rw = 0;
    en = 1;
    delay();
    en = 0;
}

void delay()
{
    unsigned int i;
    for(i = 0; i < 12000; i++);
}
```
<img width="1920" height="1200" alt="Screenshot 2026-03-18 231527" src="https://github.com/user-attachments/assets/0c8c8e4e-4574-4aea-bbcb-9a0ab2df6a08" />

## Output :
<img width="1920" height="1200" alt="Screenshot 2026-03-18 231519" src="https://github.com/user-attachments/assets/a2048451-dc65-4a9a-8f4a-004cf71699d9" />



## Result :  
Thus interfacing LCD using 8051 microcontroller is executed successfully.

