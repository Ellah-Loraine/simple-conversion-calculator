#include <stdio.h>
#include <stdlib.h>
#include <string.h>


// BINARY TO DECIMAL
int binaryToDecimal(char *binary) {
    int decimal = 0;
    int base = 1;
    int len = strlen(binary);
    for (int i = len - 1; i >= 0; i--) {
        if (binary[i] == '1') {
            decimal += base;
        }
        base *= 2;
    }
    return decimal;
}
// OCTAL TO DECIMAL
int octalToDecimal(char *octal) {
    int decimal = 0;
    int base = 1;
    int len = strlen(octal);
    for (int i = len - 1; i >= 0; i--) {
        decimal += (octal[i] - '0') * base;
        base *= 8;
    }
    return decimal;
}
// HEXADECIMAL TO DECIMAL
int hexadecimalToDecimal(char *hexadecimal) {
    int decimal = 0;
    int base = 1;
    int len = strlen(hexadecimal);
    for (int i = len - 1; i >= 0; i--) {
        if (hexadecimal[i] >= '0' && hexadecimal[i] <= '9') {
            decimal += (hexadecimal[i] - '0') * base;
        } else if (hexadecimal[i] >= 'A' && hexadecimal[i] <= 'F') {
            decimal += (hexadecimal[i] - 'A' + 10) * base;
        } else if (hexadecimal[i] >= 'a' && hexadecimal[i] <= 'f') {
            decimal += (hexadecimal[i] - 'a' + 10) * base;
        }
        base *= 16;
    }
    return decimal;
}
// DECIMAL TO BINARY
void decimalToBinary(int decimal) {
    int binary[32];
    int i = 0;
    while (decimal > 0) {
        binary[i] = decimal % 2;
        decimal /= 2;
        i++;
    }
    for (int j = i - 1; j >= 0; j--) {
        printf("%d", binary[j]);
    }
}
// DECIMAL TO OCTAL
void decimalToOctal(int decimal) {
    int octal[32];
    int i = 0;
    while (decimal > 0) {
        octal[i] = decimal % 8;
        decimal /= 8;
        i++;
    }
    for (int j = i - 1; j >= 0; j--) {
        printf("%d", octal[j]);
    }
}
// DECIMAL TO HEXADECIMAL
void decimalToHexadecimal(int decimal) {
    char hexadecimal[32];
    int i = 0;
    while (decimal > 0) {
        int remainder = decimal % 16;
        if (remainder < 10) {
            hexadecimal[i] = remainder + '0';
        } else {
            hexadecimal[i] = remainder - 10 + 'A';
        }
        decimal /= 16;
        i++;
    }
    for (int j = i - 1; j >= 0; j--) {
        printf("%c", hexadecimal[j]);
    }
}
int main() {
    int choice;
    printf("Number System Conversion Calculator\n");
    printf("\nChoose what you want to convert:");
    printf("\n1. Binary\n");
    printf("2. Octal\n");
    printf("3. Decimal\n");
    printf("4. Hexadecimal\n");
    printf("\nEnter your choice: ");
    scanf("%d", &choice);
    char input[32];
    int decimal;
    switch (choice) {
        case 1:
            printf("\nEnter binary number: ");
            scanf("%s", input);
            decimal = binaryToDecimal(input);
            printf("Decimal: %d\n", decimal);
            printf("Octal: ");
            decimalToOctal(decimal);
            printf("\nHexadecimal: ");
            decimalToHexadecimal(decimal);
            printf("\n");
            break;
        case 2:
            printf("\nEnter octal number: ");
            scanf("%s", input);
            decimal = octalToDecimal(input);
            printf("Decimal: %d\n", decimal);
            printf("Binary: ");
            decimalToBinary(decimal);
            printf("\nHexadecimal: ");
            decimalToHexadecimal(decimal);
            printf("\n");
            break;
        case 3:
            printf("\nEnter decimal number: ");
            scanf("%d", &decimal);
            printf("Binary: ");
            decimalToBinary(decimal);
            printf("\nOctal: ");
            decimalToOctal(decimal);
            printf("\nHexadecimal: ");
            decimalToHexadecimal(decimal);
            printf("\n");
            break;
        case 4:
            printf("\nEnter hexadecimal number: ");
            scanf("%s", input);
            decimal = hexadecimalToDecimal(input);
            printf("Decimal: %d\n", decimal);
            printf("Binary: ");
            decimalToBinary(decimal);
            printf("\nOctal: ");
            decimalToOctal(decimal);
            printf("\n");
            break;
    }
}
