#include <Wire.h> 
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27,16,2);  // set the LCD address to 0x27 for a 16 chars and 2 line display
#include <Stepper.h>
#include "VirtuinoBluetooth.h"
#include <SoftwareSerial.h>
SoftwareSerial bluetoothSerial =  SoftwareSerial(2,3);
VirtuinoBluetooth virtuino(bluetoothSerial);
const int stepsPerRevolution = 200;  // change this to fit the number of steps per revolution
// for your motor

// initialize the stepper library on pins 8 through 11:
Stepper myStepper(stepsPerRevolution, 9, 11, 10, 12);
void setup()
{
  virtuino.DEBUG=true;
    bluetoothSerial.begin(9600); 
  pinMode(8, OUTPUT);
digitalWrite(8, HIGH);  
  pinMode(7, OUTPUT);
  pinMode(6, OUTPUT);
  pinMode(8, OUTPUT);
  myStepper.setSpeed(100);
  pinMode(4,OUTPUT);
  lcd.init();     
  lcd.init();
  lcd.backlight();
  lcd.setCursor(0,0);
  lcd.print("Fire Fighting System");
  virtuino.vDelay(3000);
  lcd.clear();
}
void loop()
{
   virtuino.run();
      lcd.setCursor(0,0);
  lcd.print("Detecting Fire        ");
      int sensorValue = analogRead(A1);
       int sensorValue1 = analogRead(A0);
       int sensorValue2 = analogRead(A2);
       int sensorValue3 = analogRead(A3);
      if(sensorValue1 < 500)                                     //1111111
      {
        virtuino.vMemoryWrite(1,HIGH);
        digitalWrite(4,HIGH);
        virtuino.vDelay(100);
        digitalWrite(4,LOW);
        virtuino.vDelay(100);
         digitalWrite(4,HIGH);
        virtuino.vDelay(100);
        digitalWrite(4,LOW);
        virtuino.vDelay(100);
        lcd.setCursor(0,0);
  lcd.print("Fire Detected          ");
  digitalWrite(7, HIGH);   // turn the LED on (HIGH is the voltage level)
  virtuino.vDelay(100);                       // wait for a second
  digitalWrite(7, LOW);    // turn the LED off by making the voltage LOW
  virtuino.vMemoryWrite(3,HIGH);
        Serial.println("clockwise");
  myStepper.step(-stepsPerRevolution*20);
   digitalWrite(4,HIGH);
        virtuino.vDelay(100);
        digitalWrite(4,LOW);
        virtuino.vMemoryWrite(2,HIGH);
  virtuino.vDelay(2000);  
  // wait for a second
  digitalWrite(8, LOW);    // turn the LED off by making the voltage LOW
  virtuino.vDelay(800);
digitalWrite(8, HIGH);   // turn the LED on (HIGH is the voltage level)
 virtuino.vDelay(1000); 
 virtuino.vMemoryWrite(2,LOW);
  // step one revolution in the other direction:
  Serial.println("counterclockwise");
  myStepper.step(stepsPerRevolution*20);
  virtuino.vDelay(500);
  digitalWrite(6, HIGH);   // turn the LED on (HIGH is the voltage level)
  virtuino.vDelay(100);                       // wait for a second
  digitalWrite(6, LOW);
  virtuino.vMemoryWrite(3,LOW);
        digitalWrite(8, HIGH);   // turn the LED on (HIGH is the voltage level)
        digitalWrite(4,HIGH);
        virtuino.vDelay(100);
        digitalWrite(4,LOW);
        virtuino.vDelay(1000);
        virtuino.vMemoryWrite(1,LOW);
      }
      if(sensorValue < 500)                                //2222222
      {
        virtuino.vMemoryWrite(1,HIGH);
         digitalWrite(4,HIGH);
        virtuino.vDelay(100);
        digitalWrite(4,LOW);
        virtuino.vDelay(100);
         digitalWrite(4,HIGH);
        virtuino.vDelay(100);
        digitalWrite(4,LOW);
        virtuino.vDelay(100);
        lcd.setCursor(0,0);
  lcd.print("Fire Detected          ");
        Serial.println("clockwise");
        virtuino.vMemoryWrite(3,HIGH);
  myStepper.step(-stepsPerRevolution*20);
   digitalWrite(4,HIGH);
        virtuino.vDelay(100);
        digitalWrite(4,LOW);
        virtuino.vMemoryWrite(2,HIGH);
  virtuino.vDelay(2000);
digitalWrite(8, LOW);     //pump on
  virtuino.vDelay(1000);
digitalWrite(8, HIGH);  //pump off
  virtuino.vDelay(1000); 
  virtuino.vMemoryWrite(2,LOW);
  // step one revolution in the other direction:
  Serial.println("counterclockwise");
  myStepper.step(stepsPerRevolution*20);
  virtuino.vDelay(500);
        virtuino.vMemoryWrite(3,LOW);
        digitalWrite(4,HIGH);
        virtuino.vDelay(100);
        digitalWrite(4,LOW);
        virtuino.vDelay(1000);
        virtuino.vMemoryWrite(2,LOW);
      }
      if(sensorValue2 < 500)                                //3333333
      {
        virtuino.vMemoryWrite(1,HIGH);
         digitalWrite(4,HIGH);
        virtuino.vDelay(100);
        digitalWrite(4,LOW);
        virtuino.vDelay(100);
         digitalWrite(4,HIGH);
        virtuino.vDelay(100);
        digitalWrite(4,LOW);
        virtuino.vDelay(100);
        lcd.setCursor(0,0);
  lcd.print("Fire Detected          ");
    delay(1000);
   digitalWrite(4,HIGH);
        virtuino.vDelay(100);
        digitalWrite(4,LOW);
        virtuino.vMemoryWrite(2,HIGH);
  virtuino.vDelay(2000);
digitalWrite(8, LOW);     //pump on
  virtuino.vDelay(1000);
digitalWrite(8, HIGH);  //pump off
  virtuino.vDelay(1000); 
  virtuino.vMemoryWrite(2,LOW);
  // step one revolution in the other direction:
 delay(1000);
  virtuino.vDelay(500);
        virtuino.vMemoryWrite(3,LOW);
        digitalWrite(4,HIGH);
        virtuino.vDelay(100);
        digitalWrite(4,LOW);
        virtuino.vDelay(1000);
        virtuino.vMemoryWrite(2,LOW);
      }
      if(sensorValue3 < 500)                                     //44444444
      {
        virtuino.vMemoryWrite(1,HIGH);
        digitalWrite(4,HIGH);
        virtuino.vDelay(100);
        digitalWrite(4,LOW);
        virtuino.vDelay(100);
         digitalWrite(4,HIGH);
        virtuino.vDelay(100);
        digitalWrite(4,LOW);
        virtuino.vDelay(100);
        lcd.setCursor(0,0);
  lcd.print("Fire Detected          ");
  digitalWrite(7, HIGH);   // turn the LED on (HIGH is the voltage level)
  virtuino.vDelay(100);                       // wait for a second
  digitalWrite(7, LOW);    // turn the LED off by making the voltage LOW
  virtuino.vMemoryWrite(3,HIGH);
    delay(1000);
   digitalWrite(4,HIGH);
        virtuino.vDelay(100);
        digitalWrite(4,LOW);
        virtuino.vMemoryWrite(2,HIGH);
  virtuino.vDelay(2000);  
  // wait for a second
  digitalWrite(8, LOW);    // turn the LED off by making the voltage LOW
  virtuino.vDelay(800);
digitalWrite(8, HIGH);   // turn the LED on (HIGH is the voltage level)
 virtuino.vDelay(1000); 
 virtuino.vMemoryWrite(2,LOW);
  // step one revolution in the other direction:
  delay(1000);
  digitalWrite(6, HIGH);   // turn the LED on (HIGH is the voltage level)
  virtuino.vDelay(100);                       // wait for a second
  digitalWrite(6, LOW);
  virtuino.vMemoryWrite(3,LOW);
        digitalWrite(8, HIGH);   // turn the LED on (HIGH is the voltage level)
        digitalWrite(4,HIGH);
        virtuino.vDelay(100);
        digitalWrite(4,LOW);
        virtuino.vDelay(1000);
        virtuino.vMemoryWrite(1,LOW);
      }
 digitalWrite(8, HIGH);  //pump off     
}
