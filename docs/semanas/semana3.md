# Semana 3 · Propiedad intelectual, marca y vigilancia tecnológica

## Objetivo de la semana

Comprobar qué existe tecnológicamente, proteger la identidad del proyecto y empezar a validar directamente con usuarios.

| Entregable | Estado |
|---|---|
| Nombre de marca (3 prompts) | ✅ **Nervik** |
| Búsqueda fonética en el IMPI | ⏳ Falta la captura de pantalla |
| Vigilancia tecnológica (3–5 patentes + FTO) | ✅ 4 patentes · FTO 🟡 Media |
| 3 entrevistas reales | ⏳ Guía lista, entrevistas por realizar |

---

## 1. Nombre de marca

El proyecto empezó como **Kallpa Route AI**. El nombre era largo, describía una función (rutas) que ya no es el centro del producto y "Kallpa" es difícil de pronunciar para un comprador que no conoce el quechua.

### Prompt 1 (Claude) · Generación

Pedimos 12 nombres en cuatro estilos. Usamos **Claude** porque esta parte es creativa y no necesita datos externos.

| Estilo | Nombres |
|---|---|
| Evocadores | Centinela, Vigía, Faro |
| Compuestos | CargoSeal, TruckSentry, RutaFirme |
| Inventados | **Nervik**, Varkos, Telmo |
| Disruptivos | Ciego Nunca, Caja Negra, Sin Señal |

**Finalistas:** Nervik, CargoSeal y Centinela.

### Prompt 2 (Claude) · Evaluación

| Criterio | Nervik | CargoSeal | Centinela |
|---|:-:|:-:|:-:|
| Pronunciable en español e inglés | ✅ | ✅ | ⚠️ Solo español |
| Corto (≤ 3 sílabas) | ✅ | ✅ | ❌ |
| Sin significado negativo | ✅ | ✅ | ✅ |
| Registrable (no es palabra común) | ✅ | ⚠️ Descriptivo | ❌ Palabra común |
| Coherente con la emoción | ✅ "Nervio": el sistema nervioso del camión | ⚠️ Solo habla del sello | ✅ Vigilancia |

!!! success "Nombre elegido: Nervik"
    Viene de **nervio**: igual que el sistema nervioso, el dispositivo siente y reacciona aunque se corte la comunicación con "el cerebro" (la nube). Al ser una palabra inventada, es más fácil de registrar.

### Prompt 3 (Perplexity) · Verificación digital

Usamos **Perplexity** porque esta parte necesita buscar en internet y citar fuentes.

- No encontramos una marca de tecnología llamada "Nervik".
- Existe **Nervonik**, empresa de dispositivos médicos de estimulación nerviosa en EE. UU. Es otro sector y otra clase de Niza, pero es fonéticamente parecida y hay que revisarla en el IMPI.
- Existe **Nervik**, una concesionaria de autos familiar en Noruega, sin presencia en México.

## 2. Búsqueda fonética en el IMPI

**Clases de Niza a revisar:**

| Clase | Qué cubre |
|---|---|
| 9 | Aparatos electrónicos, dispositivos de rastreo y software |
| 42 | Software como servicio (la plataforma web) |
| 45 | Servicios de seguridad para bienes |

!!! warning "Pendiente"
    Hacer la búsqueda fonética de "Nervik" en el IMPI (MARCia) en las clases 9, 42 y 45, y subir la captura de pantalla. Si el IMPI no responde, usar TMview (tmdn.org) o la búsqueda de la USPTO.

---

## 3. Vigilancia tecnológica

### Términos de búsqueda

| Español | Inglés |
|---|---|
| detección de inhibidor de señal | jamming detection |
| rastreo de vehículos robados | stolen vehicle tracking |
| interferencia GNSS | GNSS interference |
| registro de eventos del vehículo | vehicle event data recorder |

**Combinación principal:** `(jamming OR jammer) AND (vehicle OR truck) AND (detect* OR monitor*)`

**Códigos de clasificación relevantes:**

| Código | Tema |
|---|---|
| H04K3/22 | Detección y monitoreo de interferencias intencionales (jamming) |
| G01S19/21 | Interferencia en sistemas de navegación por satélite |
| B60R25/10 | Sistemas antirrobo de vehículos que envían alertas |
| B60R25/2072 | Medidas contra el bloqueo de la señal del sistema antirrobo |
| G07C5/08 | Registro de datos de operación del vehículo |

**Secuencia de búsqueda:** IMPI (SIGA) → LATIPAT → Lens.org / Google Patents → Espacenet (familias y citas).

