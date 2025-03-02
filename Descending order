#include <iostream>
#include <vector>
#include <chrono>

using namespace std;

void MergeTwoArrays(vector<int>& originalInputArray, vector<int>& leftPartition, vector<int>& rightPartition) {
    int leftSize = leftPartition.size();
    int rightSize = rightPartition.size();
    int leftPartitionIterator = 0, rightPartitionIterator = 0, originalArrayIterator = 0;

    while (leftPartitionIterator < leftSize && rightPartitionIterator < rightSize) {
        if (leftPartition[leftPartitionIterator] >= rightPartition[rightPartitionIterator])
            originalInputArray[originalArrayIterator++] = leftPartition[leftPartitionIterator++];
        else
            originalInputArray[originalArrayIterator++] = rightPartition[rightPartitionIterator++];
    }

    while (leftPartitionIterator < leftSize)
        originalInputArray[originalArrayIterator++] = leftPartition[leftPartitionIterator++];

    while (rightPartitionIterator < rightSize)
        originalInputArray[originalArrayIterator++] = rightPartition[rightPartitionIterator++];
}

void PerformMergeSort(vector<int>& arr) {
    int length = arr.size();
    if (length <= 1)
        return;

    int middleElementPosition = length / 2;
    vector<int> leftPartition(arr.begin(), arr.begin() + middleElementPosition);
    vector<int> rightPartition(arr.begin() + middleElementPosition, arr.end());

    PerformMergeSort(leftPartition);
    PerformMergeSort(rightPartition);
    MergeTwoArrays(arr, leftPartition, rightPartition);
}

int main() {
    int n;
    cout << "Enter the number of integers to sort: ";
    cin >> n;

    vector<int> inputArray(n);
    cout << "Enter " << n << " integers: ";
    for (int i = 0; i < n; i++)
        cin >> inputArray[i];

    auto start = chrono::high_resolution_clock::now();
    PerformMergeSort(inputArray);
    auto stop = chrono::high_resolution_clock::now();

    cout << "Sorted array (descending order): ";
    for (int i = 0; i < inputArray.size(); i++)
        cout << inputArray[i] << " ";
    cout << endl;

    auto duration = chrono::duration_cast<chrono::milliseconds>(stop - start);
    cout << "Sorting completed in " << duration.count() << " milliseconds" << endl;

    return 0;
}
