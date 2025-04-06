# TSC_project
Pentru acest proiect am avut de implementat PCBul unui ebook reader si asamblarea acestuia in carcasa alaturi de o baterie si display.
Primul pas al proiectului a fost creearea schemei electrice ce consta in plasarea si conectarea componentelor.
Componenta principala este microcontrollerul ESP32-C6 care gestioneaza și coordoneaza functionarea celorlalte componente:
* SAMACSYS_PARTS_USB4110-GF-AUSB4 conectat la pinii 13 (USB_D-) si 14 (USB_D+) folosit pentru incarcarea bateriei
* QWIIC_RIGHT_ANGLE conectat la pinii 19 (SDA) si 20 (SCL), controleaza senzorul BME680 ce masoara temperatura/calitatea aerului/umiditate, folosit pentru energy management
* 112A-TAAR-R03_ATTEND port pentru card sd, folosit pentru transfer de date este conectat la pinii 4 (SS_SD), 6 (SCK), 7 (MOSI), 27 (MISO) 
* FH34SRJ-24S-0.5SH_99_ header pentru display conectat la pinii 7 (MOSI), 6 (SCK), 11 (EPD_CS), 5 (EPD_DC), 21 (EPD_RST), 26 (EPD_BUSY)
* W25Q512JVEIQ flash extern 64MB folosit pentru stocare de date conectat la pinii 6 (SCK), 7 (MOSI), 27 (MISO), 12 (FLASH_CS)
* 3 butoane CHANGE, RESET si BOOT conectate la pinii 23 (IO/CHANGE), 3 (RESET), 15 (IO/BOOT)
* DS3231SN# RTC module (real-time clock) conectat la pinii 8 (INT_RTC), 19 (SDA), 20 (SCL), 9 (32KHZ), 16 (RTC_RST)
* ESP32_WROVER_SPARKFUN-IC-POWER_MCP73831 controller pentru incarcarea bateriei
  
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


![OpenBookDiagram](https://github.com/user-attachments/assets/0c7cf70c-b92d-4d52-825a-fe6e54214325)
