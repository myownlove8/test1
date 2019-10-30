## 생성자
 
  - 생성자는 객체를 생성하기 위한 함수 형태
  - 리턴타입이 없다.
  - 오버로딩이 가능하다.

  ```
#include <iostream>
#include <string.h>

using namespace std;

class TestObj{
    string name;
    int age;
public:
    TestObj();                         // default 생성자 
    TestObj(string name);         // 생성자 오버로딩
    TestObj(int age);
  //TestObj(int age = 0);          //default값을 지정하여 초기화 할수 있다.
    TestObj(string name, int age);
}

TestObj::TestObj(string name){   // 생성자 함수의 정의
   this-> name = name;           //this는 자신의 객체를 가리킨다.
}

TestObj::TestObj(string name, int age):name(‘name’),age(age){}; 
// TestObj::TestObj(string name, int age){ this->name = name; this-> age = age;}; 와 같은 표현

void main(){
    TestObj obj2 = new TestObj(); // default 생성자로 new 키워드를 사용해 heap메모리에 할당
}

  ```

  ## 오버로딩 (Overloading)
 
  - 오버로딩이란 하나의 함수명으로 여러가지 동작을 할수 있게, 매개변수 갯수나 타입을 다르게 하여 함수명은 같지만 다르게 구분할 수 있게 하는것이다. 
  - 리턴타입 변경으로 오버라이딩을 할수 없다.
  - 함수나 생성자에 적용할수 있다.

  ```
#include "TestObj.h"
#include <iostream>
#include <string.h>

using namespace std;

class TestObj {
	string name;
	int age;
public:
	TestObj();                         // default 생성자 
	TestObj(string name, int age);
	void setInfo(string name);
	void setInfo(int age);
	void setInfo(string name, int age);
	string getName();
	int getAge();
};

TestObj::TestObj(string name, int age) {
	this->name = name;
	this->age = age;
}

void TestObj::setInfo(string name) {
	this->name = name;
}

void TestObj::setInfo(int age) {
	this->age = age;
}

void TestObj::setInfo(string name, int age) {
	this->name = name;
	this->name = age;
}

string TestObj::getName() {
	return this->name;
}

int TestObj::getAge() {
	return this->age;
}
void showInfo(TestObj &obj) {
	cout <<"이름 : "<<obj.getName() <<", ";
	cout <<"나이 : "<<obj.getAge() << endl;
}

void main() {
	TestObj obj("AAA", 30);
	showInfo(obj);        // 이름 : AAA, 나이 : 30
	obj.setInfo("BBB");
	showInfo(obj);        // 이름 : BBB, 나이 : 30
	obj.setInfo(25);
	showInfo(obj);        // 이름 : BBB, 나이 : 25
	obj.setInfo("CCC",53);
	showInfo(obj);        // 이름 : 5, 나이 : 25
}
  ```

## 복사생성자 / 소멸자
 
  - 같은 타입의 객체를 참조하여 생성하는것을 복사 생성자라고 한다.
  - const로 지정하여 참조하는 객체의 값을 변경할수 없고, 참조만 가능하게 한다.
  - 소멸자는 객체의 사용이 종료되었을때 호출된다.
  - 소멸자는 오버로딩할수 없다.

  ```
#include "TestObj.h"
#include <iostream>
#include <string.h>

using namespace std;

class TestObj {
	string name;
	int age;
public:
	TestObj();                         // default 생성자 
    ~TestObj(); 
	TestObj(string name, int age);
    TestObj(const TestObj &obj);
    string getName();
	int getAge();
};

TestObj::TestObj(string name, int age) {
	this->name = name;
	this->age = age;
}

TestObj::TestObj(const TestObj &obj) {
	this->name = obj.name;
	this->age = obj.age;
}

string TestObj::getName() {
	return this->name;
}

int TestObj::getAge() {
	return this->age;
}

void showInfo(TestObj &obj) {
	cout <<"이름 : "<<obj.getName() <<", ";
	cout <<"나이 : "<<obj.getAge() << endl;
}

void main() {
	TestObj obj("AAA", 30);
	showInfo(obj);        // 이름 : AAA, 나이 : 30
    TestObj obj2(obj);
    showInfo(obj2)        // 이름 : AAA, 나이 : 30
}
  ```

