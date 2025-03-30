#include <iostream>
#include <algorithm>

using namespace std;

int sequentialSearch(int arr[], int n, int key) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == key) return i;
    }
    return -1;
}

int binarySearch(int arr[], int n, int key) {
    int left = 0, right = n - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == key) return mid;
        else if (arr[mid] < key) left = mid + 1;
        else right = mid - 1;
    }
    return -1;
}

int main() {
    int n, arr[100], key;
    
    cout << "Enter number of elements: ";
    cin >> n;
    
    cout << "Enter elements: ";
    for (int i = 0; i < n; i++) cin >> arr[i];

    sort(arr, arr + n);
    
    cout << "Enter key to search: ";
    cin >> key;

    int seqRes = sequentialSearch(arr, n, key);
    if (seqRes != -1) cout << "Sequential Search: Found at index " << seqRes << endl;
    else cout << "Sequential Search: Not found" << endl;

    int binRes = binarySearch(arr, n, key);
    if (binRes != -1) cout << "Binary Search: Found at index " << binRes << endl;
    else cout << "Binary Search: Not found" << endl;

    return 0;
}

