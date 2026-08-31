

package PowerSupplySequenceModel {

    private import ScalarValues::*;

    // Messages
    attribute def UnlockDoorsMsg;
    attribute def StartButtonPressedMsg;
    attribute def KeyInsertedMsg;
    attribute def RotateToIgnitionMsg;
    attribute def RotateToStartMsg;
    attribute def EngineRunningMsg;
    attribute def KeyNotAuthenticatedMsg;
    attribute def EngineBlockedMsg;

    // Actors
    part def Driver;
    part def BCM;
    part def MultimediaSystem;
    part def KeyCylinderSensor;
    part def ImmobilizerSystem;
    part def Engine;

    // Scenario : unlock -> multimedia -> key insert -> ignition -> start -> engine running

     part scenario {

        part driver : Driver;
        part bcm : BCM;
        part multimedia : MultimediaSystem;
        part keySensor : KeyCylinderSensor;
        part immobilizer : ImmobilizerSystem;
        part engine : Engine;

        message m1 of UnlockDoorsMsg from driver to bcm;
        message m2 of StartButtonPressedMsg from driver to multimedia;
        message m3 of KeyInsertedMsg from driver to keySensor;
        message m4 of RotateToIgnitionMsg from driver to keySensor;
        message m5 of RotateToStartMsg from driver to keySensor;
        message m6 of EngineRunningMsg from immobilizer to engine;
    }

}
