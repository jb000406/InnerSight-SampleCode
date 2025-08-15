# 마경

마경 프로젝트에서 보스와 유물에 제가 사용한 스크립트 입니다.

## 🔧 기술 스택

- Unity 2022.3.x
- C#

## 🕹️ 프로젝트 설명

- 원흉의 저주에 걸린 소여제를 구하기위해 마경으로 떠나는 주인공의 이야기 입니다.
  마경은 마귀가 사는곳으로 알려져있으며 들어가서 돌아온자가 없다는 미지의 영역입니다.
  주인공은 마경탐사를 하다가 죽을경우 마을로 돌아오게되는데 스토리 전개에 따라 
  사망회귀의 비밀이 풀리는 로그라이크류 게임입니다.

## 📁 주요 기능 및 구조

### 🎯 핵심 기능 요약
- 기능1: 설명
- 기능2: 설명

### 🧩 스크립트 구성도




### 🔗 스크립트 관계도
- GameManager → Player 참조
- GameManager → RelicManager 연결
- BossController_First → BossPhaseManager 등

## 💡 참고 사항

- 테스트 환경
- 실행 조건
- 기타 주의할 점

## 📷 스크린샷 / GIF

(게임 캡처나 UI 화면 등)

## 👤 제작자

- 이름 / 연락처 (선택)
- 포트폴리오 링크, Notion, 블로그 등


## 보스 관련 개요

graph TD;
    A["GameManager"] --> B["BossStageManager"];
    
    B --> C["BossStat"];
    B --> D["BossHealthUI"];
    
    C --> E["BossConnect"];
    
    E --> F["FirstBossManager"];
    E --> F["SecondBossManager"];
    
    F --> G["BossAttack(보스의 공격들)"];
    F --> H["BossStateController"];
    
    D --> I["WorldSpaceBossHealthBar"];
    D --> J["Billboard"];


## 유물 관련 개요

graph TD;
		게임 시작 후
    A["RelicManager"] --> B["RelicEffectManager"];
    A --> C["RelicSaveData"];
    
    유물을 먹었을경우
    D["ResurrectionRelic"] --> A;


1. GameManager

- 게임 전체 흐름 제어 (보스 진입, 유물 효과, 상태 초기화 등)

- Player 스크립트 참조 제공

2. Relic 시스템

- RelicManager: 획득 및 적용된 유물 관리

- RelicEffectManager: 유물 효과를 실행하는 중앙 관리처

- RelicFactory: ID 기반 유물 객체 생성

- RelicSaveData: 저장된 유물을 불러오며 자동 복원 처리

3. 보스 시스템

- BossStageManager: 스테이지별 보스 전환 및 초기화

- FirstBossManager, SecondBossManager: 각 보스의 행동, 패턴, 애니메이션 처리

- 공격 관련 스크립트: AttackBox, TrailEffectController, SpawnAxeController, LaserDamage 등

Scripts 폴더 구조

Scripts/
├── Boss/
│   ├── Allboss/
 |     |      ├── Billboard.cs
 |     |      ├── BossHealthUI
 |     |      ├── BossStageManager.cs
 |     |      ├── BossStat.cs
 |     |      ├── BossStateController.cs
 |     |      ├── WorldSpaceBossHealthBar.cs
│   ├── BossAttack/(보스별 공격 스크립트)
│   └── BossManager/(보스별 행동, 패턴 스크립트)
└── Relic/
    ├── RelicManager.cs
    ├── RelicEffectManager.cs 
    ├── Save/
     |      ├── RelicFactory.cs
     |      ├── RelicSaveData.cs
    └── RelicList/
            ├── IRelic.cs
            ├── ResurrectionRelic.cs
            └── HealingStoneRelic.cs
Scripts/
├── GameManager.cs
├── Player.cs
