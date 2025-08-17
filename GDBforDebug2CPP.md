# Debugging Note
---

### PWNDBG
---
frame - 스택 프레임을 볼 수 있음 (입력 예시: bt에 #37번 콜스택 프레임을 보고싶다면 frame 37)

list - 현재 소스코드 위치 및 주변 소스들을 볼 수 있음 (출력 예시: list -> src/compiler/pipeline.cc:730)

info args - 현재 함수의 인자 정보를 볼 수 있음(입력 예시: i args)

info locals - 현재 스택 프레임의 지역 변수 출력 (입력 예시: i locals)

tbreak - temp break point로 임시 브레이크 포인트로 한번 걸리면 사라짐

cond - 조건부 브레이크 포인트(입력 예시: 만약 v8_flags.turbolev가 켜져있을 때 브레이크 포인트를 걸고 싶다면 cond 2 v8_flags.turbolev, 
혹은 cond 3 ((void*)linkage) == (void*)0x55555bb25a40 등의 방법으로 쓰기 가능)

rbreak - 함수 심볼에 브레이크 포인트 걸기

commands - 브레이크 포인트 스크립트 작성 가능

telescope - 

dumpargs - call 될 함수의 인자 정보 확인

retaddr - 현재 스택 프레임 함수 내에서 ret addr를 찾아줌

p scope.data_ - 필드 값만 출력

set - 특정 필드 값 수정(입력 예시: v8_flags.turbolev = false) 

p *$(구조체) - 구조체 출력

catch syscall 시스콜명 - 특정 시스콜 발생 시 잡아줌(입력 예시: catch syscall write)

p this, p *this - 현재 구조체의 생성자 필드 보는 방법




## 옵션
---

handle SIGABRT stop print pass - SIGABRT 발생 시 멈춤

set print asm-demangle on
set print demangle on - 디맹글 키기


## 참고사항 
---

C++ 디버깅 시 현재 스택 프레임 내의 지역 변수만을 볼 수 있음

보통 생성자는 컴파일 시 인라인 어셈으로 들어가며 bt를 찍었을 땐 논리적으로 스택 프레임에 있는 것처럼 보이지만 실제로는 main에 인라이닝 되어 있음. ((gdb) set debug inline-frame on 해당 옵션을 키면
진입으로 안잡힐듯)





