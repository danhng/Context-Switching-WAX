# Context-aware WAX.
## Aims
* The device location on the body also plays an important role in the accuracy of an activity
recognising algorithm. It is shown that one of the most commonly used location on the body is the
waist since it is very close to the centre of mass of human body thus displaying the most
representative part of human movement.
* The project aims to produce an algorithm optimised for devices worn at the lower back
position for the AX9 Inertial Measurement Unit developed under OpenMovement platform that is
capable of detecting simple activity transitions including postural transitions (standing to walking)
and lying transitions (lying to standing) using accelerometer tri-axis data in a computationally
efficient manner that could be applied to the devices.
* Using this algorithm, devices will be able to perform contextual triggering: turning on
gyroscope when a postural transition is detected only. This will help in saving a lot of power when
the user is inactive.

## Objectives
###Objective 1:
To produce an algorithm optimised for the lower back position that is capable of detecting
two postural transitions: Sitting to standing and vice versa, standing to walking and vice versa
given a three dimensional acceleration data as primary input. The algorithm must be:
* Accurate: The algorithm should be able to work accurately at an acceptable level.
* Computationally efficient: The algorithm should be efficient, elegant that does not put
a high pressure on the device's processor.
* Power efficient (Device implementation): The algorithm should be able help devices
operate over a substantial amount of times that is perceptibly longer than devices under context nonaware implementations..

###Objective 2:
To demonstrate the accuracy, efficiency and feasibility of the produced algorithm by:
* To produce an implementation on a simulated environment in which the targeted
device's specifications are taken into consideration.
* To produce an implementation on the targeted device that dynamically turns on the
gyroscope when a postural transition (Sitting to standing or Standing to walking) is detected by the
algorithm and turns off the gyroscope when users are inactive.
* To performs experiments and evaluation on the produced algorithm and
implementations.


##Directory structure
	/prototype/ : Contains the source code and test data.
	/support/ : Contains the appendix 4.
	/readme.md : instruction on using the project.

##Instructions

Please follow the following instruction to run the program.

Note: The program requires liblog4c dependency for debugging sections.

1. Install C4.5 using the source code obtained on www.rulequest.com/Personal/
Make sure the installation is in the path e.g. `/usr/bin`. You need not specifiy any installation path while make_ing. `make` will put all binaries and libraries in the right places. 
2. Make sure you are in the base of the project and change the directory to `/simulated`.
	
	`cd simulated`
	
3. Make sure the dataset files Michael_Train.csv and Michael_Test.csv are in thedirectory. 
4. Here there are two options. 

4.1. You could choose to manually compile the program by following this section, if you don't wish to do so, head to 4.2.
	
	`make`
	
If everything goes right, make will provide an executable called "cawax" in the same directory. verify its creation by:
	
	stat cawax
	
Run the program with optional argument that specifies the name of the users whose datatset will be used to construct the decision tree. 
	
	./cawax username
	
If no username is specified, the default value is Michael which points to Michael's datatset.
-> The program will now execute, performing all tasks indicated in the implementation section in the dissertation.

Now, provided that you have the c4.5 ready. run
	
	c4.5 cawax -v [verboseoption]
	
The classification tree will then be generated.

4.2. The fastest way to run the program is to execute the script `run.sh`, specifying the username as the only argument. It will automatically performs all necessary tasks leaving you with completely ready decision trees.

5. Test
Unfortunately, automated test is not yet suppored.
However, data for it (extracted features) will have been already computed and output to cawax_test.data as per the implementation strategy.
run 

	`consult cawax`
	
to start the test phase.
The program will ask for necessary test values. It will stop as soon as it gathers enough information to infer the classification result.

6. Clean
To clean the last build and all the data feature files generated by the program, simply run
	
	`make clean`

If you have any feedback or questionaire, please send it to 
dtnguyen.work@gmail.com

For more information on C4.5 programs, consult the manual available in the source code archive.

Updated on 2/11/2016.