# HC-06---HC-05

Esquema PINES

VCC → 5V (o 3.3V según el módulo)
GND → GND
TXD → Pin 1 de Arduino
RXD → Pin 0 de Arduino
Teneis una foto de como tendria que quedar. (pines.png)


Una vez pineado, empieza a parpadear una luz roja, cada HC tiene un numero, azules son 51,52 etc y los verdes 61,62 etc. Entramos en el bluethoot del movil y nos conectamos, la contraseña es 0000 o 1234.


#include <SoftwareSerial.h>   // Incluimos la librería  SoftwareSerial  
SoftwareSerial BT(8,2);    // Definimos los pines RX y TX del Arduino conectados al Bluetooth
 
void setup()
{
  BT.begin(9600);       // Inicializamos el puerto serie BT (Para Modo AT 2)
  Serial.begin(9600);
  Serial.println("listo"); 
   
}
 
void loop()
{
  if(BT.available())    // Si llega un dato por el puerto BT se envía al monitor serial
  {
    Serial.write(BT.read());
  }
 
  if(Serial.available())  // Si llega un dato por el monitor serial se envía al puerto BT
  {
     BT.write(Serial.read());
  }
}


