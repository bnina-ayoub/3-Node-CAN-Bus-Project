## CAN Bus Nodes-to-Gateway LEDs Control (**Beginner's Guide**)

This project demonstrates a basic implementation of CAN Bus communication between STM32F407G-DISC1 nodes and a gateway, controlling the internal LEDs on the STM32 boards based on user input.

**Features:**

* Three STM32F407G-DISC1 development boards.
* Each node has a potentiometer for controlling LEDs.
* User button on each node triggers LED update and transmits data via CAN Bus.
* STM32F407G-DISC1 gateway receives LED data and controls its own internal LED based on the received value.

**Hardware:**

* 3x STM32F407G-DISC1 development boards
* 2x Potentiometers
* 3x CAN Bus transceivers
* Jumper wires

**Software:**

* STM32CubeIDE
* C programming language

**Included Files:**

* `main.c`: Contains core application logic for both nodes and gateway.
* `stm32f4xx_hal.h`: STM32 HAL library header.
* `wiring_schematic.jpg`: Schematic diagram of the hardware connections.

**Building and Deploying the Project:**

* Install STM32CubeIDE and configure it for your specific STM32F407V development boards.
* Import this project into STM32CubeIDE.
* For the Gateway: Update the main.c file within the gateway/ folder with any necessary configuration changes (e.g., CAN Bus filtering based on NODE_ID).
* For each Node: Update the main.c file within the node/ folder with the appropriate BOARD value (e.g., #define BOARD 1 for the first node, #define BOARD 2 for the second, etc.).
* Build and deploy the code to your respective STM32F407G-DISC1 boards (gateway and each node).

**Hardware Connections (Refer to `wiring_schematic.jpg` for details):**

* Connect potentiometers to designated analog input pins on the STM32F407G-DISC1 boards.
* Connect user buttons to designated GPIO pins on the STM32F407V boards configured as interrupts.
* Connect CAN transceivers to the CAN bus according to their datasheets.

![448650229_1495594784727386_3025306698575000307_n](https://github.com/bnina-ayoub/3-Node-CAN-Bus-Project/assets/94785911/b70bdabb-952f-4727-8b7c-27ce9e3d2f05)

**Understanding the Code:**

* The code utilizes STM32 HAL libraries to interact with peripherals like GPIO, ADC, and CAN.
* When a user presses a button on one of the nodes, the code triggers functions that:
    * Read the potentiometer value using the ADC.
    * Convert the potentiometer value to a number of LEDs to light.
    * Control the internal LEDs of the node by turning on the appropriate number of LEDs based on the converted value.
* CAN Bus communication functions are then used to transmit this number (representing the lit LEDs) as data to the gateway.
* The gateway receives the data from the node and adjusts its own internal LEDs to match the number of LEDs indicated by the received data. 

**Space for CAN Bus Filtering Demo GIF**

Consider including an animated GIF here that demonstrates how CAN Bus arbitration and filtering works. The GIF could show multiple CAN nodes transmitting messages with different identifiers, and a receiving node configured with a filter that only accepts messages with a specific identifier. This would visually represent how CAN Bus filtering allows devices to ignore irrelevant messages and focus on the data they need.

![CAN Filtering](https://github.com/bnina-ayoub/3-Node-CAN-Bus-Project/assets/94785911/8969044b-9344-463a-922d-401bfef65bd3)
