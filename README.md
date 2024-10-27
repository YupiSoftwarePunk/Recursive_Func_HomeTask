#include <iostream>
#include <cstdlib>
#include <Windows.h>

// exercise 1
void RecursePrintArr(int arr[], int size, int countIndex, int sum, int counter, int minSum, int firstNum, int currentIndex);


// exercise 2
void Func(int size, int arr[], int maxValue);
void Func(int str, int col, int arr[][5], int maxValue);
void Func(int str, int col, int wdth, int arr[][3][3], int maxValue);
void Func(int num1, int num2);
void Func(int num1, int num2, int num3);


void main()
{
	SetConsoleOutputCP(1251);
	SetConsoleCP(1251);
	srand(time(NULL));

	// exercise 1
	const int size = 100;
	int arr[size];
	int countIndex = 0, sum = 0;
	int counter = 0, minSum = INT_MAX;
	int firstNum = 0, firstNum1 = 0;
	int currentIndex = 0;


	RecursePrintArr(arr, size, countIndex, sum, counter, minSum, firstNum, currentIndex);


	std::cout << "\n\n\n\n\n";

	// exercise 2
	const int size2 = 10;
	int arr2[size2];

	const int col = 5;
	const int str = 5;
	int arr3[str][col];

	const int col2 = 3;
	const int str2 = 3;
	const int wdth = 3;
	int arr4[str2][col2][wdth];

	int maxValue = INT_MIN;

	Func( size2,  arr2,  maxValue);

	std::cout << "\n\n\n";

	Func(str, col, arr3, maxValue);

	std::cout << "\n\n\n";

	Func(str2, col2, wdth, arr4, maxValue);

	std::cout << "\n\n\n";

	Func(-1, 100);

	std::cout << "\n\n\n";

	Func(100000, 99, -100);
}


// exercise 1
void RecursePrintArr(int arr[], int size, int countIndex, int sum, int counter, int minSum, int firstNum, int currentIndex)
{
	if (currentIndex >= size) 
	{
		std::cout << "\nМинимальная сумма строки = " << minSum << " Начинается с " << firstNum << "\n";
		return;
	}
	arr[currentIndex] = rand() % 100;
	std::cout << arr[currentIndex] << "\t";
	countIndex++;
	sum += arr[currentIndex];

	if (countIndex == 10)
	{
		counter++;
		std::cout << "Сумма " << counter << " десятки чисел = " << sum << "\n";

		if (sum < minSum)
		{
			minSum = sum;
			firstNum = arr[currentIndex - 9];
		}

		countIndex = 0;
		sum = 0;
	}
	RecursePrintArr(arr, size, countIndex, sum, counter, minSum, firstNum, currentIndex + 1);
}



// exercise 2
void Func(int size, int arr[], int maxValue)
{
	for (int i = 0; i < size; i++)
	{
		arr[i] = rand() % 100;
		std::cout << arr[i] << "\t";
		if (arr[i]> maxValue)
		{
			maxValue = arr[i];
		}
	}
	std::cout << "\nМаксимальное значение = " << maxValue << "\n";
}

void Func(int str, int col, int arr[][5], int maxValue)
{
	for (int i = 0; i < str; i++)
	{
		for (int j = 0; j < col; j++)
		{
			arr[i][j] = rand() % 100;
			std::cout << arr[i][j] << "\t";
			if (arr[i][j] > maxValue)
			{
				maxValue = arr[i][j];
			}
		}
		std::cout << "\n";
	}
	std::cout<<"\nМаксимальное значение = " << maxValue << "\n"; 
}

void Func(int str, int col, int wdth, int arr[][3][3], int maxValue)
{
	for (int i = 0; i < str; i++)
	{
		for (int j = 0; j < col; j++)
		{
			for (int l = 0; l < wdth; l++)
			{
				arr[i][j][l] = rand() % 100;
				std::cout << arr[i][j][l]<< "\t";
				if (arr[i][j][l] > maxValue)
				{
					maxValue = arr[i][j][l];
				}
			}
			std::cout << "\n";
		}
		std::cout<<"\n";
	}
	std::cout << "\nМаксимальное значение = " << maxValue << "\n";
}

void Func(int num1, int num2)
{
	if (num1 > num2)
	{
		std::cout << "Максимальное значение = " << num1;
	}
	else
	{
		std::cout << "Максимальное значение = " << num2;
	}
}

void Func(int num1, int num2, int num3)
{
	if (num1 > num2 && num1 > num3)
	{
		std::cout << "Максимальное значение = " << num1;
	}
	else if (num2 > num1 && num2 > num3)
	{
		std::cout << "Максимальное значение = " << num2;
	}
	else
	{
		std::cout << "Максимальное значение = " << num3;
	}
}
