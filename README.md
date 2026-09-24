// Movie-Ticket-Pricing
#include <iostream>
#include <iomanip>
#include <cmath>
#include <cstdlib>
#include <fstream>

using namespace std;
int main() {

    // Data Abstraction:
   int customerAge;
   char dayType;
   string fileName;
   ifstream inFile;
   int childAge, adultAge, seniorAge;
   double childPrice, adultWeekdayPrice, adultWeekendPrice, seniorPrice;
   double ticketPrice;
   
    // Input:
    cout << "Enter customer age: ";
    cin >> customerAge;
    cout << customerAge << endl;
   
    cout << "Enter day type (W for weekday, E for weekend): ";
    cin >> dayType;
    cout << dayType << endl;
    
    cout << "Enter the rules filename: ";
    cin >> fileName;
    cout << fileName;
    
    
    // Process:
    inFile.open(fileName);
    
    if (!inFile) {
        cout << "Error: Rules File Did Not Open!" << endl;
    }
    else{
        inFile >> childAge >> childPrice;
        inFile >> adultAge >> adultWeekdayPrice >> adultWeekendPrice;
        inFile >> seniorAge >> seniorPrice;
        
        inFile.close();
    }
    
    //Conditions for Ticket pricing
    if (customerAge <= childAge){
       ticketPrice = childPrice;
    }
    
    else if (customerAge <= adultAge){
        if (dayType == 'W'){
        ticketPrice = adultWeekdayPrice;
        }
        else if (dayType == 'E'){
        ticketPrice = adultWeekendPrice;
        }
    }
    
    else if (customerAge >= seniorAge){
        ticketPrice = seniorPrice;
    }
    
    // Output:
   cout << endl;
   cout << fixed << setprecision(2);
   cout << "Ticket price: $" << ticketPrice;
   
}
    // Assumptions:

 
    return 0;

 

}
