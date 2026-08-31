
- events (eg LockUnlockDoorsEvent, IgnitionPositionEvent ... )  which make state to change are declared as **attributes** ; 
    more appropriate would be to declare them as **events**, **messages** or **signals**, but Jupyter lab doesn't recognise these types (I get errors at code compilation) ;
- the **behaviour** is modeled by **state-based** representation

private import SI::*;

    attribute def LockUnlockDoorsEvent;
    attribute def IgnitionPositionEvent;
    attribute def StartPositionEvent;
    attribute def EngineOffEvent;
    attribute def MultimediaRequestEvent;
    attribute def DoorOpenEvent;

state def Accessory_states {

        state st1; // Locked / Sleeping
        state st3; // Unlocked
        state st4; // Multimedia On
        state st5; // Ignition On
        state st6; // Engine Started

        // st1 -> st3 : lock/unlock doors (RF key)
        transition st1_to_st3
            first st1
            accept LockUnlockDoorsEvent
            then st3;

        // st3 -> st1 : T1 timer finished
        transition st3_to_st1_T1
            first st3
            accept after (1 [min])
            then st1;

        // st3 -> st1 : T30 timer finished
        transition st3_to_st1_T30
            first st3
            accept after (30 [min])
            then st1;

        // st3 -> st5 : turn of the key in the ignition switch
        transition st3_to_st5
            first st3
            accept IgnitionPositionEvent
            then st5;

        // st3 -> st4 : multimedia request by CAN signal
        transition st3_to_st4
            first st3
            accept MultimediaRequestEvent
            then st4;

        // st4 -> st3 : door opening information received from door sensor
        transition st4_to_st3
            first st4
            accept DoorOpenEvent
            then st3;

        // st4 -> st5 : turn of the key in the ignition switch
        transition st4_to_st5
            first st4
            accept IgnitionPositionEvent
            then st5;

        // st5 -> st4 : engine turn off by ignition switch
        transition st5_to_st4
            first st5
            accept EngineOffEvent
            then st4;

        // st5 -> st6 : engine turn on by ignition switch
        transition st5_to_st6
            first st5
            accept StartPositionEvent
            then st6;
    }
