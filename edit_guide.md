# 도원시스템 홈페이지 관리 및 유지보수 가이드 (Site Guide)

이 가이드는 홈페이지의 코드 직접 수정(글자, 사진 교체), **메뉴 추가(제품소개, 시공후기)** 방법, 그리고 **신규 제품 추가** 방법을 설명합니다.

---

## 📂 1. 텍스트 및 사진 교체 방법 (HTML 수정)

홈페이지의 각 요소는 표준 HTML 파일(`index.html`, `about.html`, `products.html`)로 이루어져 있어, 메모장이나 VS Code 등의 텍스트 에디터로 열어 손쉽게 텍스트나 이미지 경로를 수정할 수 있습니다.

### ✍️ 텍스트 수정하기
- 수정할 페이지의 HTML 파일을 에디터로 엽니다.
- 변경하고 싶은 문구(예: 전화번호 `010-3819-6610`, 대표자명 등)를 찾아서 텍스트를 고친 후 저장합니다.

### 🖼️ 사진 교체하기
1. 준비한 이미지 파일(예: `new-banner.jpg`)을 프로젝트 폴더 내의 `images/` 폴더에 복사합니다.
2. 교체할 위치의 HTML 파일에서 `<img src="images/old-banner.png" ...>` 태그를 찾습니다.
3. `src` 속성의 경로를 새로 복사한 이미지 파일명(`images/new-banner.jpg`)으로 변경하고 저장합니다.

### 🖼️ 권장 사진 규격 정보
| 이미지 위치 | 권장 비율 / 크기 | 추천 내용 |
| :--- | :--- | :--- |
| **메인/서브 히어로 배경** | `16:9` 비율 (`1920x1080` 이상) | 시스템 에어컨이 설치된 거실/사무실 인테리어 또는 깔끔한 천장 공조 사진 |
| **제품 카탈로그 카드** | `4:3` 비율 (`800x600` 권장) | 브랜드별 천장형/스탠드형 실내기 컷 및 순정 기판/압축기 세부 컷 |
| **회사소개 CEO 인사말 옆** | 세로형 또는 `1:1` (`800x1000` 권장) | 대표이사 프로필 사진 또는 신뢰감을 주는 엔지니어링 작업 실측 모습 |

---

## 🛠️ 2. 제품소개 및 시공후기 메뉴 추가 방법

이미 `product-intro.html` (제품소개)과 `reviews.html` (시공후기) 파일이 완벽히 설계되어 저장되어 있습니다. 이 메뉴들을 상단 헤더와 하단 푸터에 활성화하려면 주석만 제거해 주시면 됩니다.

### Step 1: 상단 헤더 메뉴 주석 해제
각 HTML 파일의 코드 **상단 헤더(Header)** 영역에서 아래와 같이 작성된 코드를 찾습니다.

```html
<!-- <li><a href="product-intro.html" class="nav-link" id="nav_prod_intro">제품소개</a></li> -->
<!-- <li><a href="reviews.html" class="nav-link" id="nav_reviews">시공후기</a></li> -->
```

이를 주석 기호(`<!--`와 `-->`)를 제거하여 아래와 같이 활성화합니다.

```html
<li><a href="product-intro.html" class="nav-link" id="nav_prod_intro">제품소개</a></li>
<li><a href="reviews.html" class="nav-link" id="nav_reviews">시공후기</a></li>
```

### Step 2: 하단 푸터 메뉴 주석 해제
각 HTML 파일 코드 아래쪽의 **푸터(Footer)** 영역으로 이동하여 아래 코드를 찾아 주석 기호를 지워줍니다.

```html
<!-- <li><a href="product-intro.html">제품소개</a></li> -->
<!-- <li><a href="reviews.html">시공후기</a></li> -->
```

이를 아래와 같이 활성화합니다.

```html
<li><a href="product-intro.html">제품소개</a></li>
<li><a href="reviews.html">시공후기</a></li>
```

---

## 🛒 3. 제품판매 페이지에 새로운 제품 추가하는 방법

`products.html` 파일에 새로운 제품 카드를 코드 상에서 직접 추가하는 방법입니다.

1. `products.html` 파일 내부에서 `<div class="grid-container">` 영역 아래의 `<div class="grid-card">...</div>` 블록을 통째로 복사합니다.
2. 아래에 이어서 붙여넣기 한 뒤, 새로 삽입한 블록 안의 텍스트와 이미지 경로를 수정합니다.

```html
<!-- 제품 카드 구조 예시 -->
<div class="grid-card">
  <div class="grid-card-img-box">
    <img src="images/새이미지파일명.png" alt="제품명" class="grid-card-img">
  </div>
  <div class="grid-card-body">
    <h3 class="grid-card-title">제품명</h3>
    <p class="grid-card-desc">제품에 대한 상세 설명을 입력하세요.</p>
    <div class="grid-card-specs">
      <span class="spec-item">주요 스펙 1</span>
      <span class="spec-value">스펙 값 1</span>
    </div>
    <div class="grid-card-specs" style="border-top: none; padding-top: 5px;">
      <span class="spec-item">주요 스펙 2</span>
      <span class="spec-value">스펙 값 2</span>
    </div>
  </div>
</div>
```

---

## 💡 팁: 새로운 세부 페이지를 하나 더 만들고 싶을 때
기존의 서브 페이지(예: `about.html` 또는 `product-intro.html`)를 복사하여 파일 이름만 새로 변경하세요. 그 후 헤더/푸터 네비게이션 메뉴에 해당 파일 경로를 연결(a href)하면 손쉽게 페이지를 추가할 수 있습니다.
