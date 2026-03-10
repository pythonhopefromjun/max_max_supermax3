# Dreamhack - Admin Login
https://dreamhack.io/wargame/challenges/2678
## 취약점
Session Forgery (세션 위조)

## 문제 분석

세션 생성 코드:

```python
def make_session(username: str, created_at: int) -> str:
    return f"{username}.{created_at * 2026}"

세션 검증 코드:

def verify_session(value: str, created_at: int) -> str | None:
    username, token = parsed
    return username if token == str(created_at * 2026) else None

세션 값이 다음 형식으로 생성된다.

session = username.created_at*2026

서버에서 서명(secret key) 없이 단순 계산으로 세션을 검증하기 때문에
사용자가 세션을 직접 위조할 수 있다.

공격 과정

회원가입 후 /welcome 페이지 확인

/welcome 페이지에서 admin의 생성 시간 확인

10/03/2026, 14:15:43 UTC

시간을 Unix time으로 변환

1773152143

세션 값 계산

1773152143 * 2026 = 3592406241718

쿠키 session 값을 다음으로 변경

session=admin.3592406241718

/ 페이지 접속 시 admin으로 인식되어 flag가 출력된다.

Flag
DH{It_is_time_t0_s1eep~_~}
