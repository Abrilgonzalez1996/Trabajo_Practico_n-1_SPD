<h1 align= "center">Trabajo Practico N°1 SPD 🤖</h1>

<p align="center">
   <img src= "https://user-images.githubusercontent.com/131720798/234136882-1d2f7633-e589-464f-85e3-a03955c779ee.jpg" />
</p>

# Integrantes 👩‍🎓 
- Abril Mariel Gonzalez Bernabeu

# Proyecto: Semaforo 🚦 🚦 🚦 
![Plaqueta_Arduino](https://user-images.githubusercontent.com/131720798/234137513-a1cdb3da-d713-4e2f-8134-00bdde433fa4.png)

# Descripcion 
El objetivo de este proyecto fue programar un semáforo utilizando una placa Arduino. El semáforo tenía como finalidad controlar el tráfico vehicular y peatonal tanto para los videntes y no videntes en una intersección.

Para llevar a cabo este proyecto, utilicé una placa Arduino UNO, tres LEDs para tres deferentes colores, 7 resistencias de 220 ohmios, una protoboard, un buzzer y varios cables.

Programé la placa Arduino utilizando el lenguaje de programación C++. Utilicé un ciclo loop para controlar el cambio de los leds, de manera que el semáforo cambiara de rojo a amarillo, luego a verde y de nuevo a rojo. También programé una señal auditiva para indicar el cambio de luces y un juego de luces para anticipar el cambio de colores

El semáforo funciona de la siguiente manera: cuando se enciende, el led rojo se activa durante 30 segundos. Durante este tiempo, utilizando un bucle for, el buzzer comienza a emitir un sonido grave que ayuda a las personas no videntes a orientarse en relación al color del semáforo. En las últimas tres vueltas del bucle, se realiza un juego de luces que indica el cambio de color. Una vez transcurrido el tiempo programado se apaga y el led amarillo se enciende durante 5 segundos y se apaga. Luego, el led verde se enciende durante 45 segundos, y a los 39 segundos se inicia un juego de luces que indica que el led rojo volverá a encenderse y el ciclo se repetirá.

# Funcion principal
Esta funcion se encarga de encender y apagar las leds
```c++
void high_Low_Led(int led, int tiempo_High, int tiempo_Low, int tiempo_Sumar){
  digitalWrite(led, HIGH);
  delay(tiempo_High);
  delay(tiempo_Sumar);
  if(led == 13){
  	power_buzzer(30, 500, 500, 100, led);//Se pasan por parametro las led rojas para emitir sonido
  } else if(led == 11){
    power_buzzer(2, 500, 2000, 1000, led);//Se pasan por parametro las led amarillas para emitir sonido
  } else if(led == 9){
    juego_luces(Led_Green, 500, 3); //Se manda por parametro las led verdes para producir el juego de luces
  }
  digitalWrite(led, LOW);
  delay(tiempo_Low); 
}
```
# Funciones secundarias
Esta funcion se encarga de emitir el sonido del buzzer:
```c++
void power_buzzer(int cant_sonar, int tiempo_High, int tiempo_Low, int volumen, int led){
  for (int i = 0; i < cant_sonar; i++) {
  	tone(Buzzer, volumen);
    if (i > (cant_sonar - 4) and led != 11){
    	juego_luces(led, 0, 1); 
    } else {
      delay(tiempo_High);
    }
  	noTone(Buzzer);
    delay(tiempo_Low);
  }
}
```
Esta funcion de encarga de hacer un juego de luces:
```c++
void juego_luces(int led, int tiempo, int cant_Repe){
  for (int i = 0; i < cant_Repe; i++){
  	digitalWrite(led, LOW);
  	delay(500);
  	digitalWrite(led, HIGH);
  	delay(tiempo);   
  }
}
```
# Link del proyecto en tinkercad

- https://www.tinkercad.com/things/eFJjnyoYpGR-copy-of-original/editel?sharecode=CXT_Z8BpmwZd4BCv30N3PDvQAlwPVJXEZdbr5kalpS4

# Link del codigo del proyecto en GDB

- https://onlinegdb.com/vj76tVpMA
