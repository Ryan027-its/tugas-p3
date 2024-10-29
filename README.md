#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Fungsi untuk penjumlahan
int add(int x, int y) {
    return x + y;
}

// Fungsi untuk pengurangan
int sub(int x, int y) {
    return x - y;
}

// Fungsi untuk perkalian
int mult(int x, int y) {
    return x * y;
}

// Fungsi untuk pembagian
float divide(int x, int y) {
    if (y == 0) {
        printf("Error: Tidak bisa membagi dengan nol.\n");
        return 0;
    }
    return (float)x / y;
}

// Fungsi untuk faktorial
int factorial(int n) {
    if (n < 0) {
        printf("Error: Faktorial hanya untuk bilangan non-negatif.\n");
        return -1;
    }
    int result = 1;
    for (int i = 1; i <= n; i++) {
        result *= i;
    }
    return result;
}

// Fungsi untuk FPB (GCD)
int gcd(int x, int y) {
    while (y != 0) {
        int temp = y;
        y = x % y;
        x = temp;
    }
    return x;
}

// Fungsi untuk KPK (LCM)
int lcm(int x, int y) {
    return abs(x * y) / gcd(x, y);
}

// Fungsi untuk pangkat (power)
int power(int base, int exp) {
    int result = 1;
    for (int i = 0; i < exp; i++) {
        result *= base;
    }
    return result;
}

// Fungsi utama kalkulator
int main() {
    char operation[10];
    int num1, num2, result;
    float result_div;

    printf("Kalkulator Sederhana\n");
    printf("Operasi yang tersedia: ADD, SUB, MULT, DIV, FACT, GCD, LCM, POW\n");
    printf("Masukkan 'KELUAR' untuk berhenti.\n");

    while (1) {
        printf("\nMasukkan operasi: ");
        scanf("%s", operation);

        if (strcmp(operation, "KELUAR") == 0) {
            printf("Kalkulator berhenti. Terima kasih!\n");
            break;
        }

        // Parsing input dan menjalankan operasi yang diinginkan
        if (strcmp(operation, "ADD") == 0) {
            scanf("%d %d", &num1, &num2);
            result = add(num1, num2);
            printf("Output: %d\n", result);
        } else if (strcmp(operation, "SUB") == 0) {
            scanf("%d %d", &num1, &num2);
            result = sub(num1, num2);
            printf("Output: %d\n", result);
        } else if (strcmp(operation, "MULT") == 0) {
            scanf("%d %d", &num1, &num2);
            result = mult(num1, num2);
            printf("Output: %d\n", result);
        } else if (strcmp(operation, "DIV") == 0) {
            scanf("%d %d", &num1, &num2);
            result_div = divide(num1, num2);
            printf("Output: %.2f\n", result_div);
        } else if (strcmp(operation, "FACT") == 0) {
            scanf("%d", &num1);
            result = factorial(num1);
            if (result != -1) {
                printf("Output: %d\n", result);
            }
        } else if (strcmp(operation, "GCD") == 0) {
            scanf("%d %d", &num1, &num2);
            result = gcd(num1, num2);
            printf("Output: %d\n", result);
        } else if (strcmp(operation, "LCM") == 0) {
            scanf("%d %d", &num1, &num2);
            result = lcm(num1, num2);
            printf("Output: %d\n", result);
        } else if (strcmp(operation, "POW") == 0) {
            scanf("%d %d", &num1, &num2);
            result = power(num1, num2);
            printf("Output: %d\n", result);
        } else {
            printf("Operasi tidak dikenali. Silakan coba lagi.\n");
        }
    }

    return 0;
}
