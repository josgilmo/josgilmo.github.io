---
layout: post
title: Inyección de dependencias en Go.
---

Comenzar a aprender y trabajar con un lenguaje nuevo suele ser emocionante y divertido al comienzo, hasta que comenzamos a echar de menos procesos o herramientas a los que estabamos acostumbrados. Mis orígenes son PHP, y llevo en mi mochila (mi cabeza) ideas como el inyector de dependencias de Symfony. Hace más de año y medio, cuando comencé con Go no había ningún DI maduro por lo que la gente estaba acostumbrada a trabajar inyectando directamente las dependencias, y yo quería volver a usar 
este tipo de herramientas, y ahí es cuando comenzó viaje una vida con un DI mejor.

Lo primero que me encontré es que los Go developers hemos olvidado lo que es la inyección de dependencia y la confundimos con 
la composición. Creemos que el pasar las dependencias en el costructor es inyección de dependencias, pero la realidad es que eso es composición. Extraigo de la wikipedia la definición de D.I.

```
In software engineering, dependency injection is a technique whereby one object supplies the dependencies of another object. A "dependency" is an object that can be used, for example as a service. Instead of a client specifying which service it will use, something tells the client what service to use. The "injection" refers to the passing of a dependency (a service) into the object (a client) that would use it. The service is made part of the client's state.[1] Passing the service to the client, rather than allowing a client to build or find the service, is the fundamental requirement of the pattern.
```

Matizado este punto, podemos preguntarnos ¿cómo y para qué hacemos DI en Go? 

La solución que he adoptado en el equipo que estoy trabajando es google/wire. No es más que un generador de código que resuelve el grafo de dependencias y crea funciones que cumplen contratos para gestionar las dependencias. Los ejemplos de 
la librería son lo suficientemente explicativos como para echarles un ojo y prestarle algo de atención. 

Aunque pueda ser un poco repetitivo, voy a poner un ejemplo de cómo lo estamos haciendo nosotros, y qué mejoras hemos encontrado con el tiempo.



Mejoras:
 * Ahorro de tiempo al actualizar las dependencias.
 * Reutilización de inicalización de inyecciónes en base a la configuración.
 * Simplicidad en el bootstrapping de nuestra aplicación.
