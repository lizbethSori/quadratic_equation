#include <math.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <strings.h>
/*In this assignment it will be similar to assignment 4 but we are
manipulate with malloc*/
// struc that is needed for the assignment along with typedef//
struct Slope {
	double m;
	double b;
	int n;
	double *x;
	double *y;
};
typedef struct Slope Slope;
/// this is going to be our construct function//
Slope *construct(
	double new_m,
	double new_b,
	int new_n,
	double new_x,
	double new_y,
	FILE *ifp,
	FILE *ofp) {
	Slope *n_slope = malloc(sizeof(Slope));
	n_slope->m = new_m;
	n_slope->b = new_b;
	n_slope->n = new_n;
	n_slope->x = &new_x;
	n_slope->y = &new_y;
	return n_slope;
}
// this is where we will take in the input file and do the output file
void fill_in(Slope *n_slope, FILE *ifp, FILE *ofp) {
	int i, j;
	fscanf(ifp, "%lf %lf\n", &n_slope->m, &n_slope->b);
	fprintf(ofp, "Slope: %0.3f\n", n_slope->m);
	fprintf(ofp, "Intercept: %0.3f\n", n_slope->b);
	fscanf(ifp, "%d\n", &n_slope->n);
	fprintf(ofp, "the n count is: %d\n", n_slope->n);
	n_slope->x = (double *)malloc(n_slope->n * sizeof(double));
	n_slope->y = (double *)malloc(n_slope->n * sizeof(double));
	for (j = 1; j < n_slope->n + 1; j++) {
		fscanf(ifp, "%lf \n", &n_slope->x[j]);
		n_slope->y[j] = n_slope->x[j] * n_slope->m + n_slope->b;
		fprintf(
			ofp,
			" x[%d]: %+lf , y[%d]:%+lf\n",j,n_slope->x[j],j,n_slope->y[j]);
	}
}
// this is our destructor
void garbage(Slope *n_slope) {
	free(n_slope);
}
// main!!
int main(void) {
	FILE *ifp, *ofp;
	ifp = fopen("as5input.txt", "r");
	ofp = fopen("as5output_RamirezSoriano_Lizbeth.txt", "w");
	Slope *n_slope = malloc(sizeof(Slope));
	fill_in(n_slope, ifp, ofp);
	fread(n_slope, sizeof(Slope), 1, ifp);
	garbage(n_slope);
	fclose(ifp);
	fclose(ofp);
}
