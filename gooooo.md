# C Simple Encryption Program
C 언어를 사용하여 만든 간단한 문자 이동 암호화 프로그램
## 기능
- 문자열 입력
- ASCII 값을 이용한 문자 이동 암호화
## 사용 기술
- C
- 문자열 처리
- 반복문
## 실행 예시
입력:
hello
출력:
ifmmp

#include <stdio.h>
#include <string.h>

int main() {

    char text[100];
    int i;

    printf("문장 입력: ");
    fgets(text, sizeof(text), stdin);

    for(i = 0; text[i] != '\0'; i++) {
        text[i] = text[i] + 1;
    }

    printf("암호화 결과: %s", text);

    return 0;
}
