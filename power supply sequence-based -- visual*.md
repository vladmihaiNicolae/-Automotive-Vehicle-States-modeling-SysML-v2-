
the bellow diagram is generated with Gemini, based on associated code in this repository, because Jupyer lab is not able to create sequence-view

the scenario taken into account is key successfuly authenticated and immobilizer is unlocked

┌──────────┐      ┌───────┐      ┌──────────────────┐      ┌────────────────────┐      ┌───────────────────┐      ┌──────────┐
│  driver  │      │  bcm  │      │    multimedia    │      │     keySensor      │      │    immobilizer    │      │  engine  │
└────┬─────┘      └───┬───┘      └────────┬─────────┘      └─────────┬──────────┘      └───────  ┬─────────┘      └────┬─────┘
     │                │                   │                          │                         │                   │
     │  m1 : UnlockDoorsMsg               │                          │                         │                   │
     │────────────────>                   │                          │                         │                   │
     │                │                   │                          │                         │                   │
     │m2 : MultimediaStartButtonPressedMsg│                          │                         │                   │
     │────────────────────────────────────>                          │                         │                   │
     │                                    │                          │                         │                   │
     │  m3 : KeyInsertedMsg               │                          │                         │                   │
     │──────────────────────────────────────────────────────────────>│                         │                   │
     │                                    │                          │                         │                   │
     │  m4 : RotateToIgnitionMsg          │                          │                         │                   │
     │──────────────────────────────────────────────────────────────>│                         │                   │
     │                                    │                          │                         │                   │
     │  m5 : RotateToStartMsg             │                          │                         │                   │
     │──────────────────────────────────────────────────────────────>│                         │                   │
     │                                    │                          │                         │                   │
     │                                    │                          │                         │ m6:EngineRunningMsg
     │                                    │                          │                         │──────────────────>│
     │                                    │                          │                         │                   │
     v                                    v                          v                         v                   v
