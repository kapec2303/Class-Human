#include <iostream>
#include <string>
using namespace std;
class Human {
private:
    int Height = 170;
    int Weight = 70;
public:
    Human(){}
    Human(int height, int weight) : Height(height), Weight(weight) {}

    int getHeight() const {
        return Height;
    }

    int getWeight() const {
        return Weight;
    }

    void setHeight(int height) {
        Height = height;
    }

    void setWeight(int weight) {
        Weight = weight;
    }

    virtual void Hello() {
        cout << "HELLO!" << endl;
    }
};

class Student : public Human {
private:
    int classid = 9;
    string name;
public:
    Student(int height, int weight, int classid, string name) : Human(height, weight), classid(classid), name(name) {}

    void Hello() override {
        cout << "Hello, I'm in " << classid << "th grade" << endl;
    }

    int getClassid() const {
        return classid;
    }

    const string &getName() const {
        return name;
    }
};

class Parent : public Human {
public:
    void Hello(Student b){
        cout << "Hello, my kid is " << b.getName() << endl;
    }
};

int main() {
Human Petya;
Student Vasya(190 ,90, 11, "Vasiliy");
Petya.Hello();
Vasya.Hello();
Parent Mama;
Mama.Hello(Vasya);
}
