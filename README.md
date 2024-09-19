# RainGauge
The device uses LoRaWAN to uplink temperature, humidity and precipitation sensor data through calculation.
Data will be sent every 10 minutes, if there is rain, the sending time will be 2 minutes
Support sensors:
- [Digital humidity and temperature sensor - SHTC3](https://www.sensirion.com/products/catalog/SHTC3/)

## Getting Started

### Hardware

- USB to UART Converter
- RainGauge board based on rak11720

### Software

- Arduino IDE (version v1.8.13 or above is recommended)
- RUI3 lastest firmware for RAK11720 : [RAK11720_latest_final.hex](https://downloads.rakwireless.com/RUI/RUI3/Image/RAK11720_latest_final.hex)
- (STM32CubeProgammer)[https://www.st.com/en/development-tools/stm32cubeprog.html]

### Additional Libraries

- Adafruit_SHTC3.h


## Installation

### Hardware connection :

![image](https://github.com/XuanMinh201/RainGauge/assets/75436464/43590e25-210d-4a73-9fea-75715c76654b)

On the RainGauge board

![image](https://github.com/BASSO-Jostin/RainGauge_BLE/blob/main/Picture/RainGauge-connect_1.png)

### In STM32CubeProgammer :
  -  Hold the **B_RAK (boot)** button and press **R_RAK (reset)** button and release the **B_RAK (boot)** button to enter bootmode.
  -  Select UART, Baudrate 115200 and press Connect.
  -  Open RAK3172-E_latest_final.hex
  -  Select the address as in following image if needed
  -  Press Download to upload firmwave
  -  After download success, press **R_RAK (reset)** button to exit the bootmode
    
<!-- ![image](https://github.com/BASSO-Jostin/RainGauge_BLE/blob/main/Picture/Fichier_RAK11720_hex.PNG) -->
<img src="https://github.com/BASSO-Jostin/RainGauge_BLE/blob/main/Picture/Fichier_RAK11720_hex.PNG" height="450">

### In Arduino IDE:
  -  Add this JSON in Additional Boards Manager URLs [\(Show me how?\)](https://support.arduino.cc/hc/en-us/articles/360016466340-Add-third-party-platforms-to-the-Boards-Manager-in-Arduino-IDE):

```  
https://raw.githubusercontent.com/RAKWireless/RAKwireless-Arduino-BSP-Index/main/package_rakwireless.com_rui_index.json
```

  -  Go to **Tools -> Board -> Boards Manager**, search & install **RAKwireless RUI Apollo3 Boards**

<!-- ![image](https://github.com/BASSO-Jostin/RainGauge_BLE/blob/main/Picture/Apollo3_installation.PNG) -->
<img src="https://github.com/BASSO-Jostin/RainGauge_BLE/blob/main/Picture/Apollo3_installation2.PNG" height="450">

  -  Select **Tools -> Board -> RAKwireless RUI Apollo3 Boards -> WisBlock Core RAK11720 Board**
    
<!-- ![image](https://github.com/BASSO-Jostin/RainGauge_BLE/blob/main/Picture/Selection_of_Apollo3.png) -->
<img src="https://github.com/BASSO-Jostin/RainGauge_BLE/blob/main/Picture/Selection_of_Apollo3.png" height="450">


## The Things Network
- Depends on your country region and how you set up your gateway. Please create the correct application with it to be able to receive data. In Danang, the [**AS923_2**](https://ns.docs.everynet.io/channel_plans/AS920-923.html) band is used.
- To have access to The Things Network, click on [eu1.cloud.thethings.network](https://eu1.cloud.thethings.network/console/)
- Click on **Applications**, then **+ Add Application** and you **create application** for RainGauge Board : 
  
![image](https://github.com/BASSO-Jostin/RainGauge_BLE/blob/main/Picture/application_creation.PNG)

- Select **end device -> Register end device** to create your device
  
![image](https://github.com/BASSO-Jostin/RainGauge_BLE/blob/main/Picture/Version_lorawan1.png)

![image](https://github.com/BASSO-Jostin/RainGauge_BLE/blob/main/Picture/Version_lorawan_end.PNG)

- After creating the device, now you just need to copy **Device address, NwkSKey, AppSKey** and paste it into your code.
  
![image](https://github.com/BASSO-Jostin/RainGauge_BLE/blob/main/Picture/Arduino_and_TTN_sucess2.PNG)

- The data sent will be in the default format
  
![image](https://github.com/BASSO-Jostin/RainGauge_BLE/blob/main/Picture/Receive_information_wrong_format.PNG)

- You can change the format of the data to be able to observe changes, copy text on [TTN_formatters.txt](https://github.com/FabienFerrero/RainGauge_BLE/blob/main/TTN_fomatters.txt) and copy as below : 
  
![image](https://github.com/BASSO-Jostin/RainGauge_BLE/blob/main/Picture/Format_change.PNG)

![image](https://github.com/XuanMinh201/RainGauge/assets/75436464/bacd2547-f00b-4ce3-921c-7f5aad7f8b5a)

## Energy consumption
- The average energy consumption when the device is operating (sending data to the server) is **8.36mA** for **~15s**.
  
- ![image](https://github.com/XuanMinh201/RainGauge/assets/75436464/788eb731-e495-4512-936f-1b925529a2cb)

- When the device is inactive, it will be in sleep mode. Power consumption is **6.81 uA**
  
![image](https://github.com/XuanMinh201/RainGauge/assets/75436464/86c0f74d-2d5f-4a63-b74b-9b4ac87fee55)

### If you have any question or discussion points, please let me know via the [Issues](https://github.com/XuanMinh201/RainGauge/issues) & [Disscussions](https://github.com/XuanMinh201/RainGauge/discussions)





