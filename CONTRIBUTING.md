# Contributing to OSVcopy

감사합니다. 이슈·PR 모두 환영합니다.

## 빌드

```bash
cd /path/to/OSVcopy
swift build -c release
```

앱 번들(로컬):

```bash
./build_osvcopy_app.sh
```

DMG(릴리즈용):

```bash
./scripts/build_release_dmg.sh
```

`ICNS_SRC` 환경 변수로 아이콘 `.icns` 경로를 바꿀 수 있습니다 (`build_osvcopy_app.sh` 참고).

## 코드 스타일

- Swift 5.10+, macOS 13+ 타깃을 유지해 주세요.
- PR은 한 가지 목적에 집중하면 리뷰가 빨라집니다.

## 저장소 운영 참고

문서·오픈소스 골격은 [LPFchan/repo-template](https://github.com/LPFchan/repo-template)을 참고했습니다. (전체 스캐폴드·커밋 훅은 이 프로젝트에는 넣지 않았습니다.)
