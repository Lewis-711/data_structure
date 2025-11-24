# data_structure

#include<iostream>
#include<time.h>
#include<math.h>
#define MAX 1000
using namespace std;

clock_t start, stop;

double duration;

double f1(int n, double a[], double x) {
	double p = a[0];
	for (int i = 0; i < n; i++) {
		p += a[i] * pow(x, i);
	}
	return p;
}

double f2(int n, double a[], double x) {
	double p = a[n];
	for (int i = n; i > 0; i--) {
		p = a[i - 1] + x * p;
	}
	return p;
}


int main() {
	double a[MAX];
	for (int i = 0; i < MAX; i++) {
		a[i] = (double)i;
	}

	start = clock();
	for (int i = 0; i < MAX; i++) {
		f1(MAX - 1, a, 1.1);
	}
	stop = clock();
	duration = ((double)(stop - start)) / CLK_TCK / MAX;
	printf("ticks = %f\n", (double)(stop - start));
	printf("duration1 = %6.2e\n", duration);

	start = clock();
	for (int i = 0; i < MAX; i++) {
		f2(MAX - 1, a, 1.1);
	}
	stop = clock();
	duration = ((double)(stop - start)) / CLK_TCK / MAX;
	printf("ticks = %f\n", (double)(stop - start));
	printf("duration2 = %6.2e\n", duration);

}
