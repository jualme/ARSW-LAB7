# ARSW-LAB7

## Members 
- **Juan Alberto Mejía Schuster**
- **Johann Sebastian Páez Campos**
# Broker de Mensajes STOMP

## Descripción

Este ejercicio se basa en la documentación oficial de SprinbBoot, para el manejo de WebSockets con STOMP.

En este repositorio se encuentra una aplicación SpringBoot que está configurado como Broker de mensajes, de forma similar a lo mostrado en la siguiente figura:

/todo image

En este caso, el manejador de mensajes asociado a "/app" aún no está configurado, pero sí lo está el broker '/topic'. Como mensaje, se usarán puntos, pues se espera que esta aplicación permita progragar eventos de dibujo de puntos generados por los diferentes clientes.

## Parte 1

Para las partes I y II, usted va a implementar una herramienta de dibujo colaborativo Web, basada en el siguiente diagrama de actividades:

![](https://github.com/jualme/ARSW-LAB7/blob/master/img/P1-AD.png)

Para esto, realice lo siguiente:

  - Haga que la aplicación HTML5/JS al ingresarle en los campos de X y Y, además de graficarlos, los publique en el tópico: /topic/newpoint . Para esto tenga en cuenta 
  
    (1) Usar el cliente STOMP creado en el módulo de JavaScript y (2) enviar la representación textual del objeto JSON (usar JSON.stringify). Por ejemplo:
    
 ```java   
//creando un objeto literal
stompClient.send("/topic/newpoint", {}, JSON.stringify({x:10,y:10}));
```
```java
//enviando un objeto creado a partir de una clase
stompClient.send("/topic/newpoint", {}, JSON.stringify(pt)); 
```

  (2) Dentro del módulo JavaScript modifique la función de conexión/suscripción al WebSocket, para que la aplicación se suscriba al tópico "/topic/newpoint" (en lugar del tópico /TOPICOXX). Asocie como 'callback' de este suscriptor una función que muestre en un mensaje de alerta (alert()) el evento recibido. Como se sabe que en el tópico indicado se publicarán sólo puntos, extraiga el contenido enviado con el evento (objeto JavaScript en versión de texto), conviértalo en objeto JSON, y extraiga de éste sus propiedades (coordenadas X y Y). Para extraer el contenido del evento use la propiedad 'body' del mismo, y para convertirlo en objeto, use JSON.parse. Por ejemplo:
  
```java
var theObject=JSON.parse(message.body);
```

   (3) Compile y ejecute su aplicación. Abra la aplicación en varias pestañas diferentes (para evitar problemas con el caché del navegador, use el modo 'incógnito' en cada prueba).
  
   (4) Ingrese los datos, ejecute la acción del botón, y verifique que en todas la pestañas se haya lanzado la alerta con los datos ingresados.
  
   (5) Haga commit de lo realizado, para demarcar el avance de la parte 2.
  
```
git commit -m "PARTE 1".Para esto, realice lo siguiente:

Haga que la aplicación HTML5/JS al ingresarle en los campos de X y Y, además de graficarlos, los publique en el tópico: /topic/newpoint . Para esto tenga en cuenta (1) usar el cliente STOMP creado en el módulo de JavaScript y (2) enviar la representación textual del objeto JSON (usar JSON.stringify). Por ejemplo:

//creando un objeto literal
stompClient.send("/topic/newpoint", {}, JSON.stringify({x:10,y:10}));
//enviando un objeto creado a partir de una clase
stompClient.send("/topic/newpoint", {}, JSON.stringify(pt)); 
Dentro del módulo JavaScript modifique la función de conexión/suscripción al WebSocket, para que la aplicación se suscriba al tópico "/topic/newpoint" (en lugar del tópico /TOPICOXX). Asocie como 'callback' de este suscriptor una función que muestre en un mensaje de alerta (alert()) el evento recibido. Como se sabe que en el tópico indicado se publicarán sólo puntos, extraiga el contenido enviado con el evento (objeto JavaScript en versión de texto), conviértalo en objeto JSON, y extraiga de éste sus propiedades (coordenadas X y Y). Para extraer el contenido del evento use la propiedad 'body' del mismo, y para convertirlo en objeto, use JSON.parse. Por ejemplo:

var theObject=JSON.parse(message.body);
Compile y ejecute su aplicación. Abra la aplicación en varias pestañas diferentes (para evitar problemas con el caché del navegador, use el modo 'incógnito' en cada prueba).

Ingrese los datos, ejecute la acción del botón, y verifique que en todas la pestañas se haya lanzado la alerta con los datos ingresados.

Haga commit de lo realizado, para demarcar el avance de la parte 2.

git commit -m "PARTE 1".
```
  
