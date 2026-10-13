[GitHub Pages HTML5 업로드 및 배포 실습가이드.md](https://github.com/user-attachments/files/33360591/GitHub.Pages.HTML5.md)
# GitHub Pages를 이용한 HTML5 웹사이트 업로드 및 배포 실습

**실습 환경:** Google Chrome 브라우저, GitHub 계정, HTML5 파일  
**실습 목표:** 개인 PC에서 작성한 HTML5 파일을 GitHub 클라우드 저장소에 업로드하고, 인터넷 주소(URL)를 생성하여 누구나 웹브라우저에서 접속할 수 있도록 웹사이트를 배포한다.

---

## 1. GitHub Pages 개념

**GitHub Pages**는 GitHub 저장소(Repository)에 저장된 HTML, CSS, JavaScript 등의 정적 웹 파일을 인터넷에 공개할 수 있도록 제공하는 웹 호스팅 서비스이다.

별도의 웹 서버를 설치하거나 관리할 필요 없이 Chrome 브라우저에서 GitHub에 로그인한 다음 파일을 업로드하고 배포 설정을 완료하면 웹사이트 주소를 생성할 수 있다.

GitHub 무료 계정에서도 공개 저장소(Public Repository)를 이용하여 GitHub Pages를 사용할 수 있다.

### 1.1 GitHub와 GitHub Pages의 차이

| 구분 | GitHub | GitHub Pages |
|---|---|---|
| 주요 역할 | 소스코드와 파일 저장 및 버전 관리 | 정적 웹사이트 배포 |
| 주요 파일 | HTML, CSS, JS, 소스코드 등 | HTML, CSS, JS, 이미지 등 |
| 접근 방법 | GitHub 계정으로 저장소 관리 | 일반 인터넷 주소로 접속 |
| 웹페이지 실행 | 코드 저장 및 미리보기 | 브라우저에서 웹페이지 표시 |
| 무료 사용 | 가능 | 공개 저장소에서 가능 |

### 1.2 전체 배포 과정

```text
① 로컬 PC
   HTML5 · CSS3 · JavaScript 파일 준비
                │
                ▼
   Chrome 브라우저에서 파일 업로드
                │
                ▼
② GitHub 저장소(Repository)
   파일 저장 및 변경 이력 관리
                │
                ▼
   Settings → Pages → 배포 설정
                │
                ▼
③ GitHub Pages 웹사이트
   https://username.github.io/html5-practice/
   다른 사용자도 URL로 접속 가능
```

---

## 2. 실습 전에 준비할 파일

먼저 PC에서 HTML5 웹페이지를 하나 작성한다.

### 2.1 HTML5 실습 코드

다음 코드를 VS Code 또는 텍스트 편집기에 작성한 후 **`index.html`**이라는 파일 이름으로 저장한다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, initial-scale=1.0">

    <title>GitHub Pages 실습</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f2f5fa;
            text-align: center;
            padding: 60px 20px;
        }

        .container {
            max-width: 600px;
            margin: auto;
            padding: 40px;
            background: white;
            border-radius: 12px;
            box-shadow: 0 4px 16px #cccccc;
        }

        h1 {
            color: #2457a7;
        }

        button {
            background: #2457a7;
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 6px;
            cursor: pointer;
        }
    </style>
</head>

<body>

    <div class="container">

        <h1>GitHub Pages 웹사이트</h1>

        <p>HTML5 클라우드 웹 배포 실습입니다.</p>

        <p id="message">버튼을 클릭하세요.</p>

        <button onclick="showMessage()">
            실행하기
        </button>

    </div>

    <script>
        function showMessage() {
            document.getElementById("message").innerText =
                "GitHub Pages에서 JavaScript 실행 성공!";
        }
    </script>

