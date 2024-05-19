\#include <Arduino.h>

int led1 = 2;

int led2 = 3;

int led3 = 4;

**String** myString = ""; *//接收串口发送过来的值*

**String** short_String = ""; *//存储myString截取后的字符串*

**String** xstr = ""; *//存储led_flash(x)的字符串x*

**String** Control_LED[] = {"x", "led_flash(x)"}; *//定义字符串数组*

int x = 0;*//存储led_flash(x)的整数x*

int flag1 = 0;

int flag2 = 0;

int flag3 = 0;

void **setup**()

{

**pinMode**(led1, **OUTPUT**);

**pinMode**(led2, **OUTPUT**);

**pinMode**(led3, **OUTPUT**);

Serial.**begin**(9600);

}

void **loop**(){

if (Serial.**available**() > 0)*//如果串口有数据*

{

myString **=** Serial.**readStringUntil**('\n');*//读取字符串*

short_String **=** myString.**substring**(0, 8);*//截取输入字符串myString的前8位字符*

x = short_String.**toInt**();*//将字符串xstr转成数字x*

if (x==1 && flag1 == 0 )

{

Serial.**println**("LED1 on");

**digitalWrite**(led1, **HIGH**);

flag1 = 1;

}

else if (x==1 && flag1 ==1 )

{

Serial.**println**("LED1 off");

**digitalWrite**(led1, **LOW**);

flag1 = 0;

}

if (x==2 && flag2 == 0 )

{

Serial.**println**("LED2 on");

**digitalWrite**(led2, **HIGH**);

flag2 = 1;

}

else if (x==2 && flag2 ==1 )

{

Serial.**println**("LED2 off");

**digitalWrite**(led2, **LOW**);

flag2 = 0;

}

if (x==3 && flag3 == 0 )

{

Serial.**println**("LED3 on");

**digitalWrite**(led3, **HIGH**);

flag3 = 1;

}

else if (x==3 && flag3 ==1 )

{

Serial.**println**("LED3 off");

**digitalWrite**(led3, **LOW**);

flag3 = 0;

}

}

}