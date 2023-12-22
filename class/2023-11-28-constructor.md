> **출처** <br>
> 📚 [명품 C++ Programming](https://product.kyobobook.co.kr/detail/S000001076322)

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
