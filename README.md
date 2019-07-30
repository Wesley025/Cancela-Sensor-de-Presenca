# Cancela-Sensor-de-Presenca
Nesse projeto trago uma cancela com sensor e led´s indicadores

#include <Servo.h> //Inclui a biblioteca para o servo motor

Servo meuServo;
int SensorPIR = 7;
 
void setup() 
{
  pinMode(SensorPIR, INPUT_PULLUP); // define o sensor como saidas 
}
 
void loop() 
{
  meuServo.attach(9);
  if(digitalRead(SensorPIR) == HIGH)
  {
    digitalWrite( 1, HIGH);
    digitalWrite( 8, LOW);
    for(int angulo=0; angulo<=90; angulo++) // Aumenta o angulo do servo ate chegar em 180 graus
    {
      meuServo.write(angulo);
      delay(100);
    }
    for(int angulo=90; angulo>=0; angulo--)// Diminui o angulo do servo
    {
      meuServo.write(angulo);
      delay(150);
    }
  }
  meuServo.detach();
  if(digitalRead(SensorPIR) == LOW);
    digitalWrite( 8, HIGH);
  digitalWrite( 1, LOW);
}
