#include <iostream>
class Vehicle {
public:
    int speed;  
    void displayStatus()
    {  
        std::cout << "Speed: " << speed << " km/h\n";
    }
};

int main()
{
    Vehicle car;  
    car.speed = 50;  
    int Vehicle::*ptrSpeed = &Vehicle::speed;
    void (Vehicle::*ptrDisplay)() = &Vehicle::displayStatus;

    car.*ptrSpeed = 80;  
    
    (car.*ptrDisplay)();  

    return 0;
}
