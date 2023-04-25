# Trabajo_Practico_n°1_SPD 🤖
![ArduinoTinkercad](https://user-images.githubusercontent.com/131720798/234136882-1d2f7633-e589-464f-85e3-a03955c779ee.jpg)

# Integrantes 👩‍🎓 👨‍🎓 👨‍🎓
- Abril Mariel Gonzalez Bernabeu

# Proyecto: Semaforo 🚦 🚦 
![Plaqueta_Arduino](https://user-images.githubusercontent.com/131720798/234137513-a1cdb3da-d713-4e2f-8134-00bdde433fa4.png)

# Descripcion 
El objetivo de este proyecto fue programar un semáforo utilizando una placa Arduino. El semáforo tenía como finalidad controlar el tráfico vehicular y peatonal tanto para los videntes y no videntes en una intersección.

Para llevar a cabo este proyecto, utilicé una placa Arduino UNO, tres LEDs para tres deferentes colores, 7 resistencias de 220 ohmios, una protoboard, un buzzer y varios cables.

Programé la placa Arduino utilizando el software de programación Arduino IDE. Utilicé un ciclo loop para controlar el cambio de los leds, de manera que el semáforo cambiara de rojo a amarillo, luego a verde y de nuevo a rojo. También programé una señal auditiva para indicar el cambio de luces y un juego de luces para anticipar el cambio de colores

El semáforo funciona de la siguiente manera: cuando se enciende, el led rojo se activa durante 30 segundos. Durante este tiempo, utilizando un bucle for, el buzzer comienza a emitir un sonido grave que ayuda a las personas no videntes a orientarse en relación al color del semáforo. En las últimas tres vueltas del bucle, se realiza un juego de luces que indica el cambio de color. Una vez transcurrido el tiempo programado se apaga y el led amarillo se enciende durante 5 segundos y el buzzer emite un sonido más suave, indicando que el semáforo está a punto de cambiar a verde. Luego, el led verde se enciende durante 45 segundos, y a los 39 segundos se inicia un juego de luces que indica que el led rojo volverá a encenderse y el ciclo se repetirá.
Adjunto una imagen del semáforo para que se pueda visualizar como fue el armado.

# Funcion principal
```c++
void prendeYApagaLed(int led1, int led2, int led3, int tiempo,int tiempo_Sumar, int cant_sonar, int tiempo_Low_Buzzer, int tiempo_High_Buzzer, int volumen){
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  if(led1 == 13 or led1 == 10){
  	power_buzzer(cant_sonar, tiempo_High_Buzzer, tiempo_Low_Buzzer, volumen, led1, led2, led3);
  }
  delay(tiempo);
  delay(tiempo_Sumar);
  if (led1 == 7){
    juego_luces(led1, led2, led3, 2000, 3); 
  }
   digitalWrite(led1, LOW);
   digitalWrite(led2, LOW);
   digitalWrite(led3, LOW);
   delay(500); 
}
```
# Funciones secundarias
```c++
void power_buzzer(int cant_sonar, int tiempo_High, int tiempo_Low, int volumen, int led1, int led2, int led3){
  for (int i = 0; i < cant_sonar; i++) {
  	tone(Buzzer, volumen);
    if (i > (cant_sonar - 4) and led1 != 10){
    	juego_luces(led1, led2, led3 , tiempo_High, 1);
    } else {
      delay(tiempo_High);
    }
  	noTone(Buzzer);
    delay(tiempo_Low);
  }
}

void juego_luces(int led1, int led2, int led3, int tiempo, int cant_Repe){
  for (int i = 0; i < cant_Repe; i++){
  	digitalWrite(led1, LOW);
    digitalWrite(led2, LOW);
    digitalWrite(led3, LOW);
  	delay(500);
  	digitalWrite(led1, HIGH);
    digitalWrite(led2, HIGH);
    digitalWrite(led3, HIGH);
  	delay(tiempo - 500);
    
  }
}
```
# Link del proyecto en tinkercad

https://www.tinkercad.com/things/9HaVi7WJy7A-copy-of-copy-of-dojo-n1/editel?sharecode=r-XE6Y5CDL-89dq2vVFMPSFs--67va51xG0f-D6MzyQ

# Link del proyecto en GDB

https://onlinegdb.com/_fcqYVoWv
