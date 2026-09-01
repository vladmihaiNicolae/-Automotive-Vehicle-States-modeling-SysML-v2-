
- the **behaviour** is modeled by **function-based** representation

package PowerSupply {

    private import ScalarValues::*;

action def PowerSupplyActionFlow {

    attribute key_authen : Boolean;
    attribute customerAction : Boolean;
    attribute immobilizerSystemAccept : Boolean;

    first start;
    then action unlockDoors;

    then decide decision1;
        if not customerAction then wait;
        if customerAction then pushOnMultimediaStartButton;

    action wait;

    action pushOnMultimediaStartButton;

    then decide decision2;
        if not customerAction then wait;
        if customerAction then insertKey;

    action insertKey;
        then action rotateToIgnition;

    action rotateToIgnition;
        then decide decision3;
            if not key_authen then keyNotAuthentified;
            if key_authen then rotateToStart;

    action rotateToStart;
        then decide decision4;
            if immobilizerSystemAccept then engineRunning;
            if not immobilizerSystemAccept then engineStartBlockedByImmobilizer;

    action engineRunning;

    action keyNotAuthentified;

    action engineStartBlockedByImmobilizer;

}
}
