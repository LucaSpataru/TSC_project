# TSC_project
Pentru acest proiect am avut de implementat PCBul unui ebook reader si asamblarea acestuia in carcasa alaturi de o baterie si display.
Primul pas al proiectului a fost creearea schemei electrice ce consta in plasarea si conectarea componentelor.
Componenta principala este microcontrollerul ESP32-C6 care gestioneaza și coordoneaza functionarea celorlalte componente.
# Pini folositi
| Componentă                            | Pini ESP C6                         | Funcție                                                       |
|--------------------------------------|-------------------------------------|---------------------------------------------------------------|
| SAMACSYS_PARTS_USB4110-GF-AUSB4      | 13 (USB_D-), 14 (USB_D+)            | Încărcare baterie via USB                                     |
| QWIIC_RIGHT_ANGLE + BME680           | 19 (SDA), 20 (SCL)                  | Măsurare temperatură, calitate aer, umiditate (energy mgmt)  |
| 112A-TAAR-R03_ATTEND (SD card port)  | 4 (SS_SD), 6 (SCK), 7 (MOSI), 27 (MISO) | Transfer de date (card SD)                                 |
| FH34SRJ-24S-0.5SH_99_ (Display header)| 7 (MOSI), 6 (SCK), 11 (EPD_CS), 5 (EPD_DC), 21 (EPD_RST), 26 (EPD_BUSY) | Conectare display          |
| W25Q512JVEIQ (64MB Flash extern)     | 6 (SCK), 7 (MOSI), 27 (MISO), 12 (FLASH_CS) | Stocare de date                                       |
| Butoane (CHANGE, RESET, BOOT)        | 23 (IO/CHANGE), 3 (RESET), 15 (IO/BOOT) | Interfață utilizator (comenzi)                          |
| DS3231SN# (RTC module)               | 8 (INT_RTC), 19 (SDA), 20 (SCL), 9 (32KHZ), 16 (RTC_RST) | Ceas în timp real                              |

  
De asemenea sunt implementate test paduri, un regulator de tensiune si linii de protectie pentru a putea asigura functionarea corecta a dispozitivului.

Urmatoarul pas a constat in aranjarea componentelor pe placa, decuparea acesteia pentru a se potrivi in carcasa si pentru a nu incurca alte componente precum microcontrollerul si butoanele,
rutarea semnalelor si desenarea planului de masa pe fata si pe spate.
Am intampinat unele probleme precum marimea padurilor pentru componenta MAX17048G+T10 care nu se potriveau cu regulile de rutare, si marimea padurilor bobinei care erau prea mici - am modificat footprintul componentelor.
Am dat approve la 2 erori comune de tip Board Outline Clearance pentru mufa USB4.
Am plasat componentele cat mai eficient, si de asemenea am aranjat ca numele componentelor sa fie vizibile pe silkscreen.

Mai departe am cautat pentru fiecare componenta folosita modele 3D unde am comparat footprinturile pieselor gasite pentru a alege modelul corespunzator.

Ultimul pas a constat in partea 3D unde am plasat placa in carcasa, aici am facut o modificare ce se poate observa in imaginile buttons_mod, deoarece felul in care am pus butoanele se intersectau cu o bucata de plastic
care am micsorat-o. Butoanele ar trebuii sa functioneze fara probleme acum.
Dupa ce m-am asigurat ca mufele sunt aliniate cu componentele ce ies de pe placa, am creeat un model de baterie si unul de display si le-am aranjat si pe acestea in interiorul dispozitivului.

In cele din urma am generat fisierele BOM, PNP si gerbers care se afla in fisierul Manufacturing.
De asemenea am realizat o animatie cu exploded view, dar si un fisier .step cum este specificat in cerinta.
# BOM
| Componentă                     | Link de cumpărare |
|----------------------------|-------------------|
| ADAFRUIT_LEDCHIP-LED0603   | [Mouser](https://ro.mouser.com/ProductDetail/ams-OSRAM/KW-EELP41.RU-S1U1-3K6L-3X4X-5-R18?qs=sGAEpiMZZMt82OzCyDsLFIOEctO0UgBCyNaG5LP3KGg%3D)                 |
| SJ                         | [Mouser](https://ro.mouser.com/ProductDetail/Chip-Quik/WWSWLT.040-200g?qs=i8QVZAFTkqRTFq30mTreAQ%3D%3D)                 |
| CPH3225A (Supercapacitor)  | [Mouser](https://ro.mouser.com/ProductDetail/Seiko-Semiconductors/CPH3225A?qs=3etwrb1wR%252BhUOph6lAO7eg%3D%3D) |
| DS3231SN# (RTC)           | [SnapEDA](https://www.snapeda.com/parts/DS3231SN%23/Analog+Devices/view-part/?ref=eda) |
| ESP32-C6-WROOM-1-N8       | [SnapEDA](https://www.snapeda.com/parts/ESP32-C6-WROOM-1-N8/Espressif+Systems/view-part/?ref=eda) |
| FH34SRJ-24S-0.5SH_99_     | [Mouser](https://www.mouser.co.uk/ProductDetail/Hirose-Connector/FH34SRJ-24S-0.5SH99?qs=vcbW%252B4%252BSTIpKBl5ap9J8Fw%3D%3D) |
| MAX17048G+T10 (Fuel Gauge)| [SnapEDA](https://www.snapeda.com/parts/MAX17048G+T10/Analog+Devices/view-part/?ref=eda) |
| MBR0530 (Schottky Diode)  | [SnapEDA](https://www.snapeda.com/parts/MBR0530/Onsemi/view-part/?ref=eda) |
| PGB1010603MR (TVS Diode)  | [SnapEDA](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) |
| SI1308EDL-T1-GE3 (MOSFET) | [SnapEDA](https://www.snapeda.com/parts/SI1308EDL-T1-GE3/Vishay+Siliconix/view-part/?ref=eda) |
| USBLC6-2SC6Y (ESD Protection)| [SnapEDA](https://www.snapeda.com/parts/USBLC6-2SC6Y/STMicroelectronics/view-part/?ref=eda) |
| W25Q512JVEIQ (Flash Memory)| [SnapEDA](https://www.snapeda.com/parts/W25Q512JVEIQ/Winbond+Electronics/view-part/?ref=eda) |
| XC6220A331MR-G (LDO Regulator)| [Mouser](https://www.mouser.co.uk/ProductDetail/Torex-Semiconductor/XC6220A331MR-G?qs=AsjdqWjXhJ8ZSWznL1J0gg%3D%3D) |
| BD5229G-TR (Voltage Detector)| [Mouser](https://www.mouser.co.uk/ProductDetail/ROHM-Semiconductor/BD5229G-TR?qs=4kLU8WoGk0vvnhrrYwdszw%3D%3D) |
| BME680 (Environmental Sensor)| [Mouser](https://ro.mouser.com/ProductDetail/Bosch-Sensortec/BME680?qs=v271MhAjFHjo0yA%2FC4OnDQ%3D%3D)                 |
| 112A-TAAR-R03_ATTEND (SD Card Socket)| [DigiKey](https://www.digikey.ro/en/products/detail/attend-technology/112A-TAAR-R03/17633923)                 |

# Diagrama
![OpenBookDiagram](https://github.com/user-attachments/assets/0c7cf70c-b92d-4d52-825a-fe6e54214325)
