# YOLO를 활용한 손상된 보도블록 탐지

손상된 보도블록을 4개 클래스(pothole·crack·gap·asphalt)로 탐지하는 YOLO11n 객체 탐지 모델 (이미지분석 수업 개인 프로젝트).
Roboflow로 **1,018장 직접 라벨링**(Train 698 / Valid 215 / Test 105) 후 100 epoch 학습.
위험 클래스 탐지 시 소리로 안내하는 보행 보조 활용안을 제시했습니다.

프로젝트 상세 → [Notion 포트폴리오](노션 링크)

## 클래스
| 클래스 | 정의 |
|---|---|
| pothole | 보도블록 중 파진 부위 |
| crack | 깨진 보도블록 |
| asphalt | 아스팔트와 보도블록을 구분 |
| gap | 보도블록 사이 벌어진 틈 |

## 결과
전체 F1 0.33 (conf 0.384) · F1 곡선 최고점 asphalt 0.73 / crack 0.45 / pothole 0.26 / gap 0.20
→ 라벨 기준이 애매했던 gap·pothole이 하위 두 클래스

## 학습 설정
YOLO11n · epochs 100 · batch 8 · imgsz 640 · lr0 0.02 · warmup 3 · lrf 0.01 · CPU 약 7시간

## 파일 구성
| 파일 | 내용 |
|---|---|
| 분석 코드.ipynb | 데이터 로드 · YOLO11n 학습 · 평가 · 탐지 결과 |

## 기술 스택
Python · Ultralytics YOLO11 · Roboflow · OpenCV
