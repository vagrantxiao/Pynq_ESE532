If you did not get an SD Card from us, you can burn the image file into the SD card by yourself. Download the image files from [Pynq website](http://www.pynq.io/board.html). Choose Avnet `Ultra96-V2: v2.5 PYNQ image`. Download a tool called `balenaetcher`. Select the downloaded image file for Ultra96-V2, choose the SD card as target device and flash!

![](/img/flash.JPG)


Insert the SD Card into Ultra96-V2. Change the the boot mode to SD card mode. 

![](/img/sdmode.jpg)

Connect USB downstream to the PC. You can also connect JTAG board to the PC. 

![](/img/miniUSB.jpg)

Power on the board. You should see boot information in SDx Terminal.


Go to your internet browser, and access 192.168.3.1 to log into a jupyter terminal.
![](/img/jupyter.JPG)

 Type in the password (xilinx). You can log into the terminal. At this time, Ultra96-V2 is a server. Go to `http://192.168.3.1:9090/notebooks/common/wifi.ipynb`. Run the this the python code to connect your board with WIFI, so that you can install drivers for your Pynq OS. Open a terminal, as below.

![](/img/terminal.jpg)

Copy the 'libsds_lib.so' from '< Your SDx Installation Path >/SDx/2018.3/target/aarch64-linux/lib' to the root of the `\\pynq\xilinx`. You may need to enter the User ID (xilinx) and password (xilinx) to access the destination directory. 
![](/img/libs.jpg)

In this Jupyter Ubuntu system, execute such code.

````bash
cp libsds_lib.so /usr/lib
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
