# InnerSight-SampleCode

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
