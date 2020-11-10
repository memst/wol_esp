# ESP32 Wake-On-Lan server
This project turns a wifi enabled ESP32 device into a small server that forwards Wake-On-Lan packets to a device on the internal network.

It is meant to bypass routers that have no way of passing magic packets from the outside network. You will still need router credentials for this to work.

## Dependencies
* [WakeOnLan](https://github.com/a7md0/WakeOnLan): Using a pre-existing library to format magic packets

## Usage
The basic tutorial is meant for people using [Arduino IDE](https://www.arduino.cc/en/software). You sohuld install it to follow the tutorial or adapt accordingly.
1. Install board manager.

	1. In the Arduino IDE go to `File > Preferences` and paste the following url in the "Additional Boards Manager URLs": 
		```https://dl.espressif.com/dl/package_esp32_index.json```

	2. Then go to `Tools > Board > Boards Manager...` and install `esp32` manager.
	
	3. In `Tools > Board > ESP32 Arduino` select your ESP32 device from the list

2. Install [WakeOnLan](https://github.com/a7md0/WakeOnLan) library. The easiest way to install it is through `Sketch > Include Libary > Manage Libraries...` and searching for WakeOnLan.

3. Write esp_server to the board.

	1. Clone this repository to your machine and open it through your IDE. 

	2. Change the following lines with your wifi network information and the computer's you want to wake up MAC address.
		```
		const char* ssid = "WiFi name";
		const char* password = "WiFi password";
		const char* MACAddress = "MAC address of the device to be woken up";
		```

	3. Connect your ESP32 board to the computer and press Upload.


4. Add port forwarding through your router. 

	Find out how to connect to your router console and add a forwarding rule from TCP port 80 to your ESP device. The device prints its MAC address through serial on startup to help you identify it.