# **RFID Lock System Using Arduino**
This project implements an RFID-based access control system using an Arduino and a serial RFID reader. The system can **add**, **delete**, and **verify** RFID cards, with all authorized card IDs stored in EEPROM for persistent memory.
---
## **Features**
* ✔ **Add new RFID cards** using the “Add” button
* ✔ **Delete existing RFID cards** using the “Delete” button
* ✔ **Store up to 10 authorized cards** in EEPROM
* ✔ **Unlock relay** for a preset duration when a valid card is detected
* ✔ **LED and buzzer indicators** for OK or ERROR feedback
* ✔ **EEPROM-based storage**, so authorized cards remain saved even after power loss
---
## **How It Works**
1. When an RFID card is scanned, the Arduino reads its data.
2. Depending on the pressed button:
   * **Add Mode** → Stores the new card if memory space is available
   * **Delete Mode** → Removes the card from memory
   * **Normal Mode** → Compares the scanned card with stored IDs
3. If the card is authorized:
   * The **relay activates**, unlocking the door for the configured time
   * A blinking LED and buzzer indicate success
4. If unauthorized, an error LED and buzzer are triggered.
---
## **Hardware Used**
* Arduino (Uno/Nano compatible)
* Serial RFID reader (9600 baud)
* Relay module (controlled via A0)
* Buzzer
* Status LEDs (OK and ERROR)
* Push buttons (Add / Delete)
* EEPROM (built-in)
---
## **Pin Configuration**
| Component     | Arduino Pin                 |
| ------------- | --------------------------- |
| Relay         | A0                          |
| Buzzer        | 13                          |
| Add Button    | 12                          |
| Delete Button | 11                          |
| OK LED        | VCC: 5, GND: 4              |
| Error LED     | VCC: 9, GND: 8              |
| RFID Reader   | SoftwareSerial (RX=2, TX=3) |
---
## **Core Functions**
* **Check_in()** → Reads incoming RFID data
* **Add_card()** → Saves a new card to EEPROM
* **Delete_card()** → Removes a card from EEPROM
* **check_in_Mode()** → Normal card verification
* **EEP_Write_String() / EEP_Read_String()** → EEPROM handling
* **_OK() / _ERROR()** → Feedback indicators
---
## **EEPROM Structure**
The EEPROM stores up to **10 card IDs**, each occupying a 32-byte block.
Slot 11 is used as a reference for empty space detection.
---
## **Usage**
1. Power on the system.
2. **To add a new card:**
   * Press *Add* button
   * Scan the RFID card
3. **To delete a card:**
   * Press *Delete* button
   * Scan the RFID card
4. **To use normally:**
   * Scan the RFID card without pressing any buttons
---

