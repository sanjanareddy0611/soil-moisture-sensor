#define relay 8

#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);
void setup() 
{
   pinMode(A1, INPUT);
   pinMode(A0, INPUT);
      pinMode(11, OUTPUT);
      pinMode(relay, OUTPUT);

  lcd.print("Smart Irrigation");

  delay(2000);

  lcd.clear();
}


void loop() 
{   
unsigned int a,b;
        a= analogRead(A1);
       lcd.setCursor(0,0);
       lcd.print("Moisture=");
lcd.print(a);
       lcd.print("%       ");
       delay(500);
       
       delay(500);
if(a>=60)
       {
          digitalWrite(11, HIGH);

              lcd.setCursor(0,1);

       lcd.print("High Moisture         ");
       digitalWrite(relay, HIGH);

           }
           if(a<=59)
           {
            digitalWrite(relay, LOW);
            lcd.setCursor(0,1);

       lcd.print("Low Moisture           ");
           }
           
      
}

