

package PowerSupplyRequirements {
    
    private import SI::*;
    
    requirement def <'REQ-001'> PowerSupplyManagement {
        doc /* The system has to manage vehicle power supply levels, especially accessory state. */
    }

    requirement def <'REQ-01.1'> DoorManagement {
        doc /* The system will pass from st1 to st3 by doors unlocking and from st4 to st3 by doors opening. */
    }

    requirement def <'REQ-01.2'> TimeoutSleep {
        doc /* The system has to pass from st3 to st1 state after T1 or T3 timers are elapsed. */
    }

    requirement def <'REQ-02.1'> MultimediaActivation {
        doc /* The system has to pass from st3 to st4 when multimedia is turned on by customer. */
    }

    requirement def <'REQ-03.1'> IgnitionAndEngineManagement {
        doc /* The system will pass to st5 or st6 by ignition switch. */
    }

    requirement powerSupplyReq : PowerSupplyManagement {
        requirement doorReq : DoorManagement;
        requirement timeoutReq : TimeoutSleep;
        requirement multimediaReq : MultimediaActivation;
        requirement ignitionAndengineReq : IgnitionAndEngineManagement;
    }

    state def Accessory_states {
        state st1; // Locked / Sleeping
        state st3; // Unlocked
        state st4; // Multimedia On
        state st5; // Ignition On
        state st6; // Engine Started
    }

    dependency from Accessory_states to powerSupplyReq;
    dependency from Accessory_states::st1 to powerSupplyReq::doorReq;
    dependency from Accessory_states::st3 to powerSupplyReq::doorReq;
    dependency from Accessory_states::st4 to powerSupplyReq::doorReq;
    dependency from Accessory_states::st1 to powerSupplyReq::timeoutReq;
    dependency from Accessory_states::st3 to powerSupplyReq::timeoutReq;
    dependency from Accessory_states::st3 to powerSupplyReq::multimediaReq;
    dependency from Accessory_states::st4 to powerSupplyReq::multimediaReq;
    dependency from Accessory_states::st5 to powerSupplyReq::ignitionAndengineReq;
    dependency from Accessory_states::st6 to powerSupplyReq::ignitionAndengineReq;
}