</body>
</html>
```

이 예제는 HTML5 문서 구조, CSS3 스타일, JavaScript 이벤트 처리를 하나의 파일에 포함한 형태이다. 별도의 CSS 또는 JavaScript 파일을 생성하지 않아도 웹사이트를 배포할 수 있다.

### 2.2 실습 파일 확인

PC에 다음과 같이 저장되어 있는지 확인한다.

```text
HTML5_Practice/
    |
    +-- index.html
```

**주의:** 파일 이름은 `index.html`로 작성하는 것이 좋다. GitHub Pages는 `index.html`, `index.md`, `README.md` 등을 시작 파일로 인식하며, 일반적인 HTML5 웹사이트에서는 `index.html`을 첫 화면으로 사용한다.

---

## 3. Chrome 브라우저에서 GitHub 로그인하기

**실습 단계 ①**

1. Chrome 브라우저를 실행한다.
2. 주소창에 [https://github.com](https://github.com)을 입력한다.
3. GitHub 홈페이지 오른쪽 위의 **Sign in**을 클릭한다.
4. GitHub 사용자 이름 또는 이메일 주소와 비밀번호를 입력한다.
5. 추가 인증이 요청되는 경우 인증 절차를 완료한다.
6. 로그인 후 GitHub 대시보드가 표시되는지 확인한다.

GitHub 계정이 없다면 **Sign up**을 선택해 무료 계정을 생성하고 이메일 인증까지 완료한다.

---

## 4. HTML5 파일을 저장할 Repository 생성

**실습 단계 ②**

Repository(저장소)는 HTML5, CSS3, JavaScript, 이미지 파일 등을 클라우드에 저장하고 관리하는 공간이다.

로그인한 GitHub 화면에서 다음 순서대로 진행한다.

1. 오른쪽 위의 **+** 아이콘을 클릭한다.
2. 메뉴에서 **New repository**를 선택한다. 직접 [저장소 생성 페이지](https://github.com/new)에 접속해도 된다.
3. 저장소 설정 화면에 아래 값을 입력한다.
4. 설정을 확인하고 **Create repository**를 클릭한다.

### 4.1 New repository 설정 예시

| 설정 항목 | 입력 또는 선택 내용 |
|---|---|
| Owner | 자신의 GitHub 계정 |
| Repository name | `html5-practice` |
| Description (선택) | HTML5 웹사이트 배포 실습 |
| Repository visibility | **Public** (무료 Pages 배포에 사용) |
| Add README | **On** (저장소 초기화) |

> 화면의 메뉴나 옵션 배치는 GitHub 인터페이스 변경에 따라 조금 다를 수 있다.

생성 버튼을 누르면 다음과 같은 저장소 주소가 만들어진다.

```text
https://github.com/username/html5-practice
```

여기서 `username`은 본인의 GitHub 사용자 이름을 의미한다.

이 주소는 **소스 파일을 보관하는 GitHub 저장소 주소**이며, 실제 웹사이트 배포 주소는 아니다.

---

## 5. HTML5 파일을 GitHub 저장소에 업로드

**실습 단계 ③**

앞에서 생성한 `html5-practice` 저장소 화면에서 진행한다.

1. 상단의 **Code** 탭을 클릭한다.
2. 파일 목록 위의 **Add file** 버튼을 클릭한다.
3. **Upload files**를 선택한다.
4. 파일 업로드 화면에서 **choose your files**를 클릭한다.
5. PC에 저장한 `index.html` 파일을 선택한다. 파일 또는 폴더를 업로드 영역에 드래그하여 넣을 수도 있다.
6. 업로드가 완료되면 화면 아래의 Commit message(변경 설명)에 `Add index.html`을 입력한다.
7. 실습에서는 변경 내용을 `main` 브랜치에 직접 저장하는 옵션을 선택한다.
8. **Commit changes**를 클릭한다. 화면 구성에 따라 변경 내용을 제안하는 버튼이 표시될 수도 있으므로, 최종적으로 `main` 브랜치에 파일이 저장되었는지 확인한다.

GitHub는 브라우저에서 파일을 직접 업로드하는 기능을 공식 지원한다.

### 5.1 업로드 완료 후 저장소 모습

```text
html5-practice
    |
    +-- README.md
    |
    +-- index.html
