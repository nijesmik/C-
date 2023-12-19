> **출처** <br>
> 📚 [명품 C++ Programming](https://product.kyobobook.co.kr/detail/S000001076322)

# namespace

2003년 C+ 표준에서는 여러 프로젝트나 여러 사람들이 작성한 프로그램에서 변수, 함수, 클래스 등의 이름(identifer)이 충돌하는 것을 막기 위해, 개발자가 자신만의 고유한 identifier 공간을 생성할 수 있도록 `namespace` 키워드를 도입하였다. 서로 다른 `namespace` 안에 선언된 identifier들은 별개의 identifier으로 취급되기 때문에, 각 개발자가 자신만의 `namespace`을 사용하면 identifier의 충돌을 막을 수 있다.

`namespace`를 생성하는 방법은 다음과 같이 `namespace` 키워드 뒤에 자신만의 namespace 이름을 짓고 `{}`로 묶는다.

```c++
namespace foo {
    /* identifiers */
    int bar;
}
```

그리고 identifier를 이용하기 위해서는 다음과 같이 `namespace`를 함께 사용한다.

```c++
/* namespcae::identifier */
foo::bar
```

이때, `::`는 **범위 지정 연산자**로서 C++ 표준 연산자이다.

# std

`std`는 2003년 C++ 표준에서 정한 **표준 namespace**로서, 모든 C++ 표준 라이브러리는 `std` namespace에 만들어져 있다. 그러므로 응용 프로그램이 C++ 표준 라이브러리에서 선언된 identifer를 사용할 때, `std::`를 접두어로 붙여야 한다.

```c++
std::cout << "Hello" << std::endl;
```

# using 지시어

`std` namespace에 선언된 수많은 identifier에 대해 사용할 때마다 `std::` 접두어를 붙이는 것은 상당히 번거롭다. `using` 지시어를 이용하면 namespace 접두어를 생략할 수 있는데, 다음은 `cout` 앞의 `std::`를 생략하도록 `using` 지시어를 사용한 사례이다.

```c++
using std::cout; // cout에 대해서만 std:: 생략

cout << "Hello" << std::endl; // cout에 대해서만 std:: 생략
```

앞의 `using` 지시어는 `cout`이 `std` namespace에 선언된 identifier임을 공표함으로써, 지시어 아래 모든 코드에서 `cout` 앞에 `std::`를 생략할 수 있다. 그러나 `endl` 앞에는 `std::`를 생략할 수 없다. 만일, `std` namespace에 선언된 모든 이름에 대해 `std::`를 생략하고자 한다면, 다음과 같이 `namespace` 키워드와 함께 `using` 지시어를 사용하면 된다.

```c++
using namespace std; // std namespace에 선언된 모든 identifier에 std:: 생략

cout << "Hello" << endl; // cout과 endl 앞에 std:: 생략
```