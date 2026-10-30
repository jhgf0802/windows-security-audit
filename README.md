# Windows Security Audit

윈도우 시스템의 보안 설정을 자동으로 점검하고 결과를 리포트로 출력하는 PowerShell 기반 감사 스크립트입니다.

## 주요 기능

- 계정 및 암호 정책 점검 (암호 길이, 복잡도, 만료 기간, 잠금 정책)
- 로컬 사용자 계정과 Administrators 그룹 점검
- 공유 폴더 및 접근 권한 점검
- 불필요한 서비스와 취약한 포트 점검
- 방화벽, Windows Update, 감사 로그 설정 점검
- 점검 결과를 HTML / CSV 리포트로 저장

## 요구 사항

- Windows 10 / 11, Windows Server 2016 이상
- PowerShell 5.1 이상
- 관리자 권한으로 실행

## 사용 방법

```powershell
git clone https://github.com/jhgf0802/windows-security-audit.git
cd windows-security-audit

# 관리자 권한 PowerShell에서 실행
powershell -ExecutionPolicy Bypass -File .\Invoke-Audit.ps1
```

## 출력

실행 시 `reports` 폴더에 타임스탬프가 포함된 리포트가 생성됩니다.

```text
reports/
├─ audit-20261030-153000.html
└─ audit-20261030-153000.csv
```

## 점검 항목

| 구분 | 점검 내용 |
|---|---|
| 계정 | 암호 정책, 계정 잠금 정책, 로컬 계정 목록 |
| 권한 | Administrators 그룹 구성원, 공유 폴더 권한 |
| 서비스 | 불필요한 서비스 실행 여부, 자동 시작 서비스 |
| 네트워크 | 방화벽 상태, 열려 있는 포트 |
| 시스템 | Windows Update 설정, 감사 정책, 보안 로그 |

## 안전 수칙

- 이 스크립트는 **읽기 전용 감사**만 수행하며 시스템 설정을 변경하지 않습니다.
- 승인된 테스트 환경 또는 본인 소유의 시스템에서만 실행합니다.
- 비밀번호, 제품 키 등 민감한 값은 리포트에 기록하지 않습니다.

## 프로젝트 구조

```text
windows-security-audit/
├─ README.md
├─ Invoke-Audit.ps1   # 감사 실행 스크립트
├─ checks/            # 점검 항목별 모듈
└─ reports/           # 감사 결과 리포트
```

## 라이선스

MIT License
