#include <LiquidCrystal.h>
#include <SoftwareSerial.h>
#include <DHT.h>
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

SoftwareSerial GSM(8, 9); // SIM800L Tx & Rx is connected to Arduino #8 & #9

char phone_no[]="+243975465963"; // Change +92 with country code and 3378655465 with phone number to sms

char inchar; // Will hold the incoming character from the GSM shield

#define DHTPIN 7 // Pin connecté au capteur DHT11
#define DHTTYPE DHT11 // Type de capteur DHT11

DHT dht(DHTPIN, DHTTYPE);


float temperature, humidite;

void setup() {
  Serial.begin(9600); // Begin serial communication with Arduino and Arduino IDE (Serial Monitor)
  GSM.begin(9600); // Begin serial communication with Arduino and SIM800L

  initModule("AT", "OK", 1000); // Once the handshake test is successful, it will back to OK
  initModule("ATE1", "OK", 1000); // This command is used for enabling echo
  initModule("AT+CPIN?", "READY", 1000); // This command is used to check whether SIM card is inserted in GSM Module or not
  initModule("AT+CMGF=1", "OK", 1000); // Configuring TEXT mode
  initModule("AT+CNMI=2,2,0,0,0", "OK", 1000); // Decides how newly arrived SMS messages should be handled

  dht.begin(); // Initialisation du capteur DHT11
  lcd.begin(16,2); // Initialisation de l'écran LCD
  Serial.println("Initialized Successfully");
}

void loop() {
  // Lecture de la température et de l'humidité
     temperature = dht.readTemperature();
     humidite = dht.readHumidity();
  
  // Affichage des valeurs sur l'écran LCD
     lcd.clear();
     lcd.setCursor(0, 0);
     lcd.print("Temp: ");
     lcd.print(temperature);
     lcd.print((char)223); // Affichage du symbole °C
     lcd.setCursor(0, 1);   
     lcd.print("Hum: ");
     lcd.print(humidite);
     lcd.print("%");
            
  if (GSM.available() > 0) {
    inchar = GSM.read();
    Serial.print(inchar);

    if (inchar == 'B') {delay(10);
      inchar = GSM.read();
      if (inchar == 'E') {delay(10);
        inchar = GSM.read();
        if (inchar == 'B') {delay(10);
          inchar = GSM.read();
          if (inchar == 'E') {
            // Envoi du SMS
            sendSMS(phone_no, "Bonjour, la temperature est de", String(temperature).c_str(), " et l'humidite est de:", String(humidite).c_str());
          }
        }
      }
    }
  }
  delay(5);
}

void sendSMS(char *number, char *msg1, char *TEMP, char *msg2, char *HUM) {
  GSM.print("AT+CMGS=\"");
  GSM.print(number);
  GSM.println("\"\r\n"); // AT+CMGS="Mobile Number" <ENTER> - Assigning recipient's mobile number
  delay(500);
  GSM.println(msg1);
  GSM.println(TEMP);
  GSM.println(msg2);
  GSM.println(HUM);
  GSM.write(byte(26)); // Ctrl+Z send message command (26 in decimal)
  delay(500);
}

void initModule(String cmd, char *res, int t) {
  while (1) {
    Serial.println(cmd);
    GSM.println(cmd);
    delay(100);
    while (GSM.available() > 0) {
      if (GSM.find(res)) {
        Serial.println(res);
        delay(t);
        return;
      } else {
        Serial.println("Error");
      }
    }
    delay(t);
  }
}