## 명시적 변환 (explicit) 
 
  - 같은 타입의 객체를 참조하여 생성하는것을 복사 생성자라고 한다.
  - const로 지정하여 참조하는 객체의 값을 변경할수 없고, 참조만 가능하게 한다.
  - 소멸자는 객체의 사용이 종료되었을때 호출된다.
  - 소멸자는 오버로딩할수 없다.

  ```
#include "TestObj.h"
#include <iostream>
#include <string.h>

using namespace std;

class TestObj {
	string name;
	int age;
public:
	TestObj();                         // default 생성자 
	TestObj(string name);
	explicit TestObj(int age);
    string getName();
	int getAge();
};

TestObj::TestObj(string name) {
	this->name = name;
}

TestObj::TestObj(int age) {
	this->age = age;
}

string TestObj::getName() {
	return this->name;
}

int TestObj::getAge() {
	return this->age;
}

void showName(TestObj obj) {
	
}

void main() {
    showName('AAA'); 
    // 매개변수 AAA를 넣어주면 알아서 생성자 TestObj(string name)을 찾아서 넣는 암시적 변환이 일어난다.

    showName(30);   
    // showName()이라는 함수가 이름을 출력하는 함수인데, 숫자를 매개변수로 던지는 경우 TestObj(int age)를 찾아서 넣기 때문에 시스템 오류를 만들수 있다.
	// 이러한 경우에 explicit이라는 키워드를 선언하여 암시적 형변환이 일어나지 않도록한다.
}
  ```

## 오버라이딩(overriding)

  - 부모 객체로 붙어 받은 함수를 재정의 하는 것을 말한다. 
  - Human.h

  ```
  #include <iostream>
#include <string.h>

#ifndef  HUMAN_H
#define HUMAN_H

using namespace std;

class Human
{
	string name;
	int age;
public:
	Human();
	Human(string name, int age);
	void setInfo(string name, int age);
	void setName(string name);
	void setAge(int age);
	string getName();
	int getAge();
	virtual void showPrint();
};
#endif // ! HUMAN_H
  ```

- Human.cpp
 ```
#include "Human.h"

Human::Human(string name, int age) {
	this->name = name;
	this->age = age;
}
void Human::setInfo(string name, int age) {
	this->name = name;
	this->age = age;
}
void Human::setName(string name) {
	this->name = name;

}

void Human::setAge(int age) {
	this->age = age;
}

string Human::getName() {
	return this->name;
};
int Human::getAge() {
	return this->age;
};

void Human::showPrint() {
	cout << this->name << ", " << this->age << endl;
}
```
  
- Student.h
```
#include "Human.h"

#ifndef  STUDENT_H
#define STUDENT_H

class Student : public Human
{
	char grade;
	string schoolAddr;
public:
	Student();
	Student(string name, int age, char grade, string schoolAddr);
	void setGrade(char grade);
	char getGrade();
	void setSchoolAddr(string schooladdr);
	string getSchoolAddr();
	void showPrint();
	

};

#endif // ! STUDENT_H
```
- Student.cpp
```
#include "Student.h"

Student::Student(string name, int age, char grade, string schoolAddr) :Human(name, age) {
	this->grade = grade;
	this->schoolAddr = schoolAddr;
};

void Student::setGrade(char grade) {

};
char Student::getGrade() {
	return this->grade;
};
void Student::setSchoolAddr(string schooladdr) {
	this->schoolAddr = schoolAddr;
};

string Student::getSchoolAddr() {
	return this->schoolAddr;
};

void Student::showPrint() {
	cout << "이름 : " << getName() << endl;
	cout << "나이 : " << getAge() << endl;
	cout << "학점 : " << this->grade << endl;
	cout << "학교주소 : " << this->schoolAddr << endl;
}

```



