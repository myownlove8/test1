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

  ```