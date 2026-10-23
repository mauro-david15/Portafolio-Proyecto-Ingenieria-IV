# Semana 4 · Mercado, valor y propuesta de valor

## Objetivo de la semana

Definir quién compraría Nervik, cuánto mercado existe y por qué tendría valor frente a las alternativas actuales.

---

## 1. Segmento accionable

**Perfil en una oración:** gerentes de seguridad de transportistas medianas (20 a 200 tractocamiones) que cruzan el corredor México–Puebla–Veracruz o el Bajío y ya pagan por rastreo, pero quedan ciegos cuando un jammer bloquea la señal.

| Capa | Dato | Estado |
|---|---|---|
| **Demográfica** | Transportistas con 20 a 200 unidades; en México hay 219,464 permisionarios de carga y las flotas medianas (31–100 unidades) suman 259,418 vehículos | ✅ VERIFICADO (SICT/DGAF, junio 2025) |
| | Operan en el centro del país; Estado de México y Puebla concentran la mayor parte de los robos | ✅ VERIFICADO (SESNSP 2025) |
| **Conductual** | Ya pagan GPS, monitoreo 24/7 y, en rutas críticas, custodia | ✅ VERIFICADO (benchmarking, [semana 7](semana7.md#1-benchmarking-de-modelos-de-ingresos)) |
| | Han sufrido al menos un robo o intento con jammer en el último año | ⚠️ HIPÓTESIS (AMESIS reporta jammer en 71–81 % de los robos, pero falta confirmarlo por flota) |
| **Psicográfica** | Desconfían de soluciones con precio opaco y contratos largos | ⚠️ HIPÓTESIS |
| | Valoran más tener evidencia para el seguro que una alerta que llega tarde | ⚠️ HIPÓTESIS |
| **Económica** | Gastan entre USD 20 y 60 por unidad al mes en telemática | ✅ VERIFICADO (rangos de mercado de Geotab y Motive) |
| | Pagarían $300 MXN/mes extra por unidad por una capa anti-jammer | ⚠️ HIPÓTESIS |

**Hipótesis críticas sin verificar:**

1. Cuántos eventos de jammer tiene realmente **cada flota** al año (no el mercado agregado).
2. Si la aseguradora reconocería el expediente de Nervik como evidencia.
3. Si el gerente de seguridad tiene presupuesto propio o depende del director general.

**Usuario, comprador y decisor:**

| Rol | Quién |
|---|---|
| Usuario | Operador del centro de monitoreo |
| Comprador | Gerente de seguridad o de operaciones |
| Decisor | Director general o dueño de la flota (y la aseguradora como influenciador) |

---

## 2. Tamaño de mercado (TAM, SAM y SOM)

**Supuesto de precio:** $1,800 MXN por unidad instalada + **$300 MXN al mes** de servicio ($3,600 al año), tomado de la [PDS](semana5.md#3-especificacion-de-diseno-de-producto-pds) (C-03).

| | Cálculo | Valor anual |
|---|---|---:|
| **TAM** | 1,477,953 unidades de carga (SICT/DGAF, jun. 2025) × ~50 % que son unidades motrices* = **~739,000 unidades** × $3,600 | **≈ $2,660 M MXN** |
| **SAM** | Flotas medianas: 259,418 vehículos × ~50 % motrices* = ~129,700 × ~50 % en corredores de alto riesgo* = **~64,850 unidades** × $3,600 | **≈ $233 M MXN** |
| **SOM (años 1–2)** | 15 flotas × 40 unidades = **600 unidades** (≈ 0.9 % del SAM) × $3,600 | **≈ $2.2 M MXN** recurrentes + $1.1 M de hardware |

\* Supuestos a verificar en la Estadística Básica del Autotransporte Federal: el parque incluye remolques, y no todos los camiones de flotas medianas circulan por corredores de alto riesgo.

**Referencia de disposición a pagar:** el mercado de telemática comercial en México se estima en **USD 1,062.6 millones en 2025** (IMARC Group). Las flotas ya pagan por rastreo; Nervik compite por una parte de ese gasto.

**Lógica de go-to-market del SOM:**

- **Canal:** venta directa a gerentes de seguridad y alianza con 1–2 brokers de seguros de carga.
- **Piloto:** flotas de Puebla que cruzan el corredor México–Puebla–Veracruz.
- **Capacidad:** un equipo de 3–4 personas puede instalar y dar soporte a unas 30 unidades por mes.

!!! warning "Señal de viabilidad: Marginal"
    Con 600 unidades, la suscripción deja ≈ $1.7 M MXN al año después de costos variables, apenas lo que cuesta operar una startup de 4 personas (≈ $1.2 M en sueldos + $0.5 M de operación). El negocio necesita crecer más allá de 600 unidades o sumar a la aseguradora como pagador.

---

## 3. Mapa competitivo

| Tipo | Competidor | Qué hace | Precio | Debilidad para nuestro segmento |
|---|---|---|---|---|
| **Directo** | Rastreadores con detección de jammer (Ruptela, vía distribuidores como Syscom) | Detectan el jammer y activan un relevador o una alerta | No publicado | La reacción depende de la red o del paro de motor; no guardan evidencia sellada |
| **Directo** | Logitrack (México) | Soluciones anti-jammer para transporte de carga | No publicado | Enfocado en reaccionar, no en generar evidencia para el seguro |
| **Directo** | Integradores locales con paro de motor a distancia | GPS + bloqueo del motor al detectar robo | Cotización por unidad | El paro en movimiento es riesgoso y genera responsabilidad legal |
| **Indirecto** | Motive | Telemática y video con IA | ≈ USD 35/vehículo/mes | Precio opaco, contrato anual, sirve para eficiencia más que para el bloqueo |
| **Indirecto** | Geotab | Telemática basada en datos del vehículo | USD 20–60/vehículo/mes | Contrato de 3 años y configuración compleja |
| **Indirecto** | Samsara | Rastreo y gestión de flotas | Cotización por flota | Depende de conectividad; pierde valor durante el bloqueo |
| **Sustituto** | Custodia armada (Detecta Security) | Escolta física con monitoreo satelital | $8,000–$45,000 MXN por ruta | Muy caro por viaje y difícil de coordinar |
| **Sustituto** | Señuelos y rastreadores ocultos redundantes | Un segundo GPS escondido en la carga | Bajo | También se bloquea con el mismo jammer |

!!! danger "Competidor más peligroso"
    **Los rastreadores con detección de jammer de integradores locales.** Ya están instalados en muchas flotas y agregar la función es barato. Su debilidad: cuando el jammer bloquea la red, **no queda registro confiable de lo que pasó**.

---

## 4. Mapa de posicionamiento

Ejes elegidos por lo que más le importa al comprador: **costo mensual por unidad** y **autonomía durante el bloqueo** (qué tanto sigue detectando y registrando sin señal).

<figure markdown>
<svg viewBox="0 0 420 300" width="100%" style="max-width:520px" role="img" aria-label="Mapa de posicionamiento" font-family="Roboto, sans-serif" font-size="12">
  <line x1="50" y1="260" x2="400" y2="260" stroke="currentColor"/>
  <line x1="50" y1="260" x2="50" y2="20" stroke="currentColor"/>
  <text x="225" y="290" text-anchor="middle" fill="currentColor">Costo mensual por unidad →</text>
  <text x="18" y="140" text-anchor="middle" fill="currentColor" transform="rotate(-90 18 140)">Autonomía sin señal →</text>
  <circle cx="350" cy="60" r="7" fill="#9e9e9e"/><text x="350" y="45" text-anchor="middle" fill="currentColor">Custodia</text>
  <circle cx="270" cy="210" r="7" fill="#9e9e9e"/><text x="270" y="232" text-anchor="middle" fill="currentColor">Motive / Geotab / Samsara</text>
  <circle cx="140" cy="190" r="7" fill="#9e9e9e"/><text x="140" y="212" text-anchor="middle" fill="currentColor">GPS con anti-jammer</text>
  <circle cx="90" cy="235" r="7" fill="#9e9e9e"/><text x="95" y="252" text-anchor="start" fill="currentColor">Señuelos</text>
  <circle cx="150" cy="70" r="10" fill="#3f51b5"/><text x="150" y="50" text-anchor="middle" fill="currentColor" font-weight="bold">✕ Nervik</text>
</svg>
</figure>

**Por qué esta posición:** el cuadrante de **bajo costo y alta autonomía** está vacío. La única alternativa que sigue funcionando durante el bloqueo es la custodia, que cuesta miles de pesos por viaje.

---

## 5. Lienzo estratégico Blue Ocean

### Marco de las cuatro acciones

| Acción | Atributo | Justificación |
|---|---|---|
| **Eliminar** | Paro de motor | Riesgo de accidente y responsabilidad legal; las flotas desconfían |
| **Reducir** | Dependencia de la nube y contratos largos | Detección local y planes mensuales con piloto |
| **Incrementar** | Operación sin señal | Es justo cuando ocurre el robo |
| **Crear** | Expediente firmado para la aseguradora | Nadie entrega evidencia verificable de lo que pasó durante el bloqueo |

### Lienzo (1 = bajo, 5 = alto)

| Atributo | Custodia | Telemática (Motive/Geotab) | GPS anti-jammer | **Nervik** |
|---|:-:|:-:|:-:|:-:|
| Precio | 5 | 4 | 2 | **2** |
| Funciones de eficiencia (combustible, conductor) | 1 | 5 | 2 | **1** |
| Operación sin señal | 4 | 1 | 2 | **5** |
| Evidencia verificable del evento | 2 | 2 | 1 | **5** |
| Facilidad de instalación | 2 | 3 | 3 | **4** |
| Flexibilidad de contrato | 3 | 1 | 3 | **4** |
| Intervención física | 5 | 1 | 3 | **1** |

**Hueco azul:** la evidencia confiable de lo que pasa *mientras* el camión está ciego, a precio de suscripción y no de custodia.

!!! tip "Hipótesis que el lienzo asume"
    Que la **evidencia** vale lo suficiente para pagar. Si las flotas solo quieren que alguien detenga el robo, el atributo "intervención física" pesa más y Nervik pierde frente a la custodia. Se valida en las entrevistas.

---

## 6. Propuesta de valor

| Versión | Texto (≤ 25 palabras) |
|---|---|
| Funcional | Nervik sigue detectando y registrando aunque un jammer bloquee el GPS, sin depender de la nube ni de contratos largos. |
| Emocional | Que un jammer ya no te deje a ciegas: sabrás qué pasó con tu camión minuto a minuto, aunque se pierda la señal. |
| **Versión 3** | **Gerentes de seguridad de flotas medianas: cuando un jammer apaga su GPS, Nervik sigue registrando y les entrega evidencia sellada para reclamar al seguro.** |

| Evaluación IDEO | |
|---|---|
| Insightful | ✅ El problema no es saber que hubo robo, es no saber qué pasó durante el bloqueo |
| Unique | ⚠️ La combinación es nueva, pero hay que proteger el método de sellado ([semana 3](semana3.md#conclusion-de-libertad-de-operacion-fto)) |
| Targeted | ✅ Gerentes de seguridad de flotas medianas en corredores críticos |

**Pirámide de Bain:** nivel **funcional** (reduce riesgo y costo) con oportunidad de subir a **emocional** (tranquilidad) cuando el expediente se use en siniestros reales.

**Oferta vs. propuesta:** la *oferta* es un dispositivo J1939 con TinyML y bitácora firmada; la *propuesta* es no quedarse sin pruebas cuando roban un camión.

**Error de la primera versión:** vendíamos funciones (paro de motor, IA, detección "perfecta") en lugar del resultado para el usuario.

---

## 7. Canvas de mercado (resumen)

| Sección | Contenido |
|---|---|
| Segmento | Transportistas con 20–200 unidades en corredores críticos; usuario: centro de monitoreo; comprador: gerente de seguridad |
| Tamaño | TAM ≈ $2,660 M · SAM ≈ $233 M · SOM ≈ $2.2 M MXN al año (600 unidades) |
| Competencia | 3 directos, 3 indirectos y 2 sustitutos; el más peligroso: GPS con anti-jammer de integradores |
| Hueco azul | Evidencia verificable durante el bloqueo, a precio de suscripción |
| Propuesta | Versión 3 de arriba |

??? info "Fuentes"
    - SICT/DGAF, *El autotransporte federal en cifras*, junio 2025, citado por [The Logistics World](https://thelogisticsworld.com/logistica-y-distribucion/el-crecimiento-del-autotransporte-carga-mexico/).
    - SESNSP 2025, citado por [Forbes México](https://forbes.com.mx/?p=1374865) y [The Logistics World](https://thelogisticsworld.com/actualidad-logistica/alerta-en-las-carreteras-panorama-2025-de-robos-al-transporte-de-carga-en-mexico/).
    - IMARC Group, [Mercado de telemática comercial en México](https://www.imarcgroup.com/report/es/mexico-commercial-telematics-market), 2025.
    - Detección de jammer con Ruptela: [Syscom](https://syscom.mx/blog/proteja-sus-gps-vehiculares-de-los-bloqueadores-de-celulares).
    - Anti-jammer para carga: [Logitrack](https://www.logitrack.mx/en/blog/los-dos-tipos-de-anti-jammer-que-necesitas-para-prevenir-robos-al-transporte-de-carga).
