# Создайте двумерный массив через указатели

Создайте двумерный массив через указатели.
Ввод количества строк и столбцов, а также значений элементов массива, осуществить с клавиатуры. Создание, ввод и вывод матрицы осуществляется через функции.

## Скелет кода программы

```cpp
#include <iostream>

// Функция для создания двумерного массива должна вернуть двумерный массив
??? createMatrix(int rows, int cols) {

}

// Функция для ввода значений матрицы
void inputMatrix(?получить матрицу?, int rows, int cols) {
    std::cout << "Введите элементы матрицы (" << rows << "x" << cols << "):" << std::endl;
    ???
}

// Функция для вывода значений матрицы
void outputMatrix(?получить матрицу?, int rows, int cols) {
    std::cout << "Матрица (" << rows << "x" << cols << "):" << std::endl;
    ???
}

// Функция для освобождения памяти
void deleteMatrix(?получить матрицу?, ???) {
    ???
}

int main() {
    int rows, cols;

    // Ввод количества строк и столбцов
    std::cout << "Введите количество строк: ";
    std::cin >> rows;
    std::cout << "Введите количество столбцов: ";
    std::cin >> cols;

    // Создание матрицы
    

    // Ввод значений матрицы


    // Вывод значений матрицы
 

    // Освобождение памяти


    return 0;
}
```

### Что делает каждая функция:

1. **`createMatrix`**: Создает двумерный массив (матрицу) с заданным количеством строк и столбцов. Выделяет память динамически для каждой строки и для каждого столбца в этих строках.

2. **`inputMatrix`**: Осуществляет ввод значений в матрицу. Использует указатели для доступа к элементам двумерного массива.

3. **`outputMatrix`**: Осуществляет вывод значений матрицы на экран. Проходит по каждому элементу массива и выводит его.

4. **`deleteMatrix`**: Освобождает память, выделенную под двумерный массив, сначала для каждого столбца в строках, а затем для массива указателей на строки.

### Пример работы программы

```bs
Введите количество строк: 2
Введите количество столбцов: 3
Введите элементы матрицы (2x3):
Элемент [0][0]: 1
Элемент [0][1]: 2
Элемент [0][2]: 3
Элемент [1][0]: 4
Элемент [1][1]: 5
Элемент [1][2]: 6

Матрица (2x3):
1 2 3
4 5 6
```
