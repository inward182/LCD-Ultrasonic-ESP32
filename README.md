# LCD Ultrasonic ESP32
## Descripción
### En este repositorio se muestra como  podemos programar la pantalla LCD con lo anteriormente programado con el ESP32, un Ultrasonic Distance Sensor y una pantalla LCD, se actualiza cada 2 segundos, y se tienen que agregar la librería de la pantalla de liquid crystal y también en el código se tiene que iniciar la pantalla. 
## Material Necesario
- wokwi
- ESP32
- Ultrasonic Distance Sensor
- lcd1602
## Programación
```
const int Trigger = 4;   //Pin digital 2 para el Trigger del sensor
const int Echo = 15;   //Pin digital 3 para el Echo del sensor
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4
LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);


void setup() {
  Serial.begin(9600);//iniciailzamos la comunicación
  pinMode(Trigger, OUTPUT); //pin como salida
  pinMode(Echo, INPUT);  //pin como entrada
  digitalWrite(Trigger, LOW);//Inicializamos el pin con 0
  lcd.init();
  lcd.backlight();
}

void loop()
{

  long t; //timepo que demora en llegar el eco
  long d; //distancia en centimetros

  digitalWrite(Trigger, HIGH);
  delayMicroseconds(10);          //Enviamos un pulso de 10us
  digitalWrite(Trigger, LOW);
  
  t = pulseIn(Echo, HIGH); //obtenemos el ancho del pulso
  d = t/59;             //escalamos el tiempo a una distancia en cm
  
  Serial.print("Distancia: ");
  Serial.print(d);      //Enviamos serialmente el valor de la distancia
  Serial.print("cm");
  Serial.println();
  delay(1000);          //Hacemos una pausa de 100ms

lcd.clear();
  lcd.setCursor(2,0);
  lcd.print("Diplomado V");
  lcd. setCursor(2,1);
  lcd.print("Mecatronica");
  delay(2000);
  

   lcd.clear();
  lcd.setCursor(1,0);
  lcd.print("Guillermo Hdz");
  lcd. setCursor(2,1);
  lcd.print("Ing Mecanica");
  delay(2000);

  
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("Distancia " + String(d) + " cm");
  delay(2000);
}
 ```
## Librerías

1. LiquidCrystal I2C

## Conexión

![image](https://github.com/user-attachments/assets/6a983b55-4e03-4c79-a382-bd937eff4bc0)


##Instrucciones de operación 

1. Iniciar Simulador
2. Visualizar los datos en la pantalla LCD
3. Subir y Bajar la distancia dando doble click al sensor ultrasonico de distancia

## Resultados

Cuando funcione y Corra los valores serán mostrados en la pantalla LCD, cada 2 segundos se actualizará, mostrará primero el número del modulo, el nombre del diplomado. Luego mostrará mi nombre y mi carrera, y finalmente mostrará la distancia

![image](https://github.com/user-attachments/assets/8cc769f7-83d4-408d-ad1a-2a8a4a764edf)

![image](https://github.com/user-attachments/assets/16781783-f086-41c9-b172-6589de403d4d)


## Desarrollado por

Guillermo de Jesús Hernández Yáñez
[GitHub](https://github.com/inward182)
