# CPlusPlus-Cheatsheet


### Class

- Initializations
```c++

struct B
{
    explicit B(int) { }
    explicit B(int, int) { }
    explicit operator bool() const { return true; }
};
 
int main()
{

//  B b1 = 1;      // error: copy-initialization does not consider B::B(int)
    B b2(2);       // OK: direct-initialization selects B::B(int)
    B b3 {4, 5};   // OK: direct-list-initialization selects B::B(int, int)
//  B b4 = {4, 5}; // error: copy-list-initialization does not consider B::B(int,int)
    B b5 = (B)1;   // OK: explicit cast performs static_cast
    if (b2) ;      // OK: B::operator bool()
//  bool nb1 = b2; // error: copy-initialization does not consider B::operator bool()
    bool nb2 = static_cast<bool>(b2); // OK: static_cast performs direct-initialization
}
// reference : https://en.cppreference.com/w/cpp/language/explicit
```

- Operator overloading
    1. Design of Operator + 
``` c++
// 先設計 += 再設計 +
Point const operator+(Point const &lhs, Point const &rhs) // 
{
  return Point(lhs) += rhs; // 
}

// [心得] operator+ 與 operator+= 的設計
// https://www.ptt.cc/man/C_and_CPP/D8D2/DA94/DDBB/M.1127480887.A.E7F.html
```

- Rvalue
    - [\[C++\] rvalue reference 初入門](https://shininglionking.blogspot.com/2013/06/c-rvalue-reference.html)
        - lvalue, rvalue, &&, use of std::move
    - [What is move semantics?](https://stackoverflow.com/questions/3106110/what-is-move-semantics)


### Compiler behaviour
- optimize
    - [什么时候应当依靠返回值优化（RVO）](https://www.zhihu.com/question/27000013)
- Object
    - RAII


## Reading list
- Effective Modern C++
- Clean Code: A Handbook of Agile Software Craftsmanship
- \[Almost Done\]
    - 程序員的自我修養:鍵結,裝載與庫
