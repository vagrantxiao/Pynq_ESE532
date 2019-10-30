# Pynq_ESE532

## 1 Description
This a tutorial to show how to use the Pynq overlay on Ultra96 to interact with SDSoC.

## 2 Boot SD Card Creation
We assume you get an SD card from us. It has some Pynq image inside. If you are interested in creating the boot SD card, you can to to [MK_SD.md](/burn_SD/MK_SD.md).
Go back to SDx, double click `Linux Agent [default]`. Change the host to `192.168.3.1`.


## 3 Boot from Linux
Insert the SD Card into Ultra96-V2. Change the the boot mode to SD card mode. 

![SD card Mode](/img/sdmode.jpg)

Connect USB downstream to the PC. You can also connect JTAG board to the PC. 

![](/img/miniUSB.jpg)

Power on the board. You should see boot information in SDx Terminal.

![](/img/bootOK.JPG)

Go to your internet browser, and access 192.168.3.1 to log into a jupyter terminal. Type in the password (xilinx). You can log into the terminal. At this time, Ultra96-V2 is a server. 
![](/img/jupyter.JPG)


Go to `http://192.168.3.1:9090/notebooks/common/wifi.ipynb`. Run the this the python code to connect your board with WIFI, so that you can install drivers for your Pynq OS. Open a terminal, as below.

![](/img/terminal.jpg)

In the terminal execute `/etc/init.d/tcf-agent start`.
![](/img/start_tcf.jpg)

## 4 SDx Project Development
Go back to SDx, double click `Linux Agent [default]`. Change the host to `192.168.3.1`.

![](/img/tcf.JPG)

Greate a new SDx project. This time, your project is based on ESE532Linux platform which can be found under [Our repo](ese532Linux). You can integrated this platform as the [tutorial](https://github.com/vagrantxiao/ultra96_ese532) we gave you before. Now, you can run or debug it as the standalone.












