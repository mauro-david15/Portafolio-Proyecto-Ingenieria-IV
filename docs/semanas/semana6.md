# Semana 6 · Generación y selección de concepto de diseño

## Objetivo de la semana

Definir cómo será físicamente Nervik antes de comenzar el CAD y la fabricación: generar al menos 3 conceptos, elegir uno con una matriz de Pugh y hacer el primer boceto técnico y el wireframe de la app.

**Restricción:** debe poder fabricarse con los medios de la universidad (impresión 3D FDM, PCB con JLCPCB y ensamble en laboratorio).

---

## 1. Tabla morfológica

| Parámetro | Variante 1 | Variante 2 | Variante 3 |
|---|---|---|---|
| **Forma de la carcasa** | Cuña biselada · *FDM sin soportes con chaflanes a 45°* | Cápsula redondeada anti-agarre · *requiere soportes o SLA* | Caja rectangular plana · *la más fácil de imprimir* |
| **Montaje** | Cinchos a la estructura bajo el tablero · *sin herramientas* | Soporte con clip a riel · *pieza extra impresa* | Cinta doble cara VHB · *barato pero se despega con calor* |
| **Indicador de estado** | 3 LEDs con guía de luz · *requiere ventana translúcida* | 1 LED RGB · *menos piezas, más ambiguo* | Sin indicador visible (solo app) · *más discreto, difícil de instalar* |
| **Material** | PETG negro mate · *resiste el calor de cabina* | ABS · *mejor acabado, se deforma al imprimir* | PLA · *barato, se ablanda arriba de 55 °C* |
| **Interfaz física** | 2 botones (reinicio y autoprueba) | 1 botón multifunción | Imán + interruptor reed · *sin agujeros en la carcasa* |
| **Conexión al vehículo** | Cable con conector Deutsch de 9 pines | Conector OBD-II integrado en la carcasa | Cable con adaptador universal |
| **Alimentación de respaldo** | Batería LiFePO₄ · *≥ 72 h* | Supercapacitor · *solo minutos* | Batería Li-ion · *más densa, más riesgo térmico* |

## 2. Analogías tecnológicas

| Parámetro | Producto | Sector | Lógica que trasplantamos |
|---|---|---|---|
| Registro inalterable | Caja negra de avión (FDR) | Aviación | Grabar todo localmente y recuperar después del evento |
| Forma y montaje | Protector de cableado bajo el tablero | Automotriz | Formas bajas y biseladas que no se enganchan con las piernas |
| Indicador | Detector de humo | Hogar | Un LED que parpadea poco indica "todo bien" sin abrir ninguna app |

---

## 3. Los 3 conceptos

=== "Concepto 1 · Escudo"

    **Combinación:** cuña biselada · cinchos · 3 LEDs · PETG · 2 botones · cable Deutsch · LiFePO₄.

    - **Instalación (4 pasos):** 1) conectar el cable Deutsch al puerto de diagnóstico, 2) fijar con dos cinchos bajo el tablero, 3) presionar autoprueba, 4) confirmar LED verde y dar de alta en la app.
    - **Uso cotidiano:** el chofer no interactúa; el centro de monitoreo solo ve alertas cuando hay sospecha.
    - **Analogía:** caja negra de avión.
    - **Manufactura:** FDM sin soportes; la cara inclinada protege la zona del conector.

=== "Concepto 2 · Cápsula"

    **Combinación:** cápsula redondeada · clip a riel · 1 LED RGB · ABS · 1 botón · OBD-II integrado · supercapacitor.

    - **Instalación (3 pasos):** 1) insertar en el puerto, 2) presionar el botón, 3) confirmar el color del LED.
    - **Uso cotidiano:** igual que el Escudo, pero el estado se lee por color.
    - **Analogía:** detector de humo.
    - **Manufactura:** requiere soportes o SLA; el ABS se deforma al imprimir.

=== "Concepto 3 · Bloque (datum)"

    **Combinación:** caja rectangular · cinta VHB · sin indicador · PLA · imán + reed · adaptador universal · Li-ion.

    - **Instalación (3 pasos):** 1) pegar con cinta, 2) conectar el adaptador, 3) activar con el imán y confirmar en la app.
    - **Uso cotidiano:** totalmente invisible; todo pasa en la app.
    - **Analogía:** etiqueta de rastreo de paquetes.
    - **Manufactura:** la más simple de imprimir, pero el PLA no soporta el calor de cabina.

### Pantalla de la app por concepto

| | Estado normal | Alerta | Acción principal | Omisión deliberada |
|---|---|---|---|---|
| Todos | Mapa con unidades en verde | Unidad en rojo con nivel N2/N3 | Abrir expediente del evento | No mostrar telemetría de eficiencia (no es nuestro producto) |

---

## 4. Matriz de Pugh

Datum: **Concepto 3 · Bloque**. Deseabilidad = 50 % del peso total.