```

`index.html` 파일이 저장소 최상위 위치에 표시되면 업로드가 정상적으로 완료된 것이다.

파일을 클릭하면 HTML5 소스코드를 확인할 수 있다.

**중요:** GitHub에 파일을 업로드했다고 웹사이트 배포가 모두 끝나는 것은 아니다. 다음 단계에서 GitHub Pages 기능을 활성화해야 한다.

---

## 6. GitHub Pages 배포 설정

**실습 단계 ④**

GitHub Pages 기능을 활성화하여 HTML5 파일을 실제 웹사이트로 공개한다.

### 6.1 Pages 설정 화면 이동

저장소 화면의 상단 메뉴에서 다음 순서로 이동한다.

```text
html5-practice 저장소
    → Settings
        → Pages
            → Build and deployment
```

왼쪽 메뉴의 **Code, planning, and automation** 영역에서 **Pages**를 선택하면 배포 설정 화면이 표시된다.

### 6.2 배포 옵션 설정

| 항목 | 설정값 | 의미 |
|---|---|---|
| Source | **Deploy from a branch** | 브랜치 기반 배포 방식 |
| Branch | **main** | 업로드한 파일이 존재하는 브랜치 |
| Folder | **/(root)** | `index.html`이 있는 최상위 폴더 |

설정 순서:

1. **Source**에서 `Deploy from a branch`를 선택한다.
2. **Branch**에서 `main`을 선택한다.
3. 배포 폴더에서 `/(root)`를 선택한다.
4. **Save** 버튼을 클릭한다.

설정을 저장하면 GitHub Pages 배포 작업이 시작된다.

---

## 7. 배포 완료 및 웹사이트 주소 확인

**실습 단계 ⑤**

설정을 저장한 뒤 다시 **Settings → Pages** 화면을 확인한다.

배포가 완료되면 GitHub Pages 영역에서 공개된 웹사이트 주소를 확인하거나 **Visit site**를 클릭하여 사이트를 열 수 있다.

예를 들어 다음과 같다.

```text
https://username.github.io/html5-practice/
```

이 주소에서 `username`은 자신의 GitHub 사용자 이름으로 바꿔야 한다. 위 주소는 **형식 예시**이며, 실제 배포된 주소는 GitHub의 Pages 설정 화면에서 확인한다.

배포가 완료된 공개 사이트는 GitHub에 로그인하지 않은 다른 사용자도 접속할 수 있다.

배포 내용이 반영되는 데는 최대 약 10분이 걸릴 수 있다. 바로 페이지가 보이지 않는 경우 Pages 화면에서 배포 상태를 확인한다.

### 7.1 정상 작동 확인

Chrome 브라우저의 새 탭 또는 시크릿 창에서 배포 주소를 입력한다.

앞서 작성한 HTML5 코드가 정상적으로 배포되었다면 다음과 같은 내용이 표시된다.

```text
┌──────────────────────────────────────────┐
│                                          │
│        GitHub Pages 웹사이트              │
│                                          │
│    HTML5 클라우드 웹 배포 실습입니다.      │
│                                          │
│            버튼을 클릭하세요.             │
│                                          │
│              [실행하기]                  │
│                                          │
└──────────────────────────────────────────┘
```

**실행하기** 버튼을 클릭하면 표시 문장이 다음과 같이 변경된다.

```text
GitHub Pages에서 JavaScript 실행 성공!
```

버튼 클릭 시 메시지가 변경된다면 HTML5와 JavaScript가 브라우저에서 정상적으로 동작하는 것이다.

---

## 8. HTML5, CSS3, JavaScript 파일을 함께 업로드하는 방법

HTML5 웹사이트가 여러 파일로 구성되어 있는 경우에도 동일한 방법으로 배포할 수 있다.

예를 들어 다음과 같이 구성한다.

```text
html5-practice/
    |
    +-- index.html
    |
    +-- about.html
    |
    +-- css/
    |     +-- style.css
    |
    +-- js/
    |     +-- script.js
    |
    +-- images/
          +-- logo.png
