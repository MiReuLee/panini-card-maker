# Panini Card Maker

내 사진으로 파니니 감성 스포츠 트레이딩 카드를 만들고, **브라우저에 로컬 저장**(IndexedDB)해 언제든 다시 편집·내보낼 수 있는 단일 HTML 웹앱입니다.

[pokecardmaker.net](https://pokecardmaker.net/create) 의 "폼 입력 → 실시간 프리뷰 → 이미지 다운로드" 패턴을 스포츠 카드에 적용했습니다.

## 사용법

별도 빌드·서버 없이 `index.html` 을 브라우저로 열면 바로 동작합니다.

```bash
open index.html        # macOS
# 또는 정적 서버
python3 -m http.server
```

## 주요 기능

- 🎨 **실시간 카드 에디터** — 사진 업로드, 선수명·포지션·등번호·팀·시즌·스탯 입력
- 🏅 **종목/레어도 테마** — 축구·농구·야구 / Base · Silver · Gold · Holo
- 💾 **로컬 저장 (IndexedDB)** — 카드 저장 / 갤러리 / 불러와 편집 / 복제 / 삭제
- ⏳ **자동 임시저장** — 새로고침해도 작업 내용 유지
- 🖼️ **PNG 다운로드** — 만든 카드를 이미지로 내보내기
- 🔄 **백업(JSON) 내보내기/가져오기** — 서버 없이 기기 간 데이터 이전

## 기술

- HTML5 Canvas (렌더링 + `toBlob` 내보내기)
- IndexedDB (이미지 Blob 포함 로컬 영속화)
- 의존성 없는 단일 파일 (Vanilla JS)

## 데이터 모델

```
DB: paniniCardMaker
├─ store: cards (keyPath: id)
│   { id, name, sport, rarity, fields{...},
│     imageBlob, thumbBlob, createdAt, updatedAt }
└─ store: draft (keyPath: id="current")   # 자동 임시저장
```

## 로드맵 (아이디어)

- 사진 위치/줌 조절, 크롭
- 카드 뒷면 디자인
- 인쇄용 규격(54×86mm, 300dpi) 출력
- React + Vite 로 구조화

## 라이선스

MIT
