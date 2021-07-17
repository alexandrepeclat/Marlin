//Fichier compilé dans Marlin-bugfix-2.0.x\.pio\build\LPC1769\firmware.bin
//définit dans platformio.ini : default_envs = LPC1768 //LPC1769 en fait pour la skr 1.4 turbo
//à placer sur la carte sd
//si imprimante connectée via usb, le fichier est automatiquement placé sur la sd onboard si on clique "Upload"

//TODO : octoprint buffers ? http://lokspace.eu/bad-print-quality-with-usb-or-octoprint-the-solution-is-here/
//TODO : Nozzle park tool option ? 
//TODO : Fade height (activée dans fw mais pas sur printer)
//TODO : a voir #define SDCARD_CONNECTION LCD ou ONBOARD (selon doc TFT) 

/////////////////////////
//BLTouch
//Tuto marlin : https://all3dp.com/2/how-to-set-up-marlin-for-auto-bed-leveling/
//Tuto abl TeachingTech : https://www.youtube.com/watch?v=BV11-VOQjMc&t=134s 
//Commandes test manuel : http://www.geeetech.com/forum/viewtopic.php?f=27&t=18371

M851 ; Read offsets
M119 ; Endstop States
M48 ; Probe accuracy test
M420 V ; Mesh bed report

M280 P0 S10 ; pushes the pin down
M280 P0 S90 ; pulls the pin up
M280 P0 S120 ; Self test – keeps going until you do pin up/down or release alarm
M280 P0 S160 ; Release alarm

M401 ; Deploy probe
M402 ; Stow probe

G28 ; Auto-home
G29 ; Auto-probe (build mesh)
G26 ; Print mesh validation pattern

M500 ; Save eeprom
M501 ; Restore eeprom
M502 ; Factory reset


M997 ; Firmware update


/////////////////////
//TFT
//Firmware et doc de base : https://github.com/bigtreetech/BIGTREETECH-TouchScreenFirmware/tree/master
//