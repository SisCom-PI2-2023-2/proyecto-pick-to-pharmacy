---
layout: post
categories: posts
---
#Bitacora

##Semana 1  
En la semana del 12 y 14 de septiembre, una vez ya definidido lo que se iba a hacer, se empezaron a definir los actuadores a utilizar y realizar sus respectivas pruebas de concepto.
En estos dias se consiguieron los sensores de distancia HC SR04 y el RFID. Se buscó en internet un código para ver como funcionaban, siendo estos:
- Para el sensor de distancia:
```c++
#define trig 4
#define echo 5

long duration;
int distance;

void setup() {
    pinMode(trig, OUTPUT);  
    pinMode(echo, INPUT);
    Serial.begin(19200);
}

void loop() {
   // Clears the trigPin
  digitalWrite(trig, LOW);
  delayMicroseconds(2);
  // Sets the trigPin on HIGH state for 10 micro seconds
  digitalWrite(trig, HIGH);
  delayMicroseconds(10);
  digitalWrite(trig, LOW);
  // Reads the echoPin, returns the sound wave travel time in microseconds
  duration = pulseIn(echo, HIGH);
  // Calculating the distance
  distance = duration * 0.034 / 2;
  // Prints the distance on the Serial Monitor
  Serial.print("Distance: ");
  Serial.println(distance); 

}
```
- Para el RFID:
```c++
#include <SPI.h>
#include <MFRC522.h>   //GithubCommunity Version 1.4.10

#define RST_PIN  0    //Pin 9 para el reset del RC522
#define SS_PIN  15   //Pin 10 para el SS (SDA) del RC522
MFRC522 mfrc522(SS_PIN, RST_PIN); //Creamos el objeto para el RC522

void setup() {
  Serial.begin(9600); //Iniciamos la comunicación  serial
  SPI.begin();        //Iniciamos el Bus SPI
  mfrc522.PCD_Init(); // Iniciamos  el MFRC522
  Serial.println("Lectura del UID");
}

void loop() {
  // Revisamos si hay nuevas tarjetas  presentes
  if ( mfrc522.PICC_IsNewCardPresent()) 
        {    Serial.println("Lectura del UID");

      //Seleccionamos una tarjeta
            if ( mfrc522.PICC_ReadCardSerial()) 
            {
                  // Enviamos serialemente su UID
                  Serial.print("Card UID:");
                  for (byte i = 0; i < mfrc522.uid.size; i++) {
                          Serial.print(mfrc522.uid.uidByte[i] < 0x10 ? " 0" : " ");
                          Serial.print(mfrc522.uid.uidByte[i], HEX);   
                  } 
                  Serial.println();
                  // Terminamos la lectura de la tarjeta  actual
                  mfrc522.PICC_HaltA();         
            }      
  } 
}
```
