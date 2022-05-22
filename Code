#include <iostream>
#include <stdlib.h>

void takeInputs(double numCoeff[], double denomCoeff[], int* numPower, int* denomPower)
{
    int i;
    printf("enter the degree of the numerator: ");
    scanf_s("%d", numPower); 

    for (i = 0; i < *numPower; i++)
    {
        if (*numPower - i == 1)
        {
            printf("Enter the coefficient of X : ");
            scanf_s("%lf", &numCoeff[i]);
        }
        else
        {
            printf("Enter the coefficient of X^%d : ", *numPower - i);
            scanf_s("%lf", &numCoeff[i]);
        }
    }
    printf("Enter the constant term : ");
    scanf_s("%lf", &numCoeff[i]);
    printf("enter the degree of the denominator: ");
    scanf_s("%d", denomPower); 

    for (i = 0; i < *denomPower; i++)
    {
        if (*denomPower - i == 1)
        {
            printf("Enter the coefficient of X : ");
            scanf_s("%lf", &denomCoeff[i]);
        }
        else
        {
            printf("Enter the coefficient of X^%d : ", *denomPower - i);
            scanf_s("%lf", &denomCoeff[i]);
        }
    }
    printf("Enter the constant term : ");
    scanf_s("%lf", &denomCoeff[i]);
}

int isDivisible(int numPower, int denomPower)
{
    if (numPower >= denomPower) return 1;
    else return 0;
}

int divide(int numPower, double numCoeff[], int denomPower, double denomCoeff[], double outCoeff[])
{
    int outPower, i, j;
    double subtractCoeff[50]; 
    outPower = numPower - denomPower; 

    for (i = 0; i < numPower; i++)
    {
        if (isDivisible(numPower - i, denomPower))
        {
            outCoeff[i] = numCoeff[i] / denomCoeff[0]; 
            for (j = 0; j <= denomPower; j++)
            {
                subtractCoeff[j] = outCoeff[i] * denomCoeff[j]; 
            }
            for (j = 0; j <= denomPower; j++)
            {
                numCoeff[j + i] = numCoeff[j + i] - subtractCoeff[j]; 
            }
        }
        else
            break;
    }
    return outPower; 
}

void PrintPoly(int outPower, double outCoeff[])
{
    
    int i;
    char sign;  
    
    printf("The output is : ");
    for (i = 0; i < outPower; i++) 
    {
        if (outCoeff[i] < 0) 
        {
            outCoeff[i] = -outCoeff[i]; 
            sign = -1; 
        }
        else if (outCoeff[i] > 0) 
            sign = 1; 
        else
            continue; 

        if (outCoeff[i] == 1) 
        {
            if (outPower - i == 1) 
            {
                if (i == 0)
                    printf("X "); 
                else
                    printf("+ X "); 
            }
            else 
            {
                if (i == 0)
                    printf("X^%d ", outPower - i); 
                else
                    printf("+ X^%d ", outPower - i); 
            }
        } 
        else if (outCoeff[i] == -1) 
        {
            if (outPower - i == 1)
            {
                printf("- X ");
            }
            else
            {
                printf("- X^%d ", outPower - i);
            }
        }
        else
        {
            if (outPower - i == 1) 
            {
                if (i == 0) 
                    printf("%0.2lfX ", sign * outCoeff[i]); 
                else if (sign == 1) 
                    printf("+ %0.2lfX ", outCoeff[i]);
                else if (sign == -1) 
                    printf("- %0.2lfX ", outCoeff[i]);
            }
            else 
            {
                if (i == 0) 
                    printf("%0.2lfX^%d ", sign * outCoeff[i], outPower);
                else if (sign == 1) 
                    printf("+ %0.2lfX^%d ", outCoeff[i], outPower - i); 
                else if (sign == -1) 
                    printf("- %0.2lfX^%d ", outCoeff[i], outPower - i);
            }
        }

    }
    if (!outPower) 
        printf("%0.2lf ", outCoeff[i]);
    else if (outCoeff[i] > 0) 
        printf("+ %0.2lf ", outCoeff[i]);
    else if (outCoeff[i] < 0) 
        printf("- %0.2lf ", -outCoeff[i]);
    
}

int isRemained(int numPower, double numCoeff[])
{
    int i;
    for (i = 0; i <= numPower; i++)
        if (numCoeff[i]) 
            return 1;
    return 0;
}

