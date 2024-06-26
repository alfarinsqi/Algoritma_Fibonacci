#include <iostream>
#include <chrono>
using namespace std;
using namespace chrono;

// Fungsi Fibonacci dengan pendekatan rekursif
int fibonacciRecursive(int n) {
    if (n <= 1)
        return n;
    return fibonacciRecursive(n - 1) + fibonacciRecursive(n - 2);
}

// Fungsi Fibonacci dengan pendekatan pemrograman dinamis
int fibonacciDynamic(int n) {
    int fib[n+1];
    fib[0] = 0;
    fib[1] = 1;
    for (int i = 2; i <= n; ++i) {
        fib[i] = fib[i-1] + fib[i-2];
    }
    return fib[n];
}

int main() {
    // Array untuk nilai n yang diuji
    int testValues[] = {10, 25, 30, 40, 50};

    for (int n : testValues) {
        // Mengukur waktu untuk Fibonacci rekursif
        auto start_recursive = high_resolution_clock::now();
        fibonacciRecursive(n);
        auto end_recursive = high_resolution_clock::now();
        auto duration_recursive = duration_cast<microseconds>(end_recursive - start_recursive);

        // Mengukur waktu untuk Fibonacci dengan pendekatan dinamis
        auto start_dynamic = high_resolution_clock::now();
        fibonacciDynamic(n);
        auto end_dynamic = high_resolution_clock::now();
        auto duration_dynamic = duration_cast<microseconds>(end_dynamic - start_dynamic);

        // Output hasil waktu eksekusi dalam detik
        cout << "n = " << n << endl;
        cout << "Waktu eksekusi Fibonacci rekursif: " << duration_recursive.count() / 1e6 << " detik" << endl;
        cout << "Waktu eksekusi Fibonacci dinamis: " << duration_dynamic.count() / 1e6 << " detik" << endl;
        cout << endl;
    }

    // Mengukur waktu untuk Fibonacci rekursif dan dinamis untuk n = 50
    auto start_recursive_50 = high_resolution_clock::now();
    fibonacciRecursive(50);
    auto end_recursive_50 = high_resolution_clock::now();
    auto duration_recursive_50 = duration_cast<microseconds>(end_recursive_50 - start_recursive_50);

    auto start_dynamic_50 = high_resolution_clock::now();
    fibonacciDynamic(50);
    auto end_dynamic_50 = high_resolution_clock::now();
    auto duration_dynamic_50 = duration_cast<microseconds>(end_dynamic_50 - start_dynamic_50);

    // Output hasil waktu eksekusi untuk n = 50
    cout << "n = 50" << endl;
    cout << "Waktu eksekusi Fibonacci rekursif: " << duration_recursive_50.count() / 1e6 << " detik" << endl;
    cout << "Waktu eksekusi Fibonacci dinamis: " << duration_dynamic_50.count() / 1e6 << " detik" << endl;

    return 0;
}



