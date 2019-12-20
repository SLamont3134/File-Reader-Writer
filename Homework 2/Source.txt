#include <stdio.h>
#include <stdlib.h>

int main(void)
{
	FILE* fpin;
	FILE* fpout;
	int n, m;
	double Counter;
	char SpicyMeatball[128], InputFileName[80], OutputFileName[80];
	Counter = 1;


	printf("Please Enter the name of the file you wish to read: ");
	scanf("%s", &InputFileName);
	printf("The input file name has been set to %s. \n", InputFileName);
	n = fopen_s(&fpin, InputFileName, "r");

	if (n != 0)
	{
		perror("Can't Open the Input File!");
		exit(1);
	}
	if (fpin == NULL)
	{
		perror("Can't Open the Input File!");
		exit(1);
	}

	printf("Please Enter the name of the output file including .txt: ");
	scanf("%s", &OutputFileName);
	printf("The output file name has been set to %s \n", OutputFileName);
	m = fopen_s(&fpout, OutputFileName, "w");

	if (m != 0)
	{
		perror("Can't Open the Output File!");
		exit(1);
	}
	if (fpout == NULL)
	{
		perror("Can't Use That Output File!");
		exit(1);
	}

	while (fgets(SpicyMeatball, sizeof(SpicyMeatball), fpin) != NULL)
	{
		fprintf(fpout, "%.0f: %s \n", Counter, SpicyMeatball);
		//printf("%s \n", SpicyMeatball);
		Counter++;
	}

	printf("\nFile Created Successfully!");

	fclose(fpin);
	fclose(fpout);
}