```

이때 `index.html`에서는 CSS3와 JavaScript 파일을 상대경로로 연결해야 한다.

```html
<link rel="stylesheet" href="./css/style.css">

<script src="./js/script.js"></script>

<img src="./images/logo.png" alt="로고">

<a href="./about.html">소개 페이지</a>
```

저장소의 **Add file → Upload files**에서 여러 파일이나 폴더를 드래그하여 업로드할 수 있다. 업로드가 끝난 후 실제 저장소에서도 폴더 구조가 유지되었는지 확인한다.

상대경로를 사용하면 GitHub Pages의 프로젝트 주소 아래에서도 파일을 올바르게 불러올 수 있다.

### 8.1 파일별 접속 주소

GitHub 사용자 이름이 `username`, 저장소 이름이 `html5-practice`일 때의 주소 형식이다.

| 파일 | 웹사이트 접속 주소 |
|---|---|
| `index.html` | `https://username.github.io/html5-practice/` |
| `about.html` | `https://username.github.io/html5-practice/about.html` |
| `css/style.css` | `https://username.github.io/html5-practice/css/style.css` |
| `images/logo.png` | `https://username.github.io/html5-practice/images/logo.png` |

---

## 9. 배포한 HTML5 웹사이트 수정하기

**실습 단계 ⑥**

GitHub Pages는 기존 파일을 변경하여 저장하면 웹사이트를 다시 배포할 수 있다. 처음부터 저장소를 생성하거나 Pages를 다시 설정할 필요는 없다.

### 방법 A. GitHub 브라우저 화면에서 직접 수정

1. GitHub에 로그인하고 기존 저장소에 접속한다.
2. **Code** 탭에서 `index.html` 파일을 클릭한다.
3. 파일 화면 오른쪽의 연필 모양 아이콘인 **Edit this file**을 클릭한다.
4. HTML5 코드를 수정한다.
5. **Commit changes**를 클릭한다.
6. `main` 브랜치에 변경 사항을 저장한다.
7. Pages가 다시 배포한 후 기존 웹사이트 주소에서 수정된 내용을 확인한다.

### 방법 B. PC에서 수정한 파일을 다시 업로드

PC의 VS Code에서 파일을 수정했다면 다음과 같이 진행한다.

```text
Code → Add file → Upload files → 수정된 파일 업로드 → Commit changes
```

기존 파일과 이름 및 경로가 같은 파일을 업로드하면 변경 내용으로 저장할 수 있다. 파일을 변경할 때마다 GitHub가 변경 이력(Commit)을 기록하므로 이전 수정 내역도 확인할 수 있다.

---

## 10. GitHub Pages 주소의 두 가지 유형

GitHub Pages는 기본적으로 프로젝트별 웹사이트와 사용자 대표 웹사이트를 제공한다.

| 구분 | 프로젝트 웹사이트 | 사용자 대표 웹사이트 |
|---|---|---|
| 저장소 이름 | `html5-practice` | `username.github.io` |
| 주소 형식 | `username.github.io/html5-practice/` | `username.github.io/` |
| 용도 | 수업 실습, 개별 프로젝트 | 개인 홈페이지, 포트폴리오 |
| 개수 | 저장소별로 생성 가능 | 계정당 하나 |

수업에서 학생별로 여러 HTML5 실습 결과를 제출하거나 배포하려는 경우에는 **프로젝트 웹사이트 방식**을 권장한다.

예를 들어 `html5-week01`, `html5-week02`, `html5-final`이라는 저장소를 각각 생성하면 서로 다른 세 개의 실습 사이트를 관리할 수 있다.

---

## 11. GitHub Pages 배포 시 자주 발생하는 오류

