# Proyecto final: Nervik

!!! abstract "Concepto"
    **Nervik** es un dispositivo Edge-AI de bajo perfil (80 × 50 × 30 mm) que se conecta al puerto de diagnóstico **OBD-II / J1939** del tractocamión. Ejecuta IA local (TinyML) para **detectar jammers de GPS/GSM**, da **alertas en cabina** (buzzer y LEDs) y hace un **sellado criptográfico de la evidencia** en memoria local, sin depender de la nube.

| | |
|---|---|
| **Equipo** | Equipo 2: Andrik, Juan Pablo y Mauro |
| **Problema** | Robo de carga con inhibidores de señal: durante el bloqueo, el GPS y la telemetría quedan ciegos |
| **Usuario** | Encargados de flota y choferes de tractocamiones |
| **Comprador** | Dueño de la flota; la aseguradora como posible co-comprador ([ver semana 7](semanas/semana7.md#oportunidad-el-stakeholder-que-no-esta-pagando)) |
| **Modelo de ingresos** | Hardware + suscripción |

## Evolución del proyecto

| Semana | Paso |
|---|---|
| [2](semanas/semana2.md) | Idea inicial **Kallpa Route AI**; validación de deseabilidad (4 de 5 señales) |
| [3](semanas/semana3.md) | Cambio de nombre a **Nervik**; vigilancia tecnológica |
| [4](semanas/semana4.md) | Segmento: flotas medianas en corredores de alto riesgo |
| [5](semanas/semana5.md) | PDS, arquitectura de 7 módulos y salida del bloqueo de motor del alcance |
| [6](semanas/semana6.md) | Carcasa Variante B (cuña biselada) |
| [7](semanas/semana7.md) | Benchmarking de ingresos, BOM y costos del MVP |

## Flujo básico del MVP

1. Recibe telemetría y señales relevantes.
2. El microcontrolador procesa los datos localmente.
3. Detecta una condición anómala definida previamente.
4. Si se pierde la conectividad, sigue trabajando en modo local.
5. Registra el evento y muestra un estado físico.
6. Cuando regresa la conexión, sincroniza la información.
7. La app permite consultar alertas e historial.

!!! warning "Lo que todavía no prometemos"
    - Bloqueo automático del motor.
    - Detección perfecta de cualquier jammer.
    - Predicción de robos con alta precisión sin un dataset suficiente.
    - Recálculo autónomo de rutas.

## Componentes principales

| Función | Componente |
|---|---|
| Microcontrolador con TinyML | ESP32-S3-WROOM-1 (Wi-Fi/BLE, doble núcleo) |
| Lectura del camión | Transceptor CAN Bus |
| Detección de jammer | Detector de potencia RF / GNSS |
| Comunicación de respaldo | LoRa (SX1276 / RFM95W) |
| Evidencia local | Flash NOR SPI W25Q128JV (128 Mb) |
| Energía | Buck automotriz 12/24 V con TVS de protección |
| Interfaz | Buzzer piezoeléctrico y LEDs verde/rojo |
| Carcasa | 2 piezas impresas en 3D (PETG/ABS negro mate) |

---

## Plan de prototipado

!!! question "Supuesto a validar"
    El microcontrolador local puede detectar la saturación de señal de un jammer y guardar una bitácora cifrada e inalterable en su memoria en tiempo real, **sin depender de la nube** y **sin falsos positivos** con la telemetría del camión.

**Pregunta precisa:** ¿puede un encargado de flota o chofer conectar el dispositivo al puerto OBD-II y verificar que la protección está activa en **menos de 90 segundos**, sin herramientas ni capacitación?

| Aspecto | Decisión |
|---|---|
| Tipo de prototipo | Función y experiencia |
| Resolución | Baja–media: primero validar firmware, memoria y usabilidad; la carcasa final viene después |
| Tiempo de construcción | 2 a 3 semanas |

### Qué vamos a construir

- **Hardware:** prototipo en protoboard o PCB perforada con ESP32-S3 (o Raspberry Pi Pico), transceptor CAN (MCP2515/TJA1050), sensor de RF, memoria EEPROM externa, buzzer y 2 LEDs.
- **Carcasa:** impresa en 3D (PETG/PLA) con el conector OBD-II integrado.
- **Simulación:** emulador de datos CAN en laptop para simular el camión y un botón o generador de ruido RF para simular el ataque.

### Cómo capturamos evidencia

| Prueba | Método | Métrica |
|---|---|---|
| Funcional (laboratorio) | Cronometrar desde que inicia la interferencia hasta que la memoria confirma la escritura cifrada | Tiempo de respuesta (s) e integridad de la bitácora |
| Usabilidad (instalación) | Observar a 3–5 personas simulando ser choferes mientras conectan el dispositivo | Tiempo de conexión e interpretación de los LEDs |

!!! success "Umbral de éxito"
    - **4 de 5** usuarios instalan el dispositivo y confirman la protección (LED verde fijo) en **menos de 90 s**.
    - El sistema detecta la interferencia y sella la bitácora en **menos de 2 s**.
    - **Cero falsos positivos** durante 30 minutos de prueba continua.

---

## Revisión DFM

Aplicamos diseño para manufactura y ensamble (proceso de Ulrich & Eppinger) al concepto de la semana 6 y al BOM de la semana 5, para un lote piloto de **10 unidades** con PCBA en JLCPCB e impresión 3D en laboratorio.

### Costo unitario

| Rubro | Actual (MXN) | Con mejoras DFM (MXN) |
|---|---:|---:|
| BOM electrónico | $813 | $493 |
| PCB + PCBA | $260 | $147 |
| Carcasa | $90 | $78 |
| Ensamble manual | $100 (50 min) | $36 (18 min) |
| Gastos indirectos (15 %) | $189 | $113 |
| **Total por unidad** | **$1,452** | **$867** |

!!! info "Ahorro: $585 MXN por unidad (−40 %)"
    Casi todo el ahorro depende de dos decisiones de alcance: quitar el **AD8317** y no poblar **LoRa**. Si se conservan y solo se aplica lo demás, el costo queda en ≈ $1,375 MXN (−5 %).

Supuestos: tipo de cambio de $17.20 MXN/USD, 33.5 % de impuesto a paquetería desde China y mano de obra a $120 MXN/h.

### Oportunidades de reducción

| Componente | Problema | Alternativa | Ahorro (MXN/u) |
|---|---|---|---:|
| **AD8317** (detector RF) | Caro (≈ USD 11–12), encapsulado difícil de retrabajar, requiere ruteo RF de 50 Ω y se dispara con cualquier señal cercana | Módulo GNSS L1 (Quectel L76K o ATGM336H): el jamming se detecta en firmware por la caída simultánea de C/N0, cruzada con la velocidad del CAN. Además aporta hora y posición a la evidencia | ≈ $210 |
| **RFM95W** (LoRa) | Sin existencias en LCSC, soldadura manual, y sin gateways en el corredor no entrega nada en el piloto | Dejar la huella sin poblar; sincronizar la evidencia por BLE/Wi-Fi al llegar a patio. Poblar 2–3 unidades para pruebas de alcance | ≈ $220 |
| **ESP32-S3 + MCP2515 + TJA1050** | La variante N16R8 obliga a PCBA Standard (más cara); el ESP32-S3 ya trae controlador CAN (TWAI); el TJA1050 obliga a un riel de 5 V | Variante WROOM-1U o MINI-1, CAN por TWAI con SN65HVD230 (3.3 V) y todo a 3.3 V | ≈ $150 |

Correcciones al diseño, aunque no ahorren:

- **Regulador:** el MP1584EN (28 V máximo) no sirve para camiones de 24 V. Usar un buck de 60 V (LM2596HVS o LMR16020) con TVS SMBJ33A.
- **Memoria:** el W25Q128JVSIQ es parte Basic de JLCPCB y se queda.

### Ensamble

| | Piezas manipuladas | Tiempo por unidad |
|---|---:|---:|
| Diseño actual | 16 | ~50 min |
| Propuesta | 6 | ~18 min |

1. **Conector:** cambiar el OBD-II de 16 pines integrado por un conector de 4 pines con seguro (V+, GND, CAN-H, CAN-L) y un cable. Los tractocamiones Clase 8 usan el **Deutsch de 9 pines**, así que el diseño actual requeriría adaptador de todos modos.
2. **Cierre:** 2 ganchos de un lado y 2 tornillos autorroscantes del otro, sin insertos de latón.
3. **PCB:** apoyada en rieles y atrapada por la tapa, con una muesca asimétrica para que solo entre en una posición.
4. **LEDs y buzzer:** el PETG negro no deja pasar luz; agregar guías de luz translúcidas y un puerto de sonido.
5. **Impresión:** geometría sin soportes (chaflanes a 45°).
6. **Soldadura:** todo SMT montado por JLCPCB, sin soldadura manual.

### Soporte de producción y control de calidad

- Congelar una sola opción por renglón del BOM antes del layout.
- Agregar 6 pads de prueba (3V3, GND, TX, RX, EN, IO0) y un autotest en firmware: ID de la flash, loopback CAN, tramas NMEA, LEDs y buzzer.
- Probar la detección por **inyección conducida** con generador y atenuador, sin radiar con un jammer real.

### Trade-offs a evaluar

| Mejora | Lo que se pierde |
|---|---|
| AD8317 → GNSS | La detección de jamming GSM queda indirecta; afecta la promesa "detecta jammers GPS/GSM" |
| LoRa sin poblar | No hay alerta en tiempo real fuera del camión durante el bloqueo |
| Cable en lugar de conector integrado | Deja de ser un bloque único y suma ≈ $110 MXN, pero funciona con 9 pines y permite esconder el equipo |
| Autorroscantes sin insertos | Aguantan pocas aperturas; conservar insertos en las unidades de desarrollo |
| Cambio de ESP32 y CAN por TWAI | Re-layout y driver nuevo: 1 a 2 semanas |

**Compatibilidad con JLCPCB PCBA:** ⚠️ Hay que cambiar la variante del ESP32-S3, sacar el AD8317 y el RFM95W de la PCBA y eliminar los componentes THT.
