Time complexity for sensor data for linear search 

    #include<stdio.h>
    #include<stdlib.h>
    #include<time.h>

    void generateData(float arr[], int n, float min, float max){
        for(int i = 0; i < n; i++){
            arr[i] = min+((float)rand()/RAND_MAX) * (max-min);
         }
    }

    int findMin(float arr[], int n){
       int minIndex = 0;
       for(int i = 1; i < n; i++){
          if(arr[i] < arr[minIndex]){
              minIndex = i;
          }
       }
    return minIndex;
    }

    int findMax(float arr[], int n){
       int maxIndex = 0;
       for(int i = 1; i < n; i++){
          if(arr[i] > arr[maxIndex]){
             maxIndex = i;
          }
        }
    return maxIndex;
    }

    int main(){
       int n = 1000;
       float temp[n],pressure[n];
       srand(time(0));

       generateData(temp, n, -20, 50);         // Temperature: -20 to 50 C

       clock_t start, end;
       double duration;

       // Min Temperature using Linear search
       start = clock();
       int minTempInd = findMin(temp, n);
       end = clock();
       duration = ((double)(end - start)) / CLOCKS_PER_SEC;
       printf("Linear Search:- \n\nMin Temp: %.2f at index %d, Time = %lf s\n",temp[minTempInd], minTempInd, duration);

       // Max Temperature using Linear search
       start = clock();
       int maxTempInd = findMax(temp, n);
       end = clock();
       duration = ((double)(end - start)) / CLOCKS_PER_SEC;
       printf("Max Temp: %.2f at index %d, Time = %lf s\n",temp[maxTempInd], maxTempInd, duration);

       generateData(pressure, n, 950, 1050);   // Pressure: 950 to 1050 hPa

        // Min Pressure using Linear search
        start = clock();
        int minPressInd = findMin(pressure, n);
        end = clock();
        duration = ((double)(end - start)) / CLOCKS_PER_SEC;
        printf("Linear Search:- \n\nMin Press: %.2f at index %d, Time = %lf s\n",pressure[minPressInd], minPressInd, duration);
    
        // Max Pressure using Linear search
        start = clock();
        int maxPressInd = findMax(pressure, n);
        end = clock();
        duration = ((double)(end - start)) / CLOCKS_PER_SEC;
        printf("Max Press: %.2f at index %d, Time = %lf s\n",pressure[maxPressInd], maxPressInd, duration);

        return 0;
    }
