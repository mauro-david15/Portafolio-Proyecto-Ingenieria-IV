# Semana 1 · Introducción y SCAMPER

## Objetivo de la semana

Arrancar el curso: firmar el syllabus, crear la página personal en GitHub, practicar cómo escribir buenos prompts y usar el método **SCAMPER** para generar ideas, antes de elegir el área del proyecto final.

## Entregables

| Entregable | Estado |
|---|---|
| Syllabus firmado | ✅ Disponible en la [página de inicio](../index.md#syllabus) |
| Página personal en GitHub | ✅ Este sitio |
| Ejercicio de prompting | ✅ Abajo |
| Ejercicio SCAMPER | ✅ Abajo |
| Área del proyecto final (equipo) | ✅ Seguridad en el autotransporte de carga |

---

## Ejercicio de prompting: "El Desintoxicador digital analógico"

**Reto:** diseñar un dispositivo 100 % analógico (sin pantallas, cables ni baterías) que impida usar el celular durante la comida y convierta la desconexión en un juego de mesa. Teníamos 20 segundos para escribir el prompt.

Aplicamos la estructura vista en clase: **rol + contexto + tarea con verbo de acción + formato de salida**.

```text
Actúa como diseñador industrial de juegos de mesa. Diseña 5 dispositivos 100 %
analógicos (sin pantallas, cables ni baterías) que impidan usar el celular
durante una comida familiar y conviertan la desconexión en un juego.
Entrega una tabla con: nombre, mecanismo físico, regla del juego y material.
```

**Lo que aprendimos:**

- El **rol** cambió el tipo de respuesta: con "diseñador de juegos de mesa" las ideas incluyeron reglas y castigos, no solo cajas para guardar celulares.
- Pedir un **número exacto** (5) y un **formato** (tabla) hizo la respuesta comparable y fácil de evaluar.
- Funciona mejor **iterar por capas**: primero muchas ideas, luego pedir que desarrolle solo la mejor.

??? example "Ideas que salieron"

    | Nombre | Mecanismo | Regla del juego |
    |---|---|---|
    | La Torre | Base de madera con ranuras verticales para cada celular | Quien saque su celular antes del postre lava los platos |
    | Balanza familiar | Balanza de dos platos; los celulares van de un lado y un contrapeso del otro | Si alguien retira su celular, la balanza cae y suena una campana |
    | Caja de reloj de arena | Tapa que solo se abre al terminar de caer la arena (20 min) | Nadie puede abrirla antes; el primero en pedirla cuenta una historia |
    | Ruleta de preguntas | Plato giratorio sobre los celulares | Cada vuelta obliga a alguien a responder una pregunta en voz alta |
    | El Candado | Cofre con candado de combinación repartida entre todos | Se necesitan los números de todos para abrirlo |

---

## Ejercicio SCAMPER

En parejas aplicamos SCAMPER a un producto que ya existe y que después resultó clave para nuestro proyecto: el **rastreador GPS para tractocamiones**. Un rastreador típico envía la posición por red celular a un centro de monitoreo; si la señal se pierde, el centro queda ciego.

| Letra | Pregunta | Idea |
|---|---|---|
| **S** · Sustituir | ¿Qué parte se puede reemplazar? | Sustituir la decisión en la nube por **procesamiento dentro del camión** |
| **C** · Combinar | ¿Con qué se puede combinar? | Combinar GPS con los **datos del motor (CAN/J1939)** para saber si el camión se mueve aunque no haya señal |
| **A** · Adaptar | ¿Qué idea de otro sector sirve? | Adaptar la **caja negra de los aviones**: registrar todo lo que pasa aunque no se pueda transmitir |
| **M** · Modificar | ¿Qué se puede exagerar o cambiar? | Hacer el registro **inalterable** (firmado criptográficamente) para que sirva como evidencia |
| **P** · Poner en otro uso | ¿Quién más lo puede usar? | Que la **aseguradora** use el registro para ajustar primas y resolver siniestros |
| **E** · Eliminar | ¿Qué sobra? | Eliminar la dependencia de la **conexión permanente** para detectar el problema |
| **R** · Reordenar | ¿Qué pasa si se invierte el orden? | En vez de "transmitir y luego decidir", **decidir y guardar primero, y transmitir después** |

!!! success "Idea seleccionada"
    Un dispositivo que **sigue pensando cuando el camión pierde la señal**: detecta el bloqueo, guarda evidencia sellada y la envía en cuanto regresa la conexión. Esta idea combina S, C, A, M y R, y es el origen de lo que después fue Nervik.

---

## Elección del área de proyecto

**Equipo 2:** Andrik, Juan Pablo y Mauro.

De las propuestas del profesor nos llamaron la atención las tecnologías del IDIT (antenas LoRa, RTK, geofencing) y la detección temprana de riesgos. Elegimos llevarlas a un problema que vemos todos los días en Puebla: el **robo al autotransporte de carga**.

**Por qué esta área:**

- Puebla y el Estado de México concentran gran parte de los robos al transporte de carga del país.
- Las bandas usan **inhibidores de señal (jammers)** para dejar ciegos a los rastreadores.
- Combina lo que sabemos hacer como mecatrónicos: electrónica embebida, comunicación, IA y diseño de carcasas.

## Conclusión

La semana nos dejó dos herramientas que usamos en todo el proyecto: escribir prompts con rol, contexto, tarea y formato, y usar SCAMPER para no quedarnos con la primera idea. El ejercicio con el rastreador GPS nos dio la pregunta que guió las siguientes semanas: **¿qué pasa con la seguridad del camión cuando se pierde la señal?**
