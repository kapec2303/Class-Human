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
    int RAU = 4;
public:
    Student(int height, int weight, int classid, string name, int RAU) : Human(height, weight), classid(classid), name(name), RAU(RAU) {}

    void Hello() override {
        cout << "Hello, I'm in " << classid << "th grade" << endl;
    }

    int getClassid() const {
        return classid;
    }

    const string &getName() const {
        return name;
    }

    void setName(const string &name) {
        Student::name = name;
    }

    void setRau(int rau) {
        RAU = rau;
    }

    int getRau() const {
        return RAU;
    }
};

class Parent : public Human {
public:
    void Hello(Student b){
        cout << "Hello, my kid is " << b.getName() << endl;
    }
    void Rename(Student b) {
        string a;
        cin >> a;
        b.setName(a);
        cout << "Now this kid is called " << b.getName() << endl;
    }
};

class Worker : public Human {
private:
    string name;
    int age;
public:
    Worker(int height, int weight, const string &name, int age) : Human(height, weight), name(name), age(age) {}

    const string &getName() const {
        return name;
    }

    int getAge() const {
        return age;
    }

    void setName(const string &name) {
        Worker::name = name;
    }

    void setAge(int age) {
        Worker::age = age;
    }
};

class Teacher : Worker {
public:
    Teacher(int height, int weight, const string &name, int age) : Worker(height, weight, name, age) {}

    void Ask(Student pupil) {
        cout << "Sorry, komissiya tebya zhdet" << endl;
        int a = pupil.getRau();
        a -= 1;
        pupil.setRau(a);
    }
};
int main() {
Human Petya;
Student Vasya(190 ,90, 11, "Vasiliy", 5);
Petya.Hello();
Vasya.Hello();
Parent Mama;
Mama.Hello(Vasya);
Teacher StrogiyTip(180, 90, "Professor", 40);
StrogiyTip.Ask(Vasya);
cout << "Now " << Vasya.getName() << " has " << Vasya.getRau() << " RAU :(" << endl;
Mama.Rename(Vasya);
}
