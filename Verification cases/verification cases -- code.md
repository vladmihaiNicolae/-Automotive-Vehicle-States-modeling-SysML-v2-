package VehicleVerificationCases {

    private import ScalarValues::*;

    part def Power_supply {
        attribute key_authen : Boolean;
        attribute customerAction : Boolean;
        attribute immobilizerSystemAccept : Boolean;
        attribute doorsUnlocked : Boolean;
        attribute engineRunning : Boolean;
    }

    requirement def DoorUnlockRequirement {
        doc /* Doors must unlock at driver request */
        subject sys : Power_supply;
    }
    requirement doorUnlockReq : DoorUnlockRequirement;

    requirement def KeyAuthenticationRequirement {
        doc /* Starting sequence must stop if key authentication fails */
        subject sys : Power_supply;
    }
    requirement keyAuthReq : KeyAuthenticationRequirement;

    requirement def ImmobilizerSafetyRequirement {
        doc /* Engine must not start if immobilizer forbids it */
        subject sys : Power_supply;
    }
    requirement immobilizerReq : ImmobilizerSafetyRequirement;

    requirement def EngineStartRequirement {
        doc /* Engine has to start only after all conditions have been fulfield */
        subject sys : Power_supply;
    }
    requirement engineStartReq : EngineStartRequirement;


    verification def DoorUnlockTest {
        subject sys : Power_supply;
        objective doorUnlockObjective {
            satisfy doorUnlockReq by sys;
        }
        attribute verdictPass : Boolean;
    }
    verification doorUnlockVerification : DoorUnlockTest {
        verdictPass = true;
    }

    verification def KeyAuthenticationTest {
        subject sys : Power_supply;
        objective keyAuthObjective {
            satisfy keyAuthReq by sys;
        }
        attribute verdictPass : Boolean;
    }
    verification keyAuthVerification : KeyAuthenticationTest {
        verdictPass = true;
    }

    verification def ImmobilizerSafetyTest {
        subject sys : Power_supply;
        objective immobilizerObjective {
            satisfy immobilizerReq by sys;
        }
        attribute verdictPass : Boolean;
    }
    verification immobilizerVerification : ImmobilizerSafetyTest {
        verdictPass = true;
    }

    verification def EngineStartTest {
        subject sys : Power_supply;
        objective engineStartObjective {
            satisfy engineStartReq by sys;
        }
        attribute verdictPass : Boolean;
    }
    verification engineStartVerification : EngineStartTest {
        verdictPass = true;
    }
}
