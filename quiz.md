# C Korean History Quiz Game
C 언어를 사용하여 만든 한국사 퀴즈 게임
## 기능
- 3단계 난이도 문제
- 랜덤 문제 출제
- 점수 시스템
- 입력 검증 기능
## 사용 기술
- C
- 반복문 (while)
- 조건문 (if)
- 랜덤 함수 (rand)
- 사용자 입력 처리
## 보안 관련 요소
사용자의 잘못된 입력으로 인해 프로그램이 오류를 일으키지 않도록
입력 검증 함수(getNumberInput)쓰기
이를 통해 잘못된 입력을 처리하고
입력 버퍼를 정리하여 안정적인 입력 처리가 가능하도록 설계했다

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    int level;
    int answer;
    int userAnswer;
    int menu;
    int randomQuestion;
    int score = 0;

    srand(time(NULL));

    while (1) {
        printf("\n====================================\n");
        printf("         한국사 퀴즈 게임\n");
        printf("====================================\n");
        printf("현재 점수: %d점\n", score);
        printf("문제 단계를 선택하세요.\n");
        printf("1. 1단계 (100점)\n");
        printf("2. 2단계 (300점)\n");
        printf("3. 3단계 (500000점)\n");
        printf("선택: ");
        scanf("%d", &level);

        randomQuestion = rand() % 3;

        printf("\n");

        if (level == 1) {
            if (randomQuestion == 0) {
                printf("[1단계 문제]\n");
                printf("고조선을 세운 인물은 누구인가?\n");
                printf("1. 주몽\n");
                printf("2. 단군왕검\n");
                printf("3. 박혁거세\n");
                printf("정답 입력: ");
                scanf("%d", &userAnswer);
                answer = 2;
            }
            else if (randomQuestion == 1) {
                printf("[1단계 문제]\n");
                printf("세종대왕이 만든 문자는 무엇인가?\n");
                printf("1. 한자\n");
                printf("2. 훈민정음\n");
                printf("3. 이두\n");
                printf("정답 입력: ");
                scanf("%d", &userAnswer);
                answer = 2;
            }
            else {
                printf("[1단계 문제]\n");
                printf("임진왜란 때 활약한 장군은 누구인가?\n");
                printf("1. 이순신\n");
                printf("2. 강감찬\n");
                printf("3. 을지문덕\n");
                printf("정답 입력: ");
                scanf("%d", &userAnswer);
                answer = 1;
            }

            if (userAnswer == answer) {
                printf("\n정답입니다! +100점\n");
                score += 100;
            } else {
                printf("\n오답입니다!\n");
            }
        }
        else if (level == 2) {
            if (randomQuestion == 0) {
                printf("[2단계 문제]\n");
                printf("고려를 세운 인물은 누구인가?\n");
                printf("1. 왕건\n");
                printf("2. 이성계\n");
                printf("3. 궁예\n");
                printf("정답 입력: ");
                scanf("%d", &userAnswer);
                answer = 1;
            }
            else if (randomQuestion == 1) {
                printf("[2단계 문제]\n");
                printf("조선을 세운 인물은 누구인가?\n");
                printf("1. 왕건\n");
                printf("2. 이성계\n");
                printf("3. 광개토대왕\n");
                printf("정답 입력: ");
                scanf("%d", &userAnswer);
                answer = 2;
            }
            else {
                printf("[2단계 문제]\n");
                printf("삼국 통일을 이룬 나라는?\n");
                printf("1. 백제\n");
                printf("2. 고구려\n");
                printf("3. 신라\n");
                printf("정답 입력: ");
                scanf("%d", &userAnswer);
                answer = 3;
            }

            if (userAnswer == answer) {
                printf("\n정답입니다! +300점\n");
                score += 300;
            } else {
                printf("\n오답입니다!\n");
            }
        }
        else if (level == 3) {
            if (randomQuestion == 0) {
                printf("[3단계 문제]\n");
                printf("흥선대원군이 추진한 정책으로 알맞은 것은?\n");
                printf("1. 경복궁 중건\n");
                printf("2. 한글 창제\n");
                printf("3. 대동법 실시\n");
                printf("정답 입력: ");
                scanf("%d", &userAnswer);
                answer = 1;
            }
            else if (randomQuestion == 1) {
                printf("[3단계 문제]\n");
                printf("을지문덕이 활약한 전쟁은?\n");
                printf("1. 임진왜란\n");
                printf("2. 살수대첩\n");
                printf("3. 병자호란\n");
                printf("정답 입력: ");
                scanf("%d", &userAnswer);
                answer = 2;
            }
            else {
                printf("[3단계 문제]\n");
                printf("독립협회를 만든 인물은 누구인가?\n");
                printf("1. 안중근\n");
                printf("2. 유관순\n");
                printf("3. 서재필\n");
                printf("정답 입력: ");
                scanf("%d", &userAnswer);
                answer = 3;
            }

            if (userAnswer == answer) {
                printf("\n정답입니다! +500000점\n");
                score += 500000;
            } else {
                printf("\n오답입니다!\n");
            }
        }
        else {
            printf("잘못된 입력입니다. 다시 선택하세요.\n");
            continue;
        }

        printf("현재 점수: %d점\n", score);

        printf("\n1. 계속하기\n");
        printf("2. 나가기\n");
        printf("선택: ");
        scanf("%d", &menu);

        if (menu == 2) {
            printf("\n게임을 종료합니다.\n");
            printf("최종 점수: %d점\n", score);
            break;
        }
        else if (menu != 1) {
            printf("잘못된 입력입니다. 처음으로 돌아갑니다.\n");
        }
    }

    return 0;
}
