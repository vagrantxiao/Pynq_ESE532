# Pynq_ESE532

## 1 Description
This a tutorial to show how to use the Pynq overlay on Ultra96 to interact with SDSoC.

## 2 Boot SD Card Creation
If you get an SD card from us, it has some Pynq image inside. Go to If you did not get an SD Card from us, you can burn the image file into the SD card by yourself. Download the image files from [Pynq website](http://www.pynq.io/board.html). Choose Avnet `Ultra96-V2: v2.5 PYNQ image`. Download a tool called `balenaetcher`. Select the downloaded image file for Ultra96-V2, choose the SD card as target device and flash!

![](/img/flash.JPG)

## 3 Driver Installation
Insert the SD Card into Ultra96-V2. Change the the boot mode to SD card mode. 

![](/img/sdmode.jpg)

Connect USB downstream to the PC. You can also connect JTAG board to the PC. 

![](/img/miniUSB.jpg)

Power on the board. You should see boot information in SDx Terminal.

![](/img/bootOK.JPG)

Type in the password (xilinx). You can log into the terminal. At this time, Ultra96-V2 is a server. Go to `http://192.168.3.1:9090/notebooks/common/wifi.ipynb`. Run the this the python code to connect your board with WIFI, so that you can install drivers for your Pynq OS. Open a terminal, as below.

![](/img/terminal.JPG)

In this Ubuntu system, execute such code.

````bash
git clone http://git.eclipse.org/gitroot/tcf/org.eclipse.tcf.agent.git
cd org.eclipse.tcf.agent/agent/
make -j4
make install
install -d -m 755 /usr/sbin
install -d -m 755 /etc/init.d
install -d -m 755 /usr/include
install -d -m 755 /usr/include/tcf
install -d -m 755 /usr/include/tcf/framework
install -d -m 755 /usr/include/tcf/services
install -c obj/GNU/Linux/a64/Debug/agent -m 755 /usr/sbin/tcf-agent
install -c obj/GNU/Linux/a64/Debug/client -m 755 /usr/sbin/tcf-client
install -c tcf/main/tcf-agent.init -m 755 /etc/init.d/tcf-agent
install -c tcf/config.h -m 755 /usr/include/tcf/config.h
install -c -t /usr/include/tcf/framework -m 644 tcf/framework/*.h
install -c -t /usr/include/tcf/services -m 644 tcf/services/*.h
/etc/init.d/tcf-agent start
````

Go back to SDx, double click `Linux Agent [default]`. Change the host to `192.168.3.1`.


## 4 Boot from Linux
Insert the SD Card into Ultra96-V2. Change the the boot mode to SD card mode. 

![](/img/sdmode.jpg)

Connect USB downstream to the PC. You can also connect JTAG board to the PC. 

![](/img/miniUSB.jpg)

Power on the board. You should see boot information in SDx Terminal.

![](/img/bootOK.JPG)

Type in the password (xilinx). You can log into the terminal. At this time, Ultra96-V2 is a server. Go to `http://192.168.3.1:9090/notebooks/common/wifi.ipynb`. Run the this the python code to connect your board with WIFI, so that you can install drivers for your Pynq OS. Open a terminal, as below.

![](/img/terminal.JPG)




## 4 SDx Project Development
Go back to SDx, double click `Linux Agent [default]`. Change the host to `192.168.3.1`.

![](/img/tcf.JPG)

Greate a new SDx project. This time, your project is based on ESE532Linux platform which can be found under [Our repo](ese532Linux). You can integrated this platform as the [tutorial](https://github.com/vagrantxiao/ultra96_ese532) we gave you before. Now, you can run or debug it as the standalone.












