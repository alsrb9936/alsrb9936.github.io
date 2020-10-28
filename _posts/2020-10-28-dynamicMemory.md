---
title: "[C언어] 동적 메모리 할당"
date: 2020-10-28 08:26:28 -0400
categories: C언어
tags:
  - 동적메모리
  - C언어 문법
  - 언어 공부
toc: true
toc_sticky: true
author_profile: false
---
# *1. malloc()* 와 *free()* 함수


## 함수 정의

```c
#include <stdlib.h>
void * malloc(size_t size); //힙 영역에 메모리 할당 후 주소 값 반환
void * free(void * ptr); //메모리 할당 해제 
```

* 함수가 **매번 호출**될 때마다 **새롭게** 할당되고 또 함수를 빠져나가도 **유지**가 되는 유형의 변수

* **주소 값을 반환** 하기 때문에 **포인터**를 이용해 접근 가능 
  
  
  
## *malloc()* 함수의 형 변환

`mallc()` 의 **반환형**은 **void 형 포인터** 이므로  이를 사용할려면 가공이 필요하다.

다음과 같이 void형으로 반환되는 주소 값을 **적절히 형 변환**해서 할당된 메모리 공간에 접근 해야한다.

```c
int * ptr1 = (int *)malloc(sizeof(int));
double * ptr2 = (double *)malloc(sizeof(double));
```

`malloc()`  호출을 통한 메모리 할당을 '**동적 할당(dynamic allocation)**' 이라고 한다

  

  

## *free()* 함수 사용

프로그램 실행 시 할당된 모든 메모리 공간은 종료되면 운영체제에 의해 전부 해제가 된다.

하지만 습관적으로 `malloc()` 의 호출 횟수 만큼 `free()` 를 반드시 호출하자.

  

  

  

# *2. calloc()* 와 *realloc()* 함수


## 함수 정의

```c
#include <stdlib.h>
void * calloc(size_t block_count, size_t block_size); //블럭 수와 크기를 인자로 받아 메모리 할당
void * realloc(void * ptr, size_t size); //확장 대상 힙 메모리 시작 값과 확장 메모리의 전체 크기 전달받음
```

- `calloc()` 는 **인자 전달방식**에서 `malloc()` 와 차이점이 있다.
> ex) "4바이트 크기의 블록(block_size) 30개(block_count)를 힙 영역에 할당해 주세요"

- `calloc()` 는 할당된 메모리 공간의 **모든 비트를 0으로 초기화** 시킨다.

- `realloc()` 는 **확장 가능 영역**에 따라 `malloc()` 반환값과 **같을 수도 다를 수도 있다.**

  
