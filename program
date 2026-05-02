#include <iostream>
#include <fstream>
#include <vector>
using namespace std;

class Student {
public:
    int id;
    string name;
    int age;
    string course;

    void input() {
        cout << "Enter ID: ";
        cin >> id;
        cout << "Enter Name: ";
        cin.ignore();
        getline(cin, name);
        cout << "Enter Age: ";
        cin >> age;
        cout << "Enter Course: ";
        cin.ignore();
        getline(cin, course);
    }

    void display() {
        cout << "ID: " << id << endl;
        cout << "Name: " << name << endl;
        cout << "Age: " << age << endl;
        cout << "Course: " << course << endl;
        cout << "----------------------" << endl;
    }
};

// Load students from file
vector<Student> loadStudents() {
    vector<Student> students;
    ifstream file("students.txt");

    Student s;
    while (file >> s.id) {
        file.ignore();
        getline(file, s.name);
        file >> s.age;
        file.ignore();
        getline(file, s.course);
        students.push_back(s);
    }

    file.close();
    return students;
}

// Save students to file
void saveStudents(vector<Student> students) {
    ofstream file("students.txt");

    for (auto s : students) {
        file << s.id << endl;
        file << s.name << endl;
        file << s.age << endl;
        file << s.course << endl;
    }

    file.close();
}

// Add student
void addStudent() {
    Student s;
    ofstream file("students.txt", ios::app);

    s.input();

    file << s.id << endl;
    file << s.name << endl;
    file << s.age << endl;
    file << s.course << endl;

    file.close();
    cout << "Student added successfully!\n";
}

// Display students
void displayStudents() {
    vector<Student> students = loadStudents();

    if (students.empty()) {
        cout << "No records found.\n";
        return;
    }

    for (auto s : students) {
        s.display();
    }
}

// Delete student
void deleteStudent() {
    int id;
    cout << "Enter ID to delete: ";
    cin >> id;

    vector<Student> students = loadStudents();
    vector<Student> updated;

    bool found = false;

    for (auto s : students) {
        if (s.id != id) {
            updated.push_back(s);
        } else {
            found = true;
        }
    }

    saveStudents(updated);

    if (found)
        cout << "Student deleted successfully!\n";
    else
        cout << "Student not found.\n";
}

// Update student
void updateStudent() {
    int id;
    cout << "Enter ID to update: ";
    cin >> id;

    vector<Student> students = loadStudents();
    bool found = false;

    for (auto &s : students) {
        if (s.id == id) {
            cout << "Enter new details:\n";
            s.input();
            found = true;
            break;
        }
    }

    saveStudents(students);

    if (found)
        cout << "Student updated successfully!\n";
    else
        cout << "Student not found.\n";
}

int main() {
    int choice;

    do {
        cout << "\n===== Student Management System =====\n";
        cout << "1. Add Student\n";
        cout << "2. Display Students\n";
        cout << "3. Update Student\n";
        cout << "4. Delete Student\n";
        cout << "5. Exit\n";
        cout << "Enter choice: ";
        cin >> choice;

        switch (choice) {
            case 1: addStudent(); break;
            case 2: displayStudents(); break;
            case 3: updateStudent(); break;
            case 4: deleteStudent(); break;
            case 5: cout << "Exiting...\n"; break;
            default: cout << "Invalid choice!\n";
        }

    } while (choice != 5);

    return 0;
}
