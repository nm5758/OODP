#include <iostream>
class Student
{
public:
    std::string name;  

private:
    int id;  
public:
    Student(std::string studentName, int studentId)
    {
        name = studentName;
        id = studentId;
    }
    int getId() {
        return id;
    }
};
int main() {
    Student student1("Alice", 101);
    student1.name = "Bob"; 
    std::cout << "Student Name: " << student1.name << std::endl;
    std::cout << "Student ID: " << student1.getId() << std::endl;  
    return 0;
}

