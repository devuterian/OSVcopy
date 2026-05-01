# Contributing to OSVcopy

이 저장소는 [LPFchan/repo-template](https://github.com/LPFchan/repo-template)의 **운영 모델**을 그대로 따릅니다.  
템플릿 README의 Getting Started에 나온 것처럼, **정책의 원문**은 `records/REPO.md`에 있고, 에이전트 진입점은 `AGENTS.md`입니다. **CONTRIBUTING.md**는 사람 기여자가 맨 먼저 읽을 **실행 체크리스트** 역할입니다.

> Canonical policy: [`records/REPO.md`](records/REPO.md)  
> Agent entry: [`AGENTS.md`](AGENTS.md)  
> Product truth: [`records/SPEC.md`](records/SPEC.md)

---

## 1. 클론 직후 한 번만

```bash
git clone https://github.com/devuterian/OSVcopy.git
cd OSVcopy
sh scripts/install-hooks.sh
```

`install-hooks.sh`는 `core.hooksPath`를 **`.githooks`** 로 맞춥니다. 이후 **일반 커밋**은 아래 절차를 따르지 않으면 로컬에서 거절됩니다.

---

## 2. 기여 전에 읽을 것 (순서 권장)

1. [`records/REPO.md`](records/REPO.md) — 서피스 분리, `LOG-*` 규약, 역할, 라우팅
2. [`AGENTS.md`](AGENTS.md) — 스킬 트리거 표, 규칙 요약
3. [`skills/README.md`](skills/README.md) — 스킬 디렉터리 안내
4. (제품 변경 시) [`records/SPEC.md`](records/SPEC.md), [`records/STATUS.md`](records/STATUS.md)

`SPEC` / `STATUS` / `PLANS`는 템플릿 규칙상 **오케스트레이터·운영자**가 갱신하는 것이 기본입니다. 워커 에이전트는 PR 본문·이슈로 **제안**하고, 머지 시 정리하는 편이 안전합니다.

---

## 3. 일반 커밋 (거의 항상 이것)

repo-template 규약: **손으로 `git commit -m "..."` 하지 않습니다.**  
스켈레톤 생성기가 `LOG-*` id를 등록하고, 본문에 `timestamp` / `changes` / `rationale` / `checks` 와 `project` / `agent` / `role` / `commit` 트레일러를 요구합니다.

```bash
# 예: 에이전트 id는 본인 환경에 맞게 (영숫자 정규화 후 최대 6자 접미사가 LOG id에 붙음)
sh scripts/new-commit-message.sh \
  --subject "fix: describe change" \
  --agent yourid \
  --project osvcopy \
  --role worker

# 출력된 경로의 파일을 연다 (기본은 .tmp_commit_msg_* under repo root)
# TODO 로 채워진 changes / rationale / checks 를 실제 내용으로 고친 뒤:

sh scripts/check-commit-standards.sh .tmp_commit_msg_fix_....txt
git commit -F .tmp_commit_msg_fix_....txt
```

- **`--project osvcopy`**: 로컬 폴더 이름이 `osvcopy`가 아닐 때도 트레일러는 저장소 id와 맞추는 것이 좋습니다 (`records/REPO.md` Local Divergence 참고).
- **`AGENT_ID` 환경 변수**를 쓰면 `--agent` 생략 시 기본값으로 들어갑니다.

PR이 열리면 GitHub Actions의 **Commit Standards** 워크플로가 같은 규칙으로 커밋 범위를 다시 검사합니다.

---

## 4. 예외 커밋 (bootstrap / migration)

템플릿에 정의된 대로, **저장소 부트스트랩·대규모 마이그레이션**만 예외로 인정됩니다.  
커밋 메시지 **어느 줄이든** 아래 형태가 보여야 합니다 (대소문자 무시).

- 첫 줄이 `migration` 또는 `bootstrap`으로 시작하고 `exception`이 포함되거나,
- `exception: migration` / `exception: bootstrap` 형태의 줄

예시 첫 줄:

```text
migration exception: bulk import repo-template scaffold
```

이 경로는 남용하면 CI·리뷰에서 걸러지므로, **정말 예외일 때만** 사용하세요.

---

## 5. 제품 빌드·릴리즈 (Swift)

```bash
swift build -c release
./build_osvcopy_app.sh
./scripts/build_release_dmg.sh
```

- 아이콘: 기본은 `Bundle/OSVcopy.icns`. 바꿀 때는 `ICNS_SRC=/path/to/icon.icns ./build_osvcopy_app.sh`
- 산출물: `dist/OSVcopy.app`, `dist/OSVcopy-<version>.dmg` (버전은 `Bundle/Info.plist`의 Short Version String)

---

## 6. PR 체크리스트

- [ ] `main` 기준으로 **Commit Standards** + **CI** (`swift build -c release`)가 통과할 것
- [ ] 사용자에게 보이는 동작 변경이면 `README.md` 또는 `records/SPEC.md` 반영을 제안했거나 포함했을 것
- [ ] 의미 있는 아키텍처·제품 결정이면 `records/decisions/`에 `DEC-*` 초안을 제안할 것 (형식은 해당 디렉터리 `README.md` 준수)

---

## 7. Upstream

이 포크/프로젝트는 **외부 upstream Git 트래킹**이 없습니다. `records/upstream-intake/`는 템플릿과의 **디렉터리 정합**을 위해 두었으며, upstream을 두게 되면 `records/upstream-intake/README.md`를 따라 활성화하면 됩니다.

---

## 8. English summary

This repo adopts [LPFchan/repo-template](https://github.com/LPFchan/repo-template): canonical policy in [`records/REPO.md`](records/REPO.md), agent entry in [`AGENTS.md`](AGENTS.md), commit contract enforced by `.githooks` + [`scripts/new-commit-message.sh`](scripts/new-commit-message.sh) + CI. Run `sh scripts/install-hooks.sh` after clone; use **migration/bootstrap exception** commits only for rare scaffolding per template rules.
