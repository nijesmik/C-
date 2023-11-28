# 생성자 (Constructor)

```c++
/* 선언부 */
class Circle {
public:
    int radius;

    Circle();
    Circle(int r);
}

/* 구현부 */
Circle::Circle() {
    radius = 1;
}

Circle::Circle(int r) {
    radius = r;
}
```

생성자 함수는 함수 실행을 종료하기 위해 `return`문을 사용할 수 있다. 그러나 어떤 값도 리턴하면 안 된다.

```c++
Circle::Circle() {
    ...
    return; // 생성자 함수를 종료하는 정상적인 리턴문
}

Circle::Circle() {
    ...
    return 0; // 컴파일 오류. 생성자 함수는 값을 리턴해서는 안 됨
}
```

## 객체 생성

```c++
Circle circle1;

Circle circle2(5);
```

`circle1`이 생성될 때 매개 변수 없는 `Circle()`이 호출되며, `circle2`가 생성될 때 `Circle(int r)`을 호출하고 매개 변수 `r`에 `5`가 전달된다.

## 위임 생성자 (delegating constructor)

C++11부터는 중복된 초기화 코드를 하나의 생성자로 몰고, 다른 생성자에서 이 생성자를 호출할 수 있게 한다. 이 기능을 이용하면 앞의 코드는 다음과 같이 간소화된다.

```c++
/* 위임 생성자 */
Circle::Circle() : Circle(1) { } // Circle(int r)의 생성자 호출

/* 타겟 생성자 */
Circle::Circle(int r) {
    radius = r;
}
```

여기서, `Circle(int r)`을 **타겟 생성자**라고 부르고, `Circle()` 생성자는 객체의 초기화를 다른 생성자에 위임한다고 해서 **위임 생성자(delegating constructor)**라고 부른다. 위임 생성자에서는 타겟 생성자를 호출한 뒤, 자신만의 코드를 추가하면 된다.