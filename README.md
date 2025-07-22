// Time_Complexity

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

void generateData(float arr[], int n, float min, float max) {
    for (int i = 0; i < n; i++)
        arr[i] = min + ((float)rand() / RAND_MAX) * (max - min);
}

int findMinPairwise(float arr[], int n) {
    for (int i = 0; i < n; i++) {
        int isMin = 1;
        for (int j = 0; j < n; j++) {
            if (arr[j] < arr[i]) {
                isMin = 0;
                break;
            }
        }
        if (isMin) return i;
    }
    return -1;
}

int findMaxPairwise(float arr[], int n) {
    for (int i = 0; i < n; i++) {
        int isMax = 1;
        for (int j = 0; j < n; j++) {
            if (arr[j] > arr[i]) {
                isMax = 0;
                break;
            }
        }
        if (isMax) return i;
    }
    return -1;
}

int main() {
    int n = 1000;   // Use n = 1000 for tasks with O(n^2) - larger n may take very long
    float temp[n], pressure[n];
    srand(time(0));

    generateData(temp, n, -20, 50);        // Temperature: -20 to 50°C
    generateData(pressure, n, 950, 1050);  // Pressure: 950 to 1050 hPa

    clock_t start, end;
    double duration;

    // Pairwise Comparison for Minimum Temperature
    start = clock();
    int minTempInd = findMinPairwise(temp, n);
    end = clock();
    duration = ((double)(end - start)) / CLOCKS_PER_SEC;
    printf("Pairwise: Min Temperature = %.2f at index %d, Time = %lf s\n", temp[minTempInd], minTempInd, duration);

    // Pairwise Comparison for Maximum Pressure
    start = clock();
    int maxPressInd = findMaxPairwise(pressure, n);
    end = clock();
    duration = ((double)(end - start)) / CLOCKS_PER_SEC;
    printf("Pairwise: Max Pressure = %.2f at index %d, Time = %lf s\n", pressure[maxPressInd], maxPressInd, duration);

    return 0;
}
