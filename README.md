# Lunar Garage Door
Like the moon,  
the garage door rises.  
Like the moon,  
the garage door sets.  
(it can also stop in the middle)  
_-ancient proverb._

Documentation for [CCHS](https://www.hackmelbourne.org/) garage door. Intended to:
1. Allow recreation of our card reader implimentation (e.g. for backdoor)
2. Allow future committee members to manage member access cards and review entries to CCHS.

## Software  
### Accessing the Web-Portal:
1. Connect to the CCHS wifi.
2. Swipe the garage door admin card, this will reboot the controller and prompt it to run the web-portal.
3. In your browser, enter the IP address [192.168.0.40](http://192.168.0.40)
4. The ESP-RFID web-portal should load. Enter the password. The password may be found in the passwords file accessable by the CCHS committee members.
5. Congratulations, you are now in the settings/configurations/logs!

### Adding a new card 
1. Check that the new user has signed a CCHS "Security and After-Hours Agreement."
3. Access the web-portal.
4. Navigate to Menu>Users>Add new user.
5. A blank 'card-details' element will pop up in the UI.
6. Go and swipe a card on the card reader. The card's details will load into the UI element.
7. Fill in the name of the card-holder-to-be, for access logging purposes.
8. Press 'save changes'.
9. Issue the card to the newest card-carrying member of the CCHS

### Checking the access logs
1. Navigate to Menu>Logs>Access Log.
2. Review as you like.

### Backing up the user details and controller settings: 
1. Navigate to Menu>Backup and Restore.
2. Press 'Backup User Data' & 'Backup Settings'
3. Store securely, please.

### To turn off the wifi or not?
The ESP-RFID provides the option to turn off the web-portal, meaning that the access system cannot be discovered by presumed bad-actors. It is a security recommendation of the ESP-RFID group to turn off the web portal. We have enabled this 'web-portal turn off', with a 10 minute 'sleep' timer. 

If turned off, the ESP-RFID controller can be restarted by swiping a card with 'admin' privileges. There is an admin card in the CCHS safe.

When the portal is active, the on-board LED is lit solidly. When the portal is deactivated, the on-board LED blinks.

**To turn on/off the web-portal with timer:**  
1. Navigate to Menu>Settings>Wireless network>Auto Disable Wifi.
2. Select the time limit of choice, or select 'never'.

### Assigning a static IP via Wifi router:
We encountered difficulties when the last number of the IP address of the ESP-RFID was low. The working hypothesis is that multiple devices were given the same IP adress, meaning we could not access the web-portal. We have given the ESP-RFID a static IP address. 

**How to change the static/assigned IP address:**  
1. Access the router's web-portal: [192.168.0.1](192.168.0.1)
2. The router's username and password may be found in the passwords file accessable by CCHS committee members.
3. (Do the wifi stuff, go to advanced>network>LAN settings>scroll down>address reservation>add) 

## Hardware  
For the brains, we are using the [ESP-RFID](https://github.com/esprfid/esp-rfid) project, specifically the ['blue-board'](https://github.com/esprfid/esp-rfid-board) version.  
For the actual card-reader, we are using the [Adafruit PN532 NFC/RFID controller](https://www.adafruit.com/product/364). 
The garage door (insert manual here) contains a 'dry-strike' contact. When the two terminals are connected, the garage door triggers with 'up', 'stop', and 'down' triggers. 
The nearest appropriate 12V wall-wart was employed to power the ESP-RFID board. A 12V supply is definitely needed, as the on-board relay does not engage if not so apporpriately powered. 

## Wiring
The ESP-RFID controller and card-reader were connected by a six core wire. The SPI protocol was used.  
The garage door's contacts were wired to the common and 'normally' open terminals of the controller's relay.  
The 12V power supply's terminals were connected to the '12V' and 'GND' terminals on the ESP-RFID's controller. All of these wires are terminated with crimped ferrels, as a point of pride.   
The terminals of the card-reader are not a point of pride, however, consisting of bent Dupont connectors soldered to a socket connecter to a block with screw-down terminals. As they say, _there's nothing more permanent than a quick fix._

## Mounting
