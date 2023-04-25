<h2>Практическая работа №3 Отображение информации в системах с МК-51</h2>
Цель работы: изучение принципов подключения LCD дисплея к МК для визуализации информации.

Задание по варианту:
![изображение](https://user-images.githubusercontent.com/86686038/234237417-b7a5b4ac-0cc0-452a-9261-a89647627769.png)

Исходная схема:
![изображение](https://user-images.githubusercontent.com/86686038/234237546-1407db4d-c819-446d-b3d7-5f8f1e6ba79c.png)

Код добавлен ниже:
<pre>

#include <8051.h>
void main()
{
	unsigned int i, cnt = 0, a= 0, count = 0;
	unsigned char *str="        Hello!";
	//unsigned char *str2="People!        ";
	unsigned short *str2 = "#224/, #232/, #224/, #220/";
	P0 = 0x38;
	P2 = 0x1;
	P2 = 0x0;
	P0 = 0x80;
	P2 = 0x1;
	P2 = 0x0;
		for(i=0;i<14;i++) 
		{
			P0 = str[i];
			P2 = 0x3;
			P2 = 0x2;
		}
	P0 = 0xC0;
	P2 = 0x1;
	P2 = 0x0;
	i = 15;
	while(1)
	{
		while (cnt<i)
			{
				P0 = str2[cnt];
				P2 = 0x3;
				P2 = 0x2;
				cnt++;
			}
				cnt = i - count;
		while (cnt<15)
		{
			if(a<count)
				{
					a++;
					P0 = str2[a-1];
					P2 = 0x3;
					P2 = 0x2;
					cnt++;
				}
		}
		a=0;
		P0 = 0xC0;
		P2 = 0x1;
		P2 = 0x0;
		count++;
		cnt = count;
	}
}
</pre>
