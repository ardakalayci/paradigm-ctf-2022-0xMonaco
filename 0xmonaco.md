# 0xMonaco (30th place (1310.91 ELO))

Team: kalayci  (30th place out of 127)

### Description :
```
DESCRIPTION
Max Verstappen's favorite smart contract. The points for this challenge will be allocated at the end of the CTF. See "How to Play" for more info

ACCESS
https://0xmonaco.ctf.paradigm.xyz/

RESOURCES
https://github.com/paradigmxyz/paradigm-ctf-infrastructure
/resources/0xmonaco.zip
```

![](https://i.imgur.com/P2WvY85.png)


### My car contract that got me 30th place:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.13;

import "./Car.sol";

contract CarV2 is Car {
    constructor(Monaco _monaco) Car(_monaco) {}

    function Up900(Monaco.CarData[] calldata allCars, uint256 ourCarIndex)
        private
    {
        Monaco.CarData memory ourCar = allCars[ourCarIndex];
 if (ourCar.balance > 6500) {
            if (4000 > monaco.getAccelerateCost(10))
                ourCar.balance -= uint24(monaco.buyAcceleration(10));
              else if (3000 > monaco.getAccelerateCost(5))
                ourCar.balance -= uint24(monaco.buyAcceleration(5));
            if (
                ourCarIndex != 0 &&
                
                3500 > monaco.getShellCost(1)
            ) {
                monaco.buyShell(1); // This will instantly set the car in front of us' speed to 1.
            }
            
        }
        else if (ourCar.balance > 4500) {
            if (3000 > monaco.getAccelerateCost(10))
                ourCar.balance -= uint24(monaco.buyAcceleration(10));
            if (
                ourCarIndex != 0 &&
                
                1500 > monaco.getShellCost(1)
            ) {
                monaco.buyShell(1); // This will instantly set the car in front of us' speed to 1.
            }
            return;
        }else{
            if (
                ourCarIndex != 0 &&
                
                ourCar.balance > monaco.getShellCost(1)
            ) {
                monaco.buyShell(1); // This will instantly set the car in front of us' speed to 1.
            }
        }
    }

    function Up750(Monaco.CarData[] calldata allCars, uint256 ourCarIndex)
        private
    {
        Monaco.CarData memory ourCar = allCars[ourCarIndex];
 if (ourCar.balance > 6500) {
            if (2500 > monaco.getAccelerateCost(5))
                ourCar.balance -= uint24(monaco.buyAcceleration(5));
            if (
                ourCarIndex != 0 &&
                allCars[ourCarIndex - 1].speed > ourCar.speed &&
                400 > monaco.getShellCost(1)
            ) {
                monaco.buyShell(1); // This will instantly set the car in front of us' speed to 1.
            }
        }
        else if (ourCar.balance > 4000) {
            if (1000 > monaco.getAccelerateCost(5))
                ourCar.balance -= uint24(monaco.buyAcceleration(5));
            if (
                ourCarIndex != 0 &&
                allCars[ourCarIndex - 1].speed > ourCar.speed &&
                400 > monaco.getShellCost(1)
            ) {
                monaco.buyShell(1); // This will instantly set the car in front of us' speed to 1.
            }
        }
    }

    function Up600(Monaco.CarData[] calldata allCars, uint256 ourCarIndex)
        private
    {
        Monaco.CarData memory ourCar = allCars[ourCarIndex];

        if (300 > monaco.getAccelerateCost(10)) {
            ourCar.balance -= uint24(monaco.buyAcceleration(10));
        } else {
            if(ourCar.balance>10000&& 500>monaco.getAccelerateCost(6)){
                ourCar.balance -= uint24(monaco.buyAcceleration(6));
            }

            
            if (300 > monaco.getAccelerateCost(3))
                ourCar.balance -= uint24(monaco.buyAcceleration(3));
        }
        if(allCars[0].y>800){if (
                ourCarIndex != 0 &&
                
               50 > monaco.getShellCost(1)
            ) {
                monaco.buyShell(1); // This will instantly set the car in front of us' speed to 1.
            } else if(ourCarIndex != 0 && allCars[ourCarIndex - 1].speed > ourCar.speed*2&&ourCar.speed>10){
                monaco.buyShell(1); // This will instantly set the car in front of us' speed to 1.
            }}
         
    }

    function Up0(Monaco.CarData[] calldata allCars, uint256 ourCarIndex)
        private
    {
        Monaco.CarData memory ourCar = allCars[ourCarIndex];

        if (150 > monaco.getAccelerateCost(10)) {
            ourCar.balance -= uint24(monaco.buyAcceleration(10));
        } else {
            if (200 > monaco.getAccelerateCost(3))
                ourCar.balance -= uint24(monaco.buyAcceleration(3));
        }

        if(allCars[0].y>800){
 if (
                ourCarIndex != 0 &&
                
               50 > monaco.getShellCost(1)
            ) {
                monaco.buyShell(1); // This will instantly set the car in front of us' speed to 1.
            } else if(ourCarIndex != 0 && allCars[ourCarIndex - 1].speed > ourCar.speed*2&&ourCar.speed>10){
                monaco.buyShell(1); // This will instantly set the car in front of us' speed to 1.
            }
        }
               
    }

    function leader(Monaco.CarData[] calldata allCars, uint256 ourCarIndex)
        private
    {
        Monaco.CarData memory ourCar = allCars[ourCarIndex];

        if (allCars[1].balance < 500) {
            if (3000 > monaco.getAccelerateCost(10) && 3000 < ourCar.balance) {
                ourCar.balance -= uint24(monaco.buyAcceleration(10));
            }
        }
    }

    function takeYourTurn(
        Monaco.CarData[] calldata allCars,
        uint256 ourCarIndex
    ) external override {
        Monaco.CarData memory ourCar = allCars[ourCarIndex];

        if (ourCar.y > 900) {
            Up900(allCars, ourCarIndex);
        } else if (ourCar.y > 750) {
            Up750(allCars, ourCarIndex);
        } else if (ourCar.y > 600) {
            Up600(allCars, ourCarIndex);
        } else if (ourCar.y >= 0) {
            Up0(allCars, ourCarIndex);
        }
    }
}
```

![](https://pbs.twimg.com/media/FatusLsX0AMJHdp)
