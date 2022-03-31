# test


#!/bin/bash

#################################
## Begin of user-editable part ##
#################################

ETHPOOL=us-eth.2miners.com:2020
ETHWALLET=0xe55c7176a55301525965925b2aadf49bc49e81e4
ETHWORKER=3090_japan

TONPOOL=wss://eu1.stratum.ton-pool.com/stratum
TONWALLET=EQDVmmN5Fgsx5YfLO-fa4o5SeFYjETYHHhYamHpbWoFT6un-



#################################
##  End of user-editable part  ##
#################################

cd "$(dirname "$0")"

./lolMiner --algo ETHASH --pool $ETHPOOL --user $ETHWALLET --dualmode TONDUAL --dualpool $TONPOOL --dualuser $TONWALLET --worker $ETHWORKER $@
while [ $? -eq 42 ]; do
    sleep 10s
    ./lolMiner --algo ETHASH --pool $ETHPOOL --user $ETHWALLET --dualmode TONDUAL --dualpool $TONPOOL --dualuser $TONWALLET --worker $ETHWORKER $@
done

