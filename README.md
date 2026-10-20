#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include <locale.h>
#include <math.h>
float dist();
void put_point(Point z);
float dist(Point z, Point w);

int main()
{
	setlocale(LC_CTYPE, "RUS");
	task_1();
}

struct point {
	float x;
	float y;
	char name;

};

typedef struct point Point;

void put_point(Point z)
{
	printf("point %c (%.1f, %.1f)\n", z.name, z.x, z.y);
}

float dist(Point z, Point w)
{
	float dx = w.x - z.x;
	float dy = w.y - z.y;
	return sqrt(dx * dx + dy * dy);
}

Point get_midpoint(Point z, Point w) 
{
	Point mid;
	mid.x = (z.x + w.x) / 2.0f;
	mid.y = (z.y + w.y) / 2.0f;
	mid.name = 'M';
	return mid;
}

int task_1()
{
	Point b, a;
	Point pnt1, pnt2;

	a = (Point){ 1.f, 2.f, 'A' };
	b.name = 'B'; b.x = 5; b.y = -3;

	printf("Отображение точек\n");
	put_point(a);
	put_point(b);

	printf("Расстояние между точками\n");
	float distance = dist(a, b);
	printf("Расстояние между %c и %c: %.2f\n", a.name, b.name, distance);

	printf("Вычисление середины отрезка\n");

	//Point mid = midpoint(a, b);
	//printf("Середина отрезка между точками %c и %c: \n", a.name, b.name);
	//put_point(mid);
	
	printf("Введите первую точку (например, Q 1 1): \n");
	scanf(" %c %f %f", &pnt1.name, &pnt1.x, &pnt1.y);

	printf("Введите вторую точку (например, P 2 2): \n");
	scanf(" %c %f %f", &pnt2.name, &pnt2.x, &pnt2.y);

	Point mid = get_midpoint(pnt1, pnt2);
	printf("Середина отрезка между точками %c и %c: \n", pnt1.name, pnt2.name);
	put_point(mid);
	//printf("point %c (%.1f, %.1f)", b.name, b.x, b.y);
	return 0;
}