### Patentes analizadas

| Patente | Titular | Qué protege | ¿Nervik cae dentro? |
|---|---|---|---|
| [US8319615B2](https://patents.google.com/patent/US8319615) · Detección de jamming en comunicaciones | Continental Automotive (hoy Aumovio) · activa hasta ~2031 | Medir **qué tan rápido suben** la intensidad y la calidad de señal celular, y avisar a la estación base **antes de perder la sincronización** | 🟡 **Zona gris** si Nervik usara solo esa regla. Nervik decide con varias señales (C/N₀ de GNSS, CAN, IMU) y su valor está en el registro local |
| [US9102293B2](https://patents.google.com/patent/US9102293) · Reducir falsas alarmas en rastreo de vehículos robados | Continental Automotive (hoy Aumovio) · activa hasta ~2031 | Alarma solo si el vehículo se mueve sin solicitud de asistencia, o si falta la señal **en una zona con buena cobertura** | 🟡 **Zona gris**: la idea de usar "buena cobertura + sin señal" para inferir jamming se parece. Nervik usa movimiento del CAN/IMU y un modelo TinyML local |
| [US8175573B2](https://patents.google.com/patent/US8175573) · Mantener comunicación con el vehículo en presencia de jamming | Continental Automotive (hoy Aumovio) · activa hasta ~2030 | Al detectar jamming, cambiar a un **canal alterno acordado** (FM, CDMA) para seguir comunicándose | 🟢 **Fuera**: Nervik no cambia de canal; guarda y transmite después |
| [US11005589B2](https://patents.google.com/patent/US11005589) · Detección de jammers GNSS personales | Thales · activa hasta ~2038 | Sistema **a la orilla de la carretera** que analiza la señal GNSS que reenvía el vehículo y toma una foto si detecta un jammer | 🟢 **Fuera**: es infraestructura fija, no un dispositivo dentro del camión |

### Conclusión de libertad de operación (FTO)

!!! warning "FTO: 🟡 Media"
    - Ninguna patente encontrada protege la combinación de Nervik: **detección multiseñal local con TinyML + bitácora firmada inalterable como evidencia**.
    - Las patentes de Continental cubren reglas específicas de detección. Hay que **evitar** usar como único criterio "tasa de subida de RSSI/calidad + aviso antes de perder sincronización".
    - Las cuatro son patentes de **EE. UU.**; una patente solo protege en el país donde se otorga. **Falta confirmar en LATIPAT y el IMPI** si tienen familia en México.
    - **Lo que podemos proteger nosotros:** el método de sellado de evidencia y la máquina de estados N0–N3 podrían ser candidatos a **modelo de utilidad** o patente; la carcasa en cuña, a **diseño industrial**.

---

## 4. Entrevistas

### Hipótesis a probar (de la semana 2)

| | Hipótesis |
|---|---|
| **H1 · Dolor** | Las flotas medianas en corredores de alto riesgo han sufrido al menos un robo o intento con jammer en los últimos 12 meses |
| **H2 · Solución** | Un gerente de seguridad valora más tener **evidencia de lo que pasó durante el bloqueo** que solo recibir una alerta |
| **H3 · Pago** | La flota pagaría una suscripción mensual por unidad si la aseguradora reconoce la evidencia o mejora la prima |

### Perfiles a entrevistar

1. Gerente de seguridad o de operaciones de una transportista con 20 a 200 unidades.
2. Operador del centro de monitoreo de una flota o de una empresa de rastreo.
3. Ajustador o agente de seguros de carga.

### Guía de entrevista (20 minutos)

| Bloque | Tiempo | Preguntas |
|---|---|---|
| Apertura | 2 min | Presentación y permiso para tomar notas |
| Exploración | 12 min | "Cuénteme del último robo o intento que tuvieron." · "¿Qué pasó con el rastreo durante el evento?" · "¿Qué hicieron después con la aseguradora?" · "¿Cuánto gastan hoy en rastreo, custodia o señuelos?" |
| Hipótesis | 4 min | "Si hubiera tenido un registro de todo lo que pasó durante el bloqueo, ¿qué habría cambiado?" |
| Cierre | 2 min | "¿A quién más me recomienda entrevistar?" |

Reglas: escuchar el 80 % del tiempo y preguntar por **lo que ya pasó**, no por lo que harían.

!!! warning "Pendiente"
    Realizar las 3 entrevistas, guardar citas textuales y sintetizarlas con el prompt del profesor: cada hipótesis como confirmada, parcial o refutada, insight emergente, cita más importante e impacto en el concepto.
