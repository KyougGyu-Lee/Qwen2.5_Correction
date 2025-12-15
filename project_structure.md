# Qwen2.5_Correction Project Structure

```
Qwen2.5_Correction/
├── data/
│   ├── org_data/
│   │   └── evaluate_dataset.json          # 평가 데이터 (30개)
│   ├── response_data/
│   │   ├── lora_normal_response.json      # LoRA 모델 평가 결과
│   │   ├── vanilla_normal_response.json   # 0.5B 모델 평가 결과
│   │   ├── vanilla_normal_response_7B.json # 7B 모델 평가 결과
│   │   └── vanilla_normal_response_v2.json
│   └── train_data/
│       └── train_dataset.json             # 학습 데이터 (50개)
│
├── lora_Qwen2.5/
│   ├── merged_model/                      # LoRA 학습 후 병합된 모델
│   │   ├── config.json
│   │   ├── generation_config.json
│   │   ├── tokenizer.json
│   │   ├── tokenizer_config.json
│   │   ├── vocab.json
│   │   ├── special_tokens_map.json
│   │   └── added_tokens.json
│   ├── checkpoints/                       # 학습 체크포인트
│   └── scripts/
│       ├── Qwen2.5-0.5B_w.o_noerror.py   # LoRA 학습 스크립트
│       ├── Qwen2.5_lora_eval.py          # LoRA 모델 평가 스크립트
│       └── wandb/                         # Wandb 로그
│
├── vanilla/
│   └── scripts/
│       ├── Qwen2.5_org.py                # 원본 평가 스크립트 (No Error O)
│       └── Qwen2.5_org_copy.py           # 원본 평가 스크립트 (No Error X)
│
└── project_structure.md                   # 프로젝트 구조 문서
```

## 파일 설명

### 데이터
| 파일 | 설명 |
|-----|------|
| `evaluate_dataset.json` | 6가지 오류 유형별 5개씩 총 30개 평가 샘플 |
| `train_dataset.json` | LoRA 학습용 50개 샘플 |

### 스크립트
| 파일 | 용도 |
|-----|------|
| `Qwen2.5-0.5B_w.o_noerror.py` | Qwen2.5-0.5B LoRA 파인튜닝 |
| `Qwen2.5_lora_eval.py` | LoRA 모델 평가 |
| `Qwen2.5_org.py` | Vanilla 모델 평가 (No Error 옵션 포함) |
| `Qwen2.5_org_copy.py` | Vanilla 모델 평가 (No Error 없음) |

## 오류 유형 (6가지)
1. Arithmetic/Total Inconsistency - 산술/총합 불일치
2. Unit/Measurement Mismatch - 단위/측정 불일치
3. Temporal Order/Duration Inconsistency - 시간 순서/기간 불일치
4. Spatial Relation Inconsistency - 공간 관계 불일치
5. Pronoun/Referent Ambiguity - 대명사/지시 대상 모호성
6. Action-Agent/Object Mismatch - 행위-행위자/대상 불일치
