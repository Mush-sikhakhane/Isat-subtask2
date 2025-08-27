# Isat-subtask2
#include <iostream>
#include <string>
#include <bitset>
#include <sstream>
#include <cstdlib>   // for rand()
#include <ctime>     // for seeding rand()

using namespace std;

// Function 1: Decimal to Binary
string decimalToBinary(int num) {
    string binary = "";
    while (num > 0) {
        binary = (num % 2 == 0 ? "0" : "1") + binary;
        num /= 2;
    }
    return binary == "" ? "0" : binary;
}

// Function 2: Binary to Decimal
int binaryToDecimal(string binaryStr) {
    int decimal = 0;
    for (char c : binaryStr) {
        decimal = decimal * 2 + (c - '0');
    }
    return decimal;
}

// Function 3: Decimal to Hexadecimal
string decimalToHexadecimal(int num) {
    stringstream ss;
    ss << hex << uppercase << num;
    return ss.str();
}

// Function 4: Hexadecimal to Decimal
int hexadecimalToDecimal(string hexStr) {
    int decimal;
    stringstream ss;
    ss << hex << hexStr;
    ss >> decimal;
    return decimal;
}

// Menu System
void menu() {
    int choice;
    srand(time(0)); // Seed random generator

    while (true) {
        cout << "\n=== Conversion Menu ===\n";
        cout << "1. Convert Decimal to Binary\n";
        cout << "2. Convert Binary to Decimal\n";
        cout << "3. Convert Decimal to Hexadecimal\n";
        cout << "4. Convert Hexadecimal to Decimal\n";
        cout << "5. Generate random number (0–99) and convert to Binary\n";
        cout << "6. Exit\n";
        cout << "Enter your choice (1–6): ";
        cin >> choice;

        if (choice == 1) {
            int num;
            cout << "Enter a Decimal number: ";
            cin >> num;
            cout << "Binary representation: " << decimalToBinary(num) << endl;
        }
        else if (choice == 2) {
            string binaryStr;
            cout << "Enter a Binary number: ";
            cin >> binaryStr;
            cout << "Decimal representation: " << binaryToDecimal(binaryStr) << endl;
        }
        else if (choice == 3) {
            int num;
            cout << "Enter a Decimal number: ";
            cin >> num;
            cout << "Hexadecimal representation: " << decimalToHexadecimal(num) << endl;
        }
        else if (choice == 4) {
            string hexStr;
            cout << "Enter a Hexadecimal number: ";
            cin >> hexStr;
            cout << "Decimal representation: " << hexadecimalToDecimal(hexStr) << endl;
        }
        else if (choice == 5) {
            int num = rand() % 100; // Random number between 0–99
            cout << "Random number generated: " << num << endl;
            cout << "Binary representation: " << decimalToBinary(num) << endl;
        }
        else if (choice == 6) {
            cout << "Exiting program..." << endl;
            break;
        }
        else {
            cout << "Invalid choice, please try again." << endl;
        }
    }
}

int main() {
    menu();
    return 0;
}
