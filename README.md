/**
@mainpage Wireless home appliances control.

@author Akshay Pampatwar (Software)
@author Sancho Simmy Louis (Hardware Circuit Design)
@author Nijil George (Android App)
@author Sabitha Susan Joseph (PCB Design)

Appliances can be controlled via switches on a control board or a bluetooth mobile app. This project is developed for Tiva C tm4c123gh6pm uC. It can control following appliances:

(i)Fan

(ii)12 V Led strip

(iii)Plug1

(iv)Plug2

Hardware profiling of fan is done in the code so even in case of low or over voltage of AC main line, Fan speed will remain constant for a given setting.
User specific setting of fan speed,led light brightness can be enabled from bluetooth app. 

In the starting, stored i.e. last values of Fan speed and Led Intensity will be used for control. 
Remainig inputs will be taken from hardware control panel i.e. switch board.
Thus in case of electricity failure, Fan speed and Led light brighteness will be restored but on/off state of appliances will depend on states of switches. User will have to resend commands via app for wireless control.

In case of multiple users, Latest command will be considered. 
Once commands are sent over a bluetooth, o/p states will remain unnchanged even if wireless link is lost. i.e. Switch status will be ignored, But changes in switch will be incorporarted. 
E.g. Currently switch for fan is on and fan is on. Now if turn off command sent wirelessly then fan will turned off. But if switch for fan is toggled from on to off and off to on then fan will be turned on (Even if wireless link exists thus latest command is considered for final state of o/p).

	Software is divided into 3 layers.

(i)Application layer

(ii)Middle layer

(iii)Hardware Abstraction layer

For time being, for simplicity many HAL functions are defined in a Middle layer files/module. e.g. Bluetooth,fan,led,plug etc.

	Working of code: 

(i) First code initializes all the o/p pins and i/p pins. Initiallly all the o/ps are off.

(ii)Status of fan speed and led light intensity is restored from eeprom.

(iii)Depending on status of switches appliances will be turned on.

(iv)If data is sent over a bluetooth then it will be decoded and stored in a global variable.

(v)Controller continuously checks changes in states of appliances (From Switchs or Wi Command) Depending on new commands will be enforced for turning on/off or change of speed of appliances.

(vi)New commands of fan speed and intensity will be saved in an eeprom.

	Read files from Documentation\html folder for more info on software / code.
*/
