## ComFASE
 ComFASE is a  communication fault  and  attack  simulation  engine  that  allows  to  evaluate the behavior of interconnected automated vehicles in the presence of faults and attacks. ComFASE is a simulation-based fault and attack injection tool, it is composed of [OMNeT++](https://omnetpp.org/), [Veins](https://veins.car2x.org/), [Plexe](https://plexe.car2x.org/tutorial/), [SUMO](https://www.eclipse.org/sumo/) and [Python](https://www.python.org/).

<p align="center">
  <br><br>
  <img src="https://github.com/RISE-Dependable-Transport-Systems/ComFASE/blob/main/Documentation/pictures/ComFASE_Arc.jpg" width="450" height="300">
</p>
<br/> 
<br/> 


## Installation
Before integrating ComFASE into the simulator, it is recommended to have all the simulators running on your system. You can follow the instructions on the OMNeT++, Veins, and Plexe webpages to install them and have them ready to run. 

Note: ComFASE is tested in the below-mentioned versions of the simulators:

* [OMNeT++ 5.6.2](https://omnetpp.org/software/2020/01/13/omnet-5-6-released)
* [Veins 5.1](https://github.com/sommer/veins/releases/tag/veins-5.1)
* [Plexe 3.0a3](https://github.com/michele-segata/plexe/releases/tag/plexe-3.0a3)
* [SUMO 1.8.0](https://sourceforge.net/projects/sumo/files/sumo/version%201.8.0/)


|       Simulator       |                                 Definition                        |
| ----------------------| ----------------------------------------------------------------- |
| *OMNeT++*             | is a modular, component-based C++ simulation library and framework|
| *Veins*               | is a framework for running vehicular network simulations          |
| *Plexe*               | is a cooperative driving framework extending SUMO and Veins permitting the realistic simulation of platooning|
| *SUMO*                | is a microscopic traffic simulator                                  |

### Integrating ComFASE into the Simulators
1. Copy the **attackInjection** folder into the veins/src/veins directory.
2. Using **injector** in the code
```
auto Injection = FindModule<Injector*>::findGlobalModule();
    if (Injection->attackActive){
        std::cout<<"AttackActive = is TRUE"<<std::endl;
        //return myPDValue;
        //cPacket *omsg = msg->dup();
        float correctValue = receiverPos.distance(senderPos2) / BaseWorldUtility::speedOfLight();
        return Injection->AttackInjectionEngine(senderModule->getId(), receiverModule->getId(), correctValue);
        //return Injection->DenialOfServiceAttack(senderModule->getId(), receiverModule->getId(), correctValue);
        //return Injection->PropagationDelayAttack(senderModule->getId(), receiverModule->getId(), correctValue);
        //Injection.PropagationDelayAttack(senderModule->getId(), receiverModule->getId(), correctValue);
    }
    else{
    // this time-point is used to calculate the distance between sending and receiving host
        return receiverPos.distance(senderPos2) / BaseWorldUtility::speedOfLight();
    }
```
3. Update **ned** file of the example that you want to run by adding: 
``` 
import org.car2x.veins.attackInjection.Injector;
```
and 
```
        attacker: Injector {
            @display("p=120,50;i=abstract/penguin");
        }
```
4. in your **ini** file call "attackInjection.ini" by adding:
```
include <path to veins>/veins/src/veins/attackInjection/attackInjection.ini
```

5. Compile the code to make it ready to run (build all projects in OMNeT++ IDE)
## Running

## Result Analyze


## License

## Papers
