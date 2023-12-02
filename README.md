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
//    virtual void Heal() {
//        cout << "I can't do it" << endl;
//    }
};

class Student : public Human {
private:
    int classid = 9;
    string name = "Igor";
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
    string name = "Oleg";
    int age = 30;
public:
    Worker(int height, int weight, const string &name, int age) : Human(height, weight), name(name), age(age) {}

    int getAge() const {
        return age;
    }

    void setName(const string &name) {
        Worker::name = name;
    }

    void setAge(int age) {
        Worker::age = age;
    }

    const string &getName() const {
        return name;
    }
    virtual void MyAge() {
        cout << "I'm " << age << " years old"<< endl;
    }

};

class Teacher :public  Worker {
public:
    Teacher(int height, int weight, const string &name, int age) : Worker(height, weight, name, age) {}


    void Ask(Student pupil) {
        cout << "Sorry, komissiya tebya zhdet" << endl;
        int a = pupil.getRau();
        a -= 1;
        pupil.setRau(a);
    }
    void MyAge() override {
        cout << "That's inappropriate :/" << endl;
    }
};

class HeadTeacher : Worker { //Директор)
public:
    HeadTeacher(int height, int weight, const string &name, int age) : Worker(height, weight, name, age) {}
    void Fire(Teacher bedolaga, Student pupil) {
        if (pupil.getRau() > 2) {
            cout << "Good job, " << bedolaga.getName();
        } else {
            cout << "You're fired!!!" << endl;
        }
    }

    void Exam(Student pupil) {
        if (pupil.getRau() > 3) {
            int a = pupil.getClassid();
            cout << "Congratulations! You have finished " << a << "th grade!" << endl;
        }
    }
};
int main() {
Human Petya;
Student Vasya(190,90, 11, "Vasiliy", 5);
Petya.Hello();
Vasya.Hello();
Parent Mama;
Mama.Hello(Vasya);
Teacher StrogiyTip(180, 90, "Professor", 40);
StrogiyTip.Ask(Vasya);
cout << "Now " << Vasya.getName() << " has " << Vasya.getRau() << " RAU :(" << endl;
cout << "Change name for Vasya: ";
Mama.Rename(Vasya);
Worker W(170, 70, "Rabotyaga", 40);
W.MyAge();
StrogiyTip.MyAge();
HeadTeacher Morkov(177, 60, "San'Sanna", 50);
Morkov.Exam(Vasya);
}
