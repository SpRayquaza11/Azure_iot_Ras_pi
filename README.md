# Future_ready_talent_project
Submission for Future Ready Talent internship project

We will send critical Device monitoring like ambient temperature and Humidity as well as device health data Disk usage, RAM usage, CPU usage , etc to the cloud . If the cloud detects the device health is not good it will trigger a disable since if the telemetry device is not functioning correctly there is a risk of failre in the monitored device.THe monitoring data may also lead to execution of Cloud logic based on threshold parameters.

The following hardware is required , but you may use a different sensor if you wish!

   1)Raspberry pi v4 model b (v3 wll also work)
   
   2)dht22 sensor (a fairly old sensor so replacing this may definetly help!)
   
   3)Mxchip AZ3166 (Not required but nice to have)
   
   4)A MicroSD card with minimu 4 GB storage (To install our OS for raspberry pi Itdefinetly helps to have it!) 
   
   5)Jumper cables as required
   
 Optional
 
   6)A 5 k OHM resistor (Note: My connection did not require one)
   
   7)More Telemetry sensors (Eg pressure or gas sensor as you may seem fit)
    
    
STEP 1)
 
Install and burn an OS image for rasbian OS through the Rasberry PI OS installer tool

Other OS like the DietPi may work but i have not tested with the same.

you may follow online walk-throughs or the official link to get this OS here https://www.raspberrypi.com/software/


NOTE :- PLEASE ENSURE THE ETCHING PROCESS IS NOT INTERRUPTED


fill in the required details tocreate a root user account

STEP 2)

Once you have your Desktop open connect to a network with internet access through which you intend to send the data to the Azure IOT hub.

We can now begin downloading the required packages 

the packages required are :-  
    
   1)PIP
   
   2)Python3
open bash shell with root account

You would need to verify that theyare present using the following commands

    python3 -V
    pip -V

AFTER making sure PIP and Python3 are installed
    
   3)azure.iot.device
   
   4)adafruit_dht
   
   5)psutil
   
   6)Adafrut_blinka (contains the "Board" module for raspberry pi)

    
NOTE:- there is a chance PIP may just be pre-installed along with python3 package but for different versions of LINUX this may not be the case.In rasbian OS the above installation is not required.

After verifying that PIP and python3 are installed.

open bash shell with root account
   
    sudo apt-get update
    sudo apt upgrade
    sudo pip install azure-iot-device
    sudo pip install Adafruit_DHT 
    sudo pip install Adafruit_blinka


Now we use the Code in my repo ensure you paste the right connections string 

After saving the python file we make a cron job that repeatedly executes the said file in regular intervals the code or doing the same every two minutes is given below

open bash shell with root account

    crontab -e
    */2   *    *    *    *  python3   <your directory>





After that fill in the code in thonny python IDE or the IDE of your choice generate A CRON JOB that repeatedly executes the CODE and you should have your device sending Telemetry data regularly without a hitch!

To setup the Mxchip AZ3166 please follow the official documentation from Microsoft which I found to be very useful https://docs.microsoft.com/en-us/azure/iot-develop/quickstart-devkit-mxchip-az3166

The connection string as well as the SSID and password of your WI-FI is all you must supply, make sure that the essential C make and ARM GCC packages are installed (Termite is optional and only for monitoring)
 

Thanks for taking a look at my project !
-Swarup Mohapatra (Spray)
    