| 문제 | 원인 및 해결 방법 |
|---|---|
| 404 Page Not Found | Pages 배포가 완료되었는지, 주소가 올바른지 확인 |
| 첫 화면이 표시되지 않음 | `index.html`이 배포 폴더의 최상위에 있는지 확인 |
| HTML만 표시되고 CSS가 적용되지 않음 | CSS 파일 경로와 대소문자 확인 |
| 이미지가 보이지 않음 | 이미지 파일 업로드 여부 및 상대경로 확인 |
| JavaScript가 동작하지 않음 | Chrome 개발자 도구(F12)의 Console 오류 확인 |
| 수정한 내용이 표시되지 않음 | 재배포 완료 여부 확인 후 새로고침 또는 캐시 확인 |
| Pages 설정이 안 됨 | 공개 저장소 설정과 브랜치 존재 여부 확인 |

특히 파일 이름은 대소문자를 구분한다. `Index.html`이나 `INDEX.HTML`이 아닌 정확한 `index.html`로 작성하는 것이 중요하다.

배포 실패 원인을 자세히 확인하려면 저장소의 **Actions** 탭에서 Pages 배포 작업의 실행 결과를 확인한다.

---

## 12. GitHub Pages의 기술적 특징과 제한 사항

| 항목 | 지원 여부 |
|---|---|
| HTML5 웹페이지 | 지원 |
| CSS3 스타일 | 지원 |
| JavaScript 실행 | 지원 |
| 이미지 및 정적 콘텐츠 | 지원 |
| Three.js를 활용한 3D 웹페이지 | 지원 |
| PHP, JSP 등의 서버 측 실행 | 직접 지원하지 않음 |
| Node.js 서버 상시 실행 | 직접 지원하지 않음 |
| GitHub 계정 없이 공개 페이지 접속 | 가능 |

GitHub Pages는 정적 웹사이트 호스팅 서비스이므로 브라우저에서 동작하는 HTML5, CSS3, JavaScript 프로그램에 적합하다. 서버 프로그램이나 데이터베이스가 필요한 서비스는 별도의 백엔드와 연계해야 한다.

파일 업로드 및 운영에도 제한이 있다. 브라우저에서 파일을 업로드하는 경우 파일당 최대 25MiB, 한 번에 최대 100개 파일을 업로드할 수 있으며, GitHub Pages의 게시 사이트 크기 제한은 1GB이다. 세부 제한은 GitHub 정책 변경에 따라 달라질 수 있다.

공개 저장소와 웹사이트에는 개인정보, 비밀번호, 비밀 API 키를 업로드해서는 안 된다.

---

## 13. 실습 완료 확인

다음 항목을 확인하면 실습을 완료한 것이다.

- [ ] Chrome에서 GitHub 계정으로 로그인하였다.
- [ ] Public 저장소 `html5-practice`를 생성하였다.
- [ ] `index.html` 파일을 저장소에 업로드하였다.
- [ ] Settings → Pages에서 `main / (root)`를 설정하였다.
- [ ] GitHub Pages에서 배포 주소를 확인하였다.
- [ ] 배포 URL을 Chrome에서 열어 웹페이지를 확인하였다.
- [ ] 버튼을 클릭하여 JavaScript 실행 결과를 확인하였다.

---

## 14. 공식 참고자료

- [GitHub Pages 빠른 시작 안내](https://docs.github.com/ko/pages/quickstart)
- [GitHub Pages 배포 소스 설정](https://docs.github.com/ko/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
- [GitHub Pages 404 오류 해결 방법](https://docs.github.com/ko/pages/getting-started-with-github-pages/troubleshooting-404-errors-for-github-pages-sites)

---

## 최종 정리

Chrome에서 GitHub에 로그인한 후 `Public` 저장소를 생성하고, `index.html`을 업로드한 다음 다음과 같이 설정하면 HTML5 웹사이트를 인터넷 주소로 공개할 수 있다.

```text
Settings → Pages → Deploy from a branch → main → /(root) → Save
```

별도 서버 설치나 Git 명령어를 사용할 필요가 없다.
