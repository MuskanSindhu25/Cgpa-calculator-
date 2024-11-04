

#include <iostream>

#include <limits>  

using namespace std;



double calculateCGPA(double grades[], double credits[], int totalSubjects) {

    double weightedSum = 0;

    double totalCredits = 0;

    

    for (int i = 0; i < totalSubjects; ++i) {

        weightedSum += grades[i] * credits[i]; 

        totalCredits += credits[i];

    }

    

    return weightedSum / totalCredits; 

}



double getValidInput(string prompt) {

    double input;

    while (true) {

        cout << prompt;

        cin >> input;

        

        if (cin.fail() || input < 0) { 

            cin.clear(); 

            cin.ignore(numeric_limits<streamsize>::max(), '\n'); 

            cout << "Invalid input. Please enter a valid positive number." << endl;

        } else {

            return input;

        }

    }

}



int main() {

    int numSubjects;



    cout << "Enter the number of subjects: ";

    cin >> numSubjects;



    double grades[100], credits[100];

    

    for (int i = 0; i < numSubjects; ++i) {

        grades[i] = getValidInput("Enter grade for subject " + to_string(i + 1) + ": ");

        credits[i] = getValidInput("Enter credits for subject " + to_string(i + 1) + ": ");

    }



    double cgpa = calculateCGPA(grades, credits, numSubjects);

    cout << "Your CGPA is: " << cgpa << endl;



    return 0;

}


