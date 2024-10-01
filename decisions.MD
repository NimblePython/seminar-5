# Решение задач с сырыми указателями

## Задача 1. Вспоминаем сырые указатели

```cpp
#include <iostream>

// Функция, увеличивающая значение через указатель
void incrementPointer(int* ptr, int increment) {
    *ptr += increment;
}

// Функция, увеличивающая значение через ссылку
void incrementReference(int& ref, int increment) {
    ref += increment;
}

int main() {
    // 1. Динамическое выделение памяти для переменной int
    int* ptr1 = new int(10); // Указатель ptr1 указывает на область памяти, хранящую значение 10
    std::cout << "Initial value through ptr1: " << *ptr1 << std::endl;

    // 2. Создание второго указателя, указывающего на ту же область памяти
    int* ptr2 = ptr1;
    std::cout << "Разыменовать ptr2 (то же, что и ptr1): " << *ptr2 << std::endl;

    // 3. Указатель на указатель
    int** ptr3 = &ptr1;

    // 4. Изменение значения через указатель на указатель
    **ptr3 = 20;
    std::cout << "Разыменовать ptr1 после изменения ptr3: " << *ptr1 << std::endl;
    std::cout << "Разыменовать ptr2 после изменения ptr3: " << *ptr2 << std::endl;

    // Используем функцию с указателями
    incrementPointer(ptr1, 5);
    std::cout << "Value after incrementPointer: " << *ptr1 << std::endl;

    // Используем функцию со ссылками
    incrementReference(*ptr2, 10);  // *ptr2 это переменная int, передаем ее по ссылке
    std::cout << "Value after incrementReference: " << *ptr1 << std::endl;

    // 5. Освобождение памяти
    delete ptr1;

    return 0;
}
```

## Задача 2. Создание двумерного массива через указатели

```cpp
#include <iostream>

// Функция для создания двумерного массива
int** createMatrix(int rows, int cols) {
    int** matrix = new int*[rows]; // Выделяем память под строки
    for (int i = 0; i < rows; ++i) {
        matrix[i] = new int[cols]; // Выделяем память под каждый столбец
    }
    return matrix;
}

// Функция для ввода значений матрицы
void inputMatrix(int** matrix, int rows, int cols) {
    std::cout << "Введите элементы матрицы (" << rows << "x" << cols << "):" << std::endl;
    for (int i = 0; i < rows; ++i) {
        for (int j = 0; j < cols; ++j) {
            std::cout << "Элемент [" << i << "][" << j << "]: ";
            std::cin >> matrix[i][j];
        }
    }
}

// Функция для вывода значений матрицы
void outputMatrix(int** matrix, int rows, int cols) {
    std::cout << "Матрица (" << rows << "x" << cols << "):" << std::endl;
    for (int i = 0; i < rows; ++i) {
        for (int j = 0; j < cols; ++j) {
            std::cout << matrix[i][j] << " ";
        }
        std::cout << std::endl;
    }
}

// Функция для освобождения памяти
void deleteMatrix(int** matrix, int rows) {
    for (int i = 0; i < rows; ++i) {
        delete[] matrix[i]; // Освобождаем память для каждой строки
    }
    delete[] matrix; // Освобождаем память для массива указателей на строки
}

int main() {
    int rows, cols;

    // Ввод количества строк и столбцов
    std::cout << "Введите количество строк: ";
    std::cin >> rows;
    std::cout << "Введите количество столбцов: ";
    std::cin >> cols;

    // Создание матрицы
    int** matrix = createMatrix(rows, cols);

    // Ввод значений матрицы
    inputMatrix(matrix, rows, cols);

    // Вывод значений матрицы
    outputMatrix(matrix, rows, cols);

    // Освобождение памяти
    deleteMatrix(matrix, rows);

    return 0;
}
```
