#include <iostream>

class Book {
public:
    std::string title, author, isbn;
    bool available = true;

    Book() {} 
    Book(std::string t, std::string a, std::string i) : title(t), author(a), isbn(i) {}
};

class Library {
private:
    Book books[100]; 
    int count = 0;

public:
    void addBook(Book book) { books[count++] = book; }

    void borrowBook(std::string isbn) {
        for (int i = 0; i < count; i++)
            if (books[i].isbn == isbn && books[i].available) {
                books[i].available = false;
                std::cout << "Borrowed: " << books[i].title << "\n"; 
                return;
            }
        std::cout << "Book not available!\n";
    }

    void returnBook(std::string isbn) {
        for (int i = 0; i < count; i++)
            if (books[i].isbn == isbn && !books[i].available) {
                books[i].available = true;
                std::cout << "Returned: " << books[i].title << "\n"; 
                return;
            }
        std::cout << "Book not found!\n";
    }

    void displayBooks() {
        for (int i = 0; i < count; i++)
            std::cout << books[i].title << " - " << (books[i].available ? "Available" : "Borrowed") << "\n";
    }
};

int main() {
    Library lib;
    lib.addBook(Book("C++ Primer", "Lippman", "12345"));
    lib.addBook(Book("Effective C++", "Meyers", "67890"));

    lib.displayBooks();
    lib.borrowBook("12345");
    lib.returnBook("12345");

    return 0;
}

