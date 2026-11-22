# Asura Balance · 아수라판 증강 밸런스

아수라판의 C# 보드게임 규칙을 직접 실행해 4인 AI 경기의 증강 선택과 효과를 비교하는 도구다. 자유 선택 경기와 동일 조건의 강제 지급 비교를 실행하고, 경기별 로그와 오프라인 대시보드를 생성한다.

**[16판 대시보드 다운로드](https://raw.githubusercontent.com/mingsuking1002/Asura-Balance/main/docs/index.html)** · **[실행과 재현 가이드](ModooMarbleUnity/Tools/Balance/README.md)**

- 공격, 방어, 금전, 도박, 시너지 선호와 세 가지 선택 노이즈
- 카드별 선택, 리롤, 금전 변화, 피해·방어, 무인도 이송
- 맵·성향·노이즈 필터, 대응 경기 승률 차이, 경기 효과 타임라인

## 자동 경기 실행

Python 3.10 이상과 Unity 6000.3.9f1의 Editor 설치 경로가 필요하다. Unity 창을 열 필요는 없다.

~~~powershell
git clone https://github.com/mingsuking1002/AsuraBoard-Git.git ../AsuraBoard-Git
git -C ../AsuraBoard-Git checkout 2e9364090740877f3f33db57058e10711cac0401
cd ModooMarbleUnity
python Tools/Balance/run.py --games 200 --seed 4200 --game-source ../../AsuraBoard-Git/ModooMarbleUnity --unity "C:/Program Files/Unity/Hub/Editor/6000.3.9f1/Editor"
~~~

결과는 Validation/Balance/dashboard.html과 matches.jsonl에 저장된다. 기본 예시는 자유 선택 200판과 대응 비교 120판을 생성한다. 저장소에 포함된 16판 샘플은 대시보드를 둘러보기 위한 데이터다.

게임 규칙과 시뮬레이터는 [아수라판 소스 스냅샷](https://github.com/mingsuking1002/AsuraBoard-Git/tree/2e9364090740877f3f33db57058e10711cac0401)을 사용한다. 공통 검사 도구는 [GameHarness](https://github.com/mingsuking1002/GameHarness)에서 관리한다.