void PrintRemainder(int numPower, double numCoeff[], int denomPower, double denomCoeff[])
{ 
    int i;
    char sign;
    for (i = 0; i <= numPower; i++) 
    {
        if (numCoeff[i]) 
        {
            if (numCoeff[i] > 0) 
                sign = 1; 
            else 
            {
                sign = -1; 
                numCoeff[i] = -numCoeff[i];
            }

            if (i != 0 && !numCoeff[i - 1]) 
            {
                printf("+ ("); 
                if (numPower - i == 0) 
                {
                    if (sign == 1) 
                        printf(" %0.2lf ", numCoeff[i]);
                    else if (sign == -1) 
                        printf("- %0.2lf ", numCoeff[i]);
                }
                else if (numPower - i == 1) 
                {
                    if (sign == 1) 
                        printf(" %0.2lfX ", numCoeff[i]);
                    else if (sign == -1) 
                        printf("- %0.2lfX ", numCoeff[i]);
                }
                else if (numPower - i > 1) 
                {
                    if (sign == 1) 
                        printf(" %0.2lfX^%d ", numCoeff[i], numPower - i);
                    else if (sign == -1)
                        printf("- %0.2lfX^%d ", numCoeff[i], numPower - i);
                }
            }
            else if (i == 0) 
            {
                printf("("); 
                if (numPower - i == 0) 
                {
                    if (sign == 1)
                        printf(" %0.2lf ", numCoeff[i]);
                    else if (sign == -1)
                        printf("- %0.2lf ", numCoeff[i]);
                }
                else if (numPower - i == 1)
                {
                    if (sign == 1)
                        printf(" %0.2lfX ", numCoeff[i]);
                    else if (sign == -1)
                        printf("- %0.2lfX ", numCoeff[i]);
                }
                else if (numPower - i > 1)
                {
                    if (sign == 1)
                        printf(" %0.2lfX^%d ", numCoeff[i], numPower - i);
                    else if (sign == -1)
                        printf("- %0.2lfX^%d ", numCoeff[i], numPower - i);
                }
            }
            else 
            { 
                if (numPower - i == 0)
                {
                    if (sign == 1)
                        printf("+ %0.2lf ", numCoeff[i]);
                    else if (sign == -1)
                        printf("- %0.2lf ", numCoeff[i]);
                }
                else if (numPower - i == 1)
                {
                    if (sign == 1)
                        printf("+ %0.2lfX ", numCoeff[i]);
                    else if (sign == -1)
                        printf("- %0.2lfX ", numCoeff[i]);
                }
                else if (numPower - i > 1)
                {
                    if (sign == 1)
                        printf("+ %0.2lfX^%d ", numCoeff[i], numPower - i);
                    else if (sign == -1)
                        printf("- %0.2lfX^%d ", numCoeff[i], numPower - i);
                }
            }
        }
    }
    printf(") / ("); 
    for (i = 0; i < denomPower; i++) 
    {
        if (denomCoeff[i] < 0)
        {
            denomCoeff[i] = -denomCoeff[i];
            sign = -1;
        }
        else if (denomCoeff[i] > 0)
            sign = 1;
        else
            continue;

        if (denomCoeff[i] == 1)
        {
            if (denomPower - i == 1)
            {
                if (i == 0)
                    printf("X ");
                else
                    printf("+ X ");
            }
            else
            {
                if (i == 0)
                    printf("X^%d ", denomPower - i);
                else
                    printf("+ X^%d ", denomPower - i);
            }
        }
        else if (denomCoeff[i] == -1)
        {
            if (denomPower - i == 1)
            {
                printf("- X ");
            }
            else
            {
                printf("- X^%d ", denomPower - i);
            }
        }
        else
        {
            if (denomPower - i == 1)
            {
                if (i == 0)
                    printf("%0.2lfX ", sign * denomCoeff[i]);
                else if (sign == 1)
                    printf("+ %0.2lfX ", denomCoeff[i]);
                else if (sign == -1)
                    printf("- %0.2lfX ", denomCoeff[i]);
            }
            else
            {
                if (i == 0)
                    printf("%0.2lfX^%d ", sign * denomCoeff[i], denomPower);
                else if (sign == 1)
                    printf("+ %0.2lfX^%d ", denomCoeff[i], denomPower - i);
                else if (sign == -1)
                    printf("- %0.2lfX^%d ", denomCoeff[i], denomPower - i);
            }
        }

    }
    if (denomCoeff[i] > 0) 
        printf("+ %0.2lf ", denomCoeff[i]);
    else if (denomCoeff[i] < 0)
        printf("- %0.2lf ", -denomCoeff[i]);
    printf(")"); 
}

int main()
{
    double numCoeff[50];
    double denomCoeff[50];
    double outCoeff[50];
    int numPower, denomPower, outPower;
    takeInputs(numCoeff, denomCoeff, &numPower, &denomPower);
    if (isDivisible(numPower, denomPower))
    {
        outPower = divide(numPower, numCoeff, denomPower, denomCoeff, outCoeff);
        PrintPoly(outPower, outCoeff);
        if (isRemained(numPower, numCoeff))
            PrintRemainder(numPower, numCoeff, denomPower, denomCoeff);
    }
    else
        PrintRemainder(numPower, numCoeff, denomPower, denomCoeff
