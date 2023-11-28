# 멤버 변수 초기화

```c++
class Point {
    int x, y;

public:
    Point();
    Point(int a, int b);
};
```

## 생성자 코드에서 멤버 변수 초기화

```c++
Point::Point() {
    x = 0;
    y = 0;
}

Point::point(int a, int b) {
    x = a;
    y = b:
}
```

## 생성자 서두에 초깃값으로 초기화

멤버 변수와 초깃값을 쌍으로 지정하고 이들을 콤마(,)로 나열하여 작성할 수 있다.

```c++
Point::Point() : x(0), y(0) { // 멤버 변수 x, y를 0으로 초기화
}

point::Point(int a, int b) // 멤버 변수 x=a로, y=b로 초기화
    : x(a), y(b) { // 콜론(:) 이하 부분을 다음 줄에 써도 됨
}
```

## 클래스 선언부에서 직접 초기화

멤버 변수는 C++11부터 다음과 같이 선언문에서 직접 초기화할 수 있다.

```c++
class Point {
    int x=0, y=0; // 클래스 선언부에서 x, y를 0으로 직접 초기화
    ...
};
```