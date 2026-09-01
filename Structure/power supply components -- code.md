
package PowerSupplyStructure {
    
    part def Key {
        port rfOut;
    }

    part def BCM {
        port rfIn;
        port wireIn;
        port wireOut;
        port canBus;
    }

    part def IgnitionCylinder {
        port wireOut;
    }

    part def AccessoryRelay {
        port wireIn;
    }

        part def IgnitionRelay {
        port wireIn;
    }

    part connections {
        part key : Key;
        part bcm : BCM;
        part ignitionCylinder : IgnitionCylinder;
        part accessoryRelay : AccessoryRelay;
        part ignitionRelay : IgnitionRelay;

        connect bcm.wireIn to ignitionCylinder.wireOut ;
        connect bcm.wireOut to accessoryRelay.wireIn;
        connect bcm.wireOut to ignitionRelay.wireIn;
        connect key.rfOut to bcm.rfIn;  
        
    }
}

