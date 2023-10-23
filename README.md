# Proyecto en Arduino

[![Arduino-presentacion.jpg](https://i.postimg.cc/P5Rf0hmp/Arduino-presentacion.jpg)](https://postimg.cc/yD0zSMps)

### Integrantes

------------

- Daraio Camila.
- Dominguez Franco.

 
### Proyecto contador Binario.

------------

[![Arduino-2.png](https://i.postimg.cc/Zn1jXGs8/Arduino-2.png)](https://postimg.cc/n9GvDPJr)

###  Descripcion

------------


Hemos realizado modificaciones en la primera parte del proyecto, reemplazando los tres botones por un interruptor deslizante. Ahora, el Arduino muestra los números del 0 al 99 en los visualizadores de 7 segmentos de forma automática, sin necesidad de los botones. Además, si utilizamos la otra opción del interruptor, el Arduino mostrará los números primos.

También hemos añadido un sensor de temperatura y un motor de corriente continua al Arduino. Esto nos permite controlar la temperatura y evitar el sobrecalentamiento. Cuando el sensor detecta una temperatura elevada, el motor se enciende, y al mismo tiempo, se activa un LED rojo como indicador de advertencia.

------------

###  Funcion principal

------------

La función "loop" en el código de Arduino monitorea constantemente el estado de un interruptor deslizante conectado al pin 4 del Arduino. Cuando el interruptor cambia de apagado a encendido, el contador se incrementa y asegura que los números mostrados estén en el rango de 0 a 99. Si el número actual es primo, se muestra en un display. Además, el programa lee un sensor de temperatura (NTC) y monitorea la temperatura a través de una función llamada "monitoriza". Si la temperatura supera un nivel establecido, se enciende un LED rojo y se activa un motor para enfriar el sistema. Si la temperatura está por debajo del nivel, el LED y el motor se apagan. Esta función se ejecuta en un bucle continuo, lo que permite que el proyecto muestre números y controle la temperatura en función de la posición del interruptor y las condiciones de temperatura detectadas.

```cpp
void loop() {
  
  currentSwitchState = digitalRead(4);

  if (currentSwitchState == LOW && lastSwitchState == HIGH) {
    countDigit = (countDigit + 1) % 100;
    if (esPrimo(countDigit)) {
    // Muestra el número primo en el display
    printCount(countDigit);
    }
  } 
  else 
  {  
	countDigit = (countDigit + 1) % 100;
    printCount(countDigit);
  }
  
  medida=analogRead(ntc);
  monitoriza();
  if (medida>nivel){
    digitalWrite(led,HIGH);
    digitalWrite(motor,HIGH);}
   else{
      digitalWrite(led,LOW);
      digitalWrite(motor,LOW);
  }   
```

------------

###  Link al Proyecto

------------

[Link](https://www.tinkercad.com/things/i4w00k018sJ-tp-parte-2-/editel?sharecode=2ExBk70DXcq03s4Z7L7gS3aZWhCGc5nt2JdNow4ZJ7A)https://www.tinkercad.com/things/i4w00k018sJ-tp-parte-2-/editel?sharecode=2ExBk70DXcq03s4Z7L7gS3aZWhCGc5nt2JdNow4ZJ7A

------------

### Fuentes

------------
https://www.youtube.com/watch?v=_Ry7mtURGDE&list=PL7LaR6_A2-E11BQXtypHMgWrSR-XOCeyD&index=4&ab_channel=UTNFRA

https://www.youtube.com/watch?v=61xafTRPvuI&list=PL7LaR6_A2-E11BQXtypHMgWrSR-XOCeyD&index=2&ab_channel=UTNFRA

------------




