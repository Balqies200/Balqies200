#include <LiquidCrystal.h>
LiquidCrystal lcd(7,6,5,4,3,2);
const int moisture = A5;
int sensorValue = 0;
int moisture_value;
const int buzzer = 12;
const int LED = 8;

void setup() {
     lcd.begin(16, 2);
pinMode(moisture,INPUT);
pinMode(buzzer,OUTPUT);
pinMode(LED,OUTPUT);
}

void loop() {
    lcd.clear();
    lcd.setCursor(0,0);
  lcd.print("Soil Moisture : %");
sensorValue =analogRead(moisture);
 moisture_value=map(sensorValue,490,1023,0,100);
 lcd.setCursor(0,1);
lcd.print(moisture_value);

if(moisture_value >75)
{
  lcd.setCursor(0,1);
lcd.print("Help the plant!");
digitalWrite(buzzer,HIGH);
digitalWrite(LED,HIGH);
delay(500);
}else{
  digitalWrite(buzzer,LOW);
digitalWrite(LED,LOW);
}
delay(300);
}
