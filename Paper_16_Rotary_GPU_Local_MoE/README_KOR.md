# Paper 16 - Rotary GPU

**소비자용 8GB VRAM 장치에서 대형 MoE 모델을 로컬 실행하기 위한 공개 검증 패키지**

**Rotary GPU는 모델이 아닙니다.**  
Rotary GPU는 대형 MoE 언어 모델을 일반 노트북급 장치에 더 가깝게 가져오기 위한 로컬 실행 검증입니다.

이 공개 패키지는 사용자가 직접 준비한 대형 MoE GGUF 모델을 로컬 장치에서 실행해보는 데 필요한 최소 구성만 제공합니다. 이번 검증에서는 Qwen 3.6 계열 35B-A3B MoE GGUF 모델을 하나의 검증 타깃으로 사용했습니다.

모델 가중치는 이 저장소에 포함되어 있지 않습니다. 사용자는 공식 또는 허용된 출처에서 모델 파일을 직접 받아야 합니다.

## 구성

| 파일 | 설명 |
|---|---|
| `Paper_16_Rotary_GPU_Local_MoE.tex` | 공개 기술 노트 LaTeX 원문 |
| `anima-run.exe` | Rotary GPU 데모 CLI 실행 파일 |
| `README.md` | 영어 사용 설명서 |
| `README_KOR.md` | 한국어 사용 설명서 |
| `EXECUTIVE_SUMMARY.md` | 공개 요약 |
| `LIMITATIONS.md` | 한계와 주의사항 |
| `RELEASE_MANIFEST.md` | 배포 구성과 제외 항목 |
| `CHECKSUMS.txt` | SHA-256 체크섬 |

## 무엇을 보여주는가

- Rotary GPU 로컬 실행 개념
- 사용자가 직접 준비한 대형 MoE GGUF 모델 실행
- 8GB VRAM 소비자용 노트북 GPU 환경에서의 검증
- 일반 응답 모드와 thinking 모드
- 짧은 내부 smoke set 기준 10/10 통과
- 공개 보수 기준 20+ tokens/s
- warm 상태 decode-only 측정에서 30+ tokens/s 관측

이 패키지는 모델 배포가 아니라 **공개 검증 패키지**입니다.

## 요구 사항

- Windows 11
- NVIDIA RTX 계열 8GB VRAM급 GPU 또는 호환 환경
- 권장 32GB 시스템 메모리
- 모델 파일 저장을 위한 약 20GB 이상 여유 공간
- 사용자가 직접 받은 compatible GGUF 검증 모델
- 로컬 OpenAI 호환 inference server 실행 파일  
  예: `llama-server.exe`

`llama-server.exe`는 `PATH`에 두거나, `LLAMA_SERVER_PATH` 환경 변수로 전체 경로를 지정하면 됩니다.

## 빠른 실행

### 1. 모델 준비

공식 또는 허용된 출처에서 compatible GGUF 검증 모델을 받습니다.

예시 경로:

```text
D:\models\Qwen3.6-35B-A3B.gguf
```

### 2. 최초 설정

처음 한 번만 실행합니다.

```powershell
.\anima-run.exe --setup --model "D:\models\Qwen3.6-35B-A3B.gguf"
```

이 과정은 현재 사용자 환경에 필요한 작은 로컬 실행 데이터를 준비합니다. 모델 가중치를 복사하거나 재배포하지 않습니다.

### 3. 일반 응답 실행

```powershell
.\anima-run.exe --model "D:\models\Qwen3.6-35B-A3B.gguf" --prompt "Hello" --thinking off
```

### 4. Thinking 모드 실행

```powershell
.\anima-run.exe --model "D:\models\Qwen3.6-35B-A3B.gguf" --prompt "Think through this problem." --thinking on
```

### 5. 벤치마크 실행

```powershell
.\anima-run.exe --model "D:\models\Qwen3.6-35B-A3B.gguf" --bench
```

성공 시 대략 다음 형태를 확인할 수 있습니다.

```text
pass_rate: 1.0
metric_source: timings_api
```

## 포함하지 않는 것

이 저장소에는 다음이 포함되지 않습니다.

- 모델 가중치
- 학습 데이터
- 모델 재배포 파일
- 내부 구현 세부사항
- 비공개 검증 자료
- 비공개 빌드 자료

## 참고

첫 설정 또는 첫 서버 시작은 몇 분 정도 걸릴 수 있습니다. 모델이 이미 준비된 warm 상태에서는 이후 실행이 더 빠를 수 있습니다.

이 공개 패키지는 사용자가 직접 실행해볼 수 있는 최소 인터페이스만 제공합니다. 내부 구현 방식은 공개 범위에 포함하지 않습니다.

## 특허 관련 안내

이 공개 검증은 저자가 이미 출원한 지식재산 방향과 관련되어 있습니다. 이 저장소는 내부 구현 공개가 아니라, 외부에서 관찰 가능한 검증 결과와 사용 흐름을 제공하기 위한 패키지입니다.

## 저자

조명준  
Myeong Jun Jo
