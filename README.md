# OSVcopy

**DJI Osmo 360, Insta360 X 시리즈** 등에서 나온 `.OSV`, `.INSV` 등을 포함해 미디어를 **촬영 날짜** 기준으로 정리하는 macOS용 **importer**입니다.  
Lightroom 스타일 폴더(`YYYY-MM-DD` 또는 `YYYY/YYYY-MM-DD`)에 **복사** 또는 **이동**합니다.

[![CI](https://github.com/devuterian/OSVcopy/actions/workflows/ci.yml/badge.svg)](https://github.com/devuterian/OSVcopy/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 설치하기

1. [Releases](https://github.com/devuterian/OSVcopy/releases)에서 **OSVcopy-1.0.0.dmg** 를 받습니다.
2. DMG를 열고 **OSVcopy.app** 을 **응용 프로그램** 폴더로 드래그합니다.
3. 첫 실행 시 **시스템 설정 → 개인 정보 보호 및 보안**에서 “확인 없이 열기”가 필요할 수 있습니다. (Apple Developer 서명 없음)

**선택:** 파일명에 날짜가 없을 때 메타데이터로 날짜를 잡으려면 [Homebrew](https://brew.sh/)로 `ffmpeg`(`ffprobe`)를 설치하세요.

```bash
brew install ffmpeg
```

---

## 쓰는 법

1. 앱을 실행합니다.
2. **대상 라이브러리 폴더**를 고릅니다. (예: SMB로 마운트한 NAS 경로)
3. **폴더 구조**, **복사 / 이동**, **미리보기만**, **숨김 폴더까지 스캔**을 설정합니다.
4. 정리할 파일·폴더를 **드래그**하거나 추가한 뒤 실행합니다.

**팁:** 같은 이름의 파일이 이미 있으면 **MD5**로 비교해, 내용이 같으면 건너뜁니다. Dock 아이콘에 진행이 표시되고, 완료 시 알림을 보낼 수 있습니다.

---

## 지원하는 것

| 구분 | 예시 |
|------|------|
| 확장자 | `.OSV`, `.INSV`, `.MP4`, `.MOV`, `.JPG`, `.ARW`, `.DNG` 등 |
| 스캔 | 폴더를 넣으면 **하위 전체**를 재귀 스캔 |
| 날짜 | 파일명 패턴 → `ffprobe` creation_time → 생성일/수정일 순 |

---

## 한계·주의

- **Lightroom / 공식 편집기 대체**가 아닙니다. 라이브러리로 **가져오기·폴더 정리**에 가깝습니다.
- 네트워크 볼륨은 속도·안정성이 환경에 따라 다릅니다.
- `ffprobe`가 없으면 일부 파일은 날짜 추론이 약해질 수 있습니다.

---

## 빌드 (소스)

```bash
git clone https://github.com/devuterian/OSVcopy.git
cd OSVcopy
swift build -c release
```

`.app` 번들:

```bash
./build_osvcopy_app.sh
```

릴리즈용 DMG:

```bash
./scripts/build_release_dmg.sh
```

자세한 기여 방법은 [CONTRIBUTING.md](CONTRIBUTING.md)를 보세요.

---

## 기여·이슈

이슈와 PR을 환영합니다. [CONTRIBUTING.md](CONTRIBUTING.md)

---

## 라이선스

[MIT](LICENSE)

---

문서·저장소 운영 시 [LPFchan/repo-template](https://github.com/LPFchan/repo-template)을 참고했습니다. README 구성은 [devuterian/killeverybody](https://github.com/devuterian/killeverybody)처럼 **짧은 단계**로 맞추었습니다.