| Tipo | Criterio | Peso | C1 · Escudo | C2 · Cápsula | C3 · Bloque |
|---|---|:-:|:-:|:-:|:-:|
| Deseabilidad | Facilidad de instalación sin instrucciones | 15 | **+** LEDs y cinchos guían el paso a paso | **+** se inserta y listo | S |
| Deseabilidad | Legibilidad del estado sin abrir la app | 12 | **+** 3 LEDs con significado fijo | **+** un LED RGB | S |
| Deseabilidad | Confianza que inspira el material y acabado | 10 | **+** PETG mate, robusto | **+** ABS liso | S |
| Deseabilidad | Tamaño y discreción en cabina | 8 | S | **+** más pequeño | S |
| Deseabilidad | Resistencia a manipulación | 5 | **+** cinchos y cable difícil de arrancar | **–** se saca del puerto de un jalón | S |
| Factibilidad | Costo de manufactura a 10 unidades | 15 | S | **–** SLA o soportes | S |
| Factibilidad | Complejidad del ensamble | 10 | **–** más piezas (LEDs, botones) | S | S |
| Factibilidad | Compatibilidad con el proceso (FDM + JLCPCB) | 10 | **+** sin soportes | **–** necesita SLA | S |
| Factibilidad | Resistencia al calor de cabina | 10 | **+** PETG | **+** ABS | S |
| Factibilidad | Compatibilidad con J1939 (Deutsch 9 pines) | 5 | **+** cable Deutsch | **–** OBD-II no entra en tractocamiones | S |
| | **Puntuación ponderada** | **100** | **+67 / –10 = +57** | **+55 / –35 = +20** | 0 |

!!! success "Concepto ganador: Escudo (cuña biselada)"
    - **Por qué:** es el único que funciona con el conector J1939 de los tractocamiones, se imprime sin soportes y deja leer el estado sin la app.
    - **Riesgo principal:** más piezas que ensamblar (LEDs, botones, guías de luz).
    - **Iteración recomendada:** aplicar las mejoras DFM del [proyecto final](../proyecto-final.md#revision-dfm) (snap-fits, PCB atrapada por la tapa) para bajar de 16 a 6 piezas.

---

## 5. Boceto técnico del Escudo

| Vista | Descripción |
|---|---|
| **Frontal** | 90 mm de largo × 25 mm de alto; cara superior inclinada 30° hacia el conector; 3 LEDs alineados en la parte alta |
| **Lateral** | Perfil en cuña: 25 mm del lado trasero, 12 mm del lado del cable |
| **Sección transversal** | Base con rieles para la PCB (80 × 50 mm); batería LiFePO₄ debajo de la PCB; tapa que atrapa la PCB; salida del cable con alivio de tensión |

| Parte | Material |
|---|---|
| Base y tapa | PETG negro mate (FDM) |
| Guías de luz | PETG translúcido a presión |
| Botones | TPU impreso sobre microswitch |
| Fijación | 2 ganchos snap-fit + 2 tornillos autorroscantes |

**Componentes principales:** conector del cable al frente-abajo, MCU y memoria al centro, módulo GNSS con antena hacia la cara superior (para ver el cielo a través del parabrisas), batería atrás.

!!! warning "Pendiente"
    Subir la foto del boceto en papel o el dibujo digital con cotas.

---

## 6. Wireframe de la app

```text
┌───────── Pantalla principal ─────────┐   ┌──────────── Alerta ────────────┐
│ Nervik · Flota Transportes Puebla    │   │ ⚠ Unidad 07 · Nivel N3         │
│ ┌──────────────────────────────────┐ │   │ Evento confirmado · 03:12      │
│ │          [ mapa ]                │ │   │ Pérdida de GNSS y celular      │
│ │   ● 12  ● 05  ● 07  ● 19         │ │   │ Última posición: km 142        │
│ └──────────────────────────────────┘ │   │ México–Puebla                  │
│ 24 unidades · 24 protegidas  ●       │   │                                │
│ Sin alertas en las últimas 24 h      │   │ [ Ver expediente firmado ]     │
│ [ Unidades ]  [ Eventos ]  [ Ajustes]│   │ [ Llamar al operador ]         │
└──────────────────────────────────────┘   └────────────────────────────────┘

┌─ Instalación 1/3 ─┐  ┌─ Instalación 2/3 ─┐  ┌─ Instalación 3/3 ─┐
│ Escanea el QR del │  │ Conecta el cable  │  │ Presiona prueba.  │
│ dispositivo       │  │ y fija con cinchos│  │ ¿LED verde fijo?  │
│   [ ▢ cámara ]    │  │   [ Siguiente ]   │  │ [ Sí, terminar ]  │
└───────────────────┘  └───────────────────┘  └───────────────────┘
```

## Conclusión

El Escudo ganó porque resuelve lo que más importa en campo: se instala sin herramientas, se lee sin abrir la app y se conecta al puerto real de un tractocamión. El siguiente paso es el CAD, aplicando las mejoras DFM para reducir piezas y tiempo de ensamble.
