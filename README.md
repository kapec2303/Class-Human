#include <iostream>

class Human {
private:
    int Height = 170;
    int Weight = 70;
public:
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
};
int main() {

}
