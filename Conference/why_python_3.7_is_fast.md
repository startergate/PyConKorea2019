[< Go Back](../index.md)

파이썬 3.7 어찌 그렇게 빨라졌나 - 정겨울 ❄ [#](https://www.pycon.kr/program/talk-detail?id=127)
---

3.7부터 optimization 항목 추가

기본 메서드 호출
---
* 표준 라이브러리에 속한 클래스에 있는 여러 메서드 최적화
* METH_FASTCALL 컨벤션 따르도록 바꿈
   * 이에 맞춰 함수 선언시 성능 상 이득
* Argument Clinic
    * 함수 선언과 생성 도와줌
    * CPython 내장 함수 도움!
* 30%까지 빨라짐

파이썬 시작 시간
---
* abc 모듈을 C로 짬 
* site.py가 sysconfig import를 복사로 대체
    * 유지보수 우려로 필요한 부분만 가져오고, 유지보수에 필요한 부분에 주석을 담

인스턴스 메소드 호출
---
* positional arguments 함수 호출에 대한 새로운 opcode 2개 추가

asyncio.sleep
---
* 비교 연산자 하나 교체

이벤트 루프 가져오기
---
* C로 짬
* get_running_loop 개선
* getpid() 개선
    * os.getpid()를 버리고 시스템 함수로 교체

동시에 실행하기
---
* 코루틴 하나하나마다 function.partial 호출되던 것 제거
* ensure_future와 중복되는 부분 제거

asyncio.ensure_future
---
* if 문 순서를 바꿈
    * future인지 먼저 검사하던 것을 코루틴인지 먼저 검사하게 바꿈

typing 모듈 가져오기
---
* 제너릭 형식을 더 잘 지원하기 위해 __class_getitem__ 메서드 추가

리스트 정렬
---
* 타입을 한번만 미리 검사
* 미리 가정을 세우고 여러 pre-check stage를 만듬
* 최악의 경우 pre-check때문에 원래보다 15% 느려짐

딕셔너리 복사
---
* key, value를 통채로 복사하도록 바꿈

정규표현식
---
* lower/upper case 구분이 존재하는 글자에 대해서만 특정 케이스 적용
