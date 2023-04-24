<h2>Практическая работа №2 Отображение информации на семисегментных индикаторах</h2>
Цель: Изучить принцип работы и подключения семисегментного индикатора

Устройство состоит из семи светодиодов размещенных таким образом, чтобы, зажигая их в разных сочетаниях, можно было бы отобразить любую десятичную арабскую цифру от 0 до 9.

Задание по варианту (4 вариант):
![изображение](https://user-images.githubusercontent.com/86686038/233961404-f30316a4-e6bd-4ed7-b55e-894d661cd3a4.png)


Схема подключения семисегментного индикатора с общим анодом к МК приведена на рисунке ниже:
![изображение](https://user-images.githubusercontent.com/86686038/233962248-e3a70b8b-98eb-414d-8b1f-88509ddb9e72.png)


Код программы приведен нижe:
<pre>
#include <8051.h>

void main()
{
	unsigned char i,j; 
	unsigned char massiv [11] = {0x00, 0x06, 0x5b, 0x4f, 0x66, 0x6d, 0x7d, 0x07, 0x7f, 0x6f, 0xFF};

	P1 = massiv [10]; 
	i = 0;
	while(1){

		if(P30 == 1 && i <= 10){
		if(i == 10){i = 0;}
		if (i==0) P2 = massiv[3];
		else if (i==1) P2 = massiv[7];
		else if (i==2) P2 = massiv[9];
		else if (i==3) P2 = massiv[1];
		else if (i==4) P2 = massiv[6];
		else if (i==5) P2 = massiv[2];
		else if (i==6) P2 = massiv[8];
		else if (i==7) P2 = massiv[4];
		else if (i==8) P2 = massiv[5];
		i++;  
		}
	}  
	P2 = massiv[10]; 
}
</pre>
