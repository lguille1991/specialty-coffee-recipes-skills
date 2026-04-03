# ☕ AI Skill – Coffee Range System (Specialty Coffee Recipe Generator)

## 🎯 Objetivo

Generar recetas de café de especialidad utilizando un **sistema de rangos dinámico** en lugar de valores fijos.

El agente debe:
- Recomendar el **método de preparación que mejor resalte las bondades del grano**.
- Evitar acidez agresiva y amargor pesado, buscar balance.
- Adaptar cada receta al equipo del usuario.
- Usar lógica de **rangos + offsets + ajustes finos**.
- Considerar siempre **método, proceso, tueste, frescura y variedad**.

---

## 🧠 Principio clave

> No usar valores absolutos. Siempre trabajar con rangos controlados.

La receta debe construirse así:

1. Método → define rango base
2. Proceso → desplaza el rango
3. Tueste → ajusta agresividad de extracción
4. Frescura → ajusta comportamiento del flujo y desgasificación
5. Variedad → ajuste fino
6. Taza → navegación dentro del rango

---

## ⚙️ Equipamiento del usuario

### Métodos disponibles:
- Hario V60 (02 y Mugen)
- Hario Switch 03
- Chemex
- Kalita Wave
- Origami Air M
- AeroPress (Original + XL)
- NextLevel Pulsar
- Orea V4
- Ceado Hoop

### Molinos:
- 1ZPresso K-Ultra (principal referencia)
- 1ZPresso Q-Air
- Baratza Encore ESP

---

## 🔶 BLOQUE 1 – RANGOS BASE POR MÉTODO

### K-Ultra (referencia principal)

| Método | Rango base (clicks) | Temperatura base |
|--------|---------------------|------------------|
| V60 / Origami | 78 – 84 | 92–94°C |
| Orea V4 | 76 – 83 | 92–94°C |
| Hario Switch | 80 – 86 | 91–94°C |
| Kalita Wave | 80 – 86 | 91–93°C |
| Chemex | 82 – 88 | 92–94°C |
| Ceado Hoop | 80 – 87 | 91–94°C |
| Pulsar | 78 – 85 | 91–94°C |
| AeroPress | 70 – 80 | 88–92°C |

> Nota sobre temperatura: todos los valores se refieren a **temperatura del kettle**. Con kettle de cuello de ganso y vertido lento, esperar una pérdida de ~2–3°C en el slurry.

Regla:
- El agente debe tomar este rango como **zona neutra inicial**.
- Nunca debe partir de un valor aislado si aún no evaluó los demás factores.

---

## 🔶 BLOQUE 1B – RANGOS DE RATIO POR MÉTODO

El ratio es una variable crítica de extracción. El agente debe elegir dentro de estos rangos según intensidad deseada.

| Método | Rango de ratio | Nota |
|--------|---------------|------|
| V60 / Origami / Orea V4 | 1:15 – 1:17 | Zona más común: 1:16 |
| Hario Switch | 1:13 – 1:16 | Inmersión tolera más concentración |
| Kalita Wave | 1:15 – 1:17 | Similar a V60 |
| Chemex | 1:15 – 1:17 | Filtro grueso compensa ratio estándar |
| Ceado Hoop | 1:14 – 1:16 | Flujo controlado admite más café |
| Pulsar | 1:14 – 1:16 | |
| AeroPress | 1:11 – 1:16 | El más flexible; inmersión corta puede ir 1:11–1:13 |

Ajuste de ratio por perfil:
- Café complejo (natural/anaeróbico): puede ir hacia el lado más diluido del rango para evitar saturación
- Café delicado o floral: mantener zona media-alta (más agua) para claridad en taza
- Café muy viejo o plano: bajar el ratio (más café) como primera corrección antes de cambiar molido

---

## 🔶 BLOQUE 2 – OFFSETS POR PROCESO (AJUSTE PRINCIPAL)

### Molido (K-Ultra)

| Proceso | Ajuste |
|--------|--------|
| Lavado | -2 a -4 clicks |
| Honey / Natural | +2 a +5 clicks |
| Anaeróbico / experimental | +4 a +7 clicks |

### Temperatura

| Proceso | Ajuste |
|--------|--------|
| Lavado | +1 a +2°C |
| Honey / Natural | -1 a -3°C |
| Anaeróbico / experimental | -2 a -4°C |

Lectura práctica:
- **Lavado**: suele permitir mayor temperatura y molido más fino.
- **Honey / Natural**: suele requerir molido más grueso y temperatura más controlada para evitar pesadez.
- **Anaeróbico / experimental**: requiere más control aún; priorizar limpieza, balance y contención de fermentación.

---

## 🔶 BLOQUE 3 – OFFSETS POR NIVEL DE TUESTE

El tueste modifica la **solubilidad** y la facilidad de extracción.

### Molido (K-Ultra)

| Tueste | Ajuste |
|--------|--------|
| Claro | -2 a -5 clicks |
| Medio | neutro |
| Medio-oscuro / oscuro | +3 a +6 clicks |

### Temperatura

| Tueste | Ajuste |
|--------|--------|
| Claro | +2 a +4°C |
| Medio | neutro |
| Medio-oscuro / oscuro | -2 a -5°C |

Lectura práctica:
- **Tueste claro**: requiere más energía de extracción.
- **Tueste medio**: punto neutro del sistema.
- **Tueste oscuro**: se sobreextrae con facilidad; bajar energía.

---

## 🔶 BLOQUE 4 – OFFSETS POR FRESCURA

La frescura afecta principalmente el **CO₂**, el bloom y la estabilidad del flujo.

### Ventanas de referencia

| Frescura | Lectura |
|---------|---------|
| 1–7 días | muy fresco |
| 8–21 días | ventana óptima |
| 22–45 días | café más viejo |
| 46+ días | café pasado de ventana |

### Molido (K-Ultra)

| Frescura | Ajuste |
|---------|--------|
| Muy fresco | +1 a +2 clicks |
| Óptimo | neutro |
| Más viejo (22–45 días) | -1 a -3 clicks |
| Pasado (46+ días) | -2 a -4 clicks |

### Temperatura

| Frescura | Ajuste |
|---------|--------|
| Muy fresco | neutro o -1°C si el café se muestra agresivo |
| Óptimo | neutro |
| Más viejo (22–45 días) | +1 a +2°C |
| Pasado (46+ días) | +2 a +3°C |

### Ajustes de técnica

**Muy fresco (1–7 días):**
- Bloom más largo: 45–60 s
- Puede requerir un bloom algo más generoso
- Agitación moderada y controlada
- Evitar moler demasiado fino al inicio

**Óptimo (8–21 días):**
- Usar el sistema normalmente

**Más viejo (22–45 días):**
- Más fino
- Más temperatura
- Más agitación si la taza sale plana

**Pasado (46+ días):**
- Ajustes agresivos: molido fino + temperatura alta + agitación
- Ratio más concentrado (bajar a zona baja del rango) para recuperar intensidad
- Advertir que el café puede haber perdido complejidad de forma irreversible

---

## 🔶 BLOQUE 5 – AJUSTE FINO POR DENSIDAD (VARIEDAD + ALTITUD)

La densidad del grano es una función combinada de **variedad + altitud de cultivo**. Es un micro ajuste, no el factor dominante.

### Por variedad

| Tipo | Ajuste |
|------|--------|
| Alta densidad (Gesha, SL28 y similares) | -1 a -2 clicks / +1°C |
| Media (Bourbon, Caturra y similares) | neutro |
| Baja densidad | +1 a +2 clicks |
| Pacamara | puede ir fino, pero controlar flujo |

### Por altitud de cultivo

| Altitud | Ajuste |
|---------|--------|
| Alta (>1800 msnm) | -1 a -2 clicks / +1°C |
| Media (1200–1800 msnm) | neutro |
| Baja (<1200 msnm) | +1 a +2 clicks |

Cuando variedad y altitud señalen en la misma dirección, aplicar el ajuste una sola vez en la zona media de ambos offsets — no sumarlos mecánicamente.

Regla:
- Densidad nunca debe sobreescribir la lógica de proceso, tueste o frescura.
- Solo debe afinar el rango final.

---

## 🔶 BLOQUE 5B – REGLA DE ACUMULACIÓN MÁXIMA DE OFFSETS

Cuando se apilan todos los offsets, el rango operativo final no debe exceder **10 clicks de amplitud**.

Si el rango acumulado es mayor:
1. Comprimir hacia el centro del rango
2. Priorizar proceso y tueste como factores dominantes
3. Frescura y densidad actúan como micro-ajustes de ±1–2 clicks sobre ese centro

Ejemplo de compresión:
- Rango acumulado teórico: 76–91 (15 clicks) → comprimir a zona 81–87 (6 clicks), centrando en proceso natural + tueste claro

Esta regla garantiza que la receta sea operativamente útil, no una suma mecánica de offsets.

---

## 🔶 BLOQUE 6 – ORDEN OBLIGATORIO DE DECISIÓN

El agente debe construir la receta en este orden exacto:

1. Identificar método recomendado
2. Tomar rango base del método
3. Aplicar offset por proceso
4. Aplicar offset por tueste
5. Aplicar offset por frescura
6. Aplicar ajuste fino por variedad
7. Definir rango operativo final
8. Elegir punto medio como referencia inicial
9. Redactar la receta
10. Preparar ajustes rápidos sin romper el sistema

---

## 🔶 BLOQUE 7 – CONSTRUCCIÓN DEL RANGO FINAL

El agente debe:

1. Tomar rango base del método
2. Moverlo según proceso
3. Ajustarlo según tueste
4. Corregirlo según frescura
5. Afinarlo según variedad

Resultado:
- Definir **rango operativo final**
- Usar el **punto medio** como referencia inicial
- Si el rango final queda demasiado amplio, priorizar el centro útil y describirlo de forma práctica

Ejemplo lógico:
- Método: V60 → 78–84
- Proceso natural → +2 a +5
- Tueste claro → -2 a -5
- Frescura óptima → neutro
- Variedad Gesha → -1 a -2

El agente debe sintetizar esto en una recomendación operativa coherente, no en una suma mecánica absurda.

---

## 🔶 BLOQUE 8 – GENERACIÓN DE RECETA

Formato obligatorio:

### Receta recomendada – [Método]

**Objetivo:** [perfil en taza]

---

### Parámetros
- Café: XX g  
- Agua: XXX g  
- Ratio: 1:XX  
- Temperatura: XX °C  
- Filtro: [tipo]  
- Tiempo total: X:XX – X:XX  

---

### Molido

**Para tus molinos:**

**1ZPresso K-Ultra (preferido)**  
[Rango final calculado]

**Punto inicial recomendado:**  
[valor medio o zona media del rango]

**1ZPresso Q-Air**  
[Conversión equivalente]

**Baratza Encore ESP**  
[Conversión equivalente — rango 14–24 para pour over]

Descripción:
[relación con método y comportamiento esperado]

---

### Técnica de vertido

El estilo de vertido debe indicarse en la receta. Guía por método y proceso:

| Método | Estilo recomendado |
|--------|-------------------|
| V60 / Origami / Orea V4 | Pulse pour (3–4 pours) |
| Chemex | Pulse pour suave (2–3 pours, hilo más grueso) |
| Kalita Wave | Continuous pour circular o 3 pours controlados |
| Hario Switch | Single pour en inmersión, drenaje al final |
| Pulsar | Según protocolo de poros del dispositivo |
| AeroPress | Single pour + agitación según protocolo |
| Ceado Hoop | Pulse pour moderado |

Ajuste por proceso:
- **Lavado**: agitación moderada, pulse pour estándar
- **Honey / Natural**: pours suaves y controlados, minimizar turbulencia
- **Anaeróbico**: pours lentos, mínima agitación, priorizar limpieza en taza

---

### Pasos

Incluir siempre:
- Tiempo
- Agua vertida
- Agua acumulada

Las recetas deben ser:
- Claras
- Reproducibles
- Directas
- Sin teoría innecesaria

---

## 🔶 BLOQUE 9 – NAVEGACIÓN DENTRO DEL RANGO (FEEDBACK)

El agente debe ajustar **sin salir del sistema**.

### Muy ácido
- Ir hacia el lado fino del rango
- Subir temperatura
- Extender ligeramente el contacto

### Muy amargo
- Ir hacia el lado grueso
- Bajar temperatura
- Reducir agitación

### Drenaje lento
- Moverse hacia el extremo grueso
- Reducir pours agresivos o agitación

### Drenaje rápido
- Moverse hacia el extremo fino
- Mejorar bloom o distribución de agua

### Plano o sin vida
- Más fino si está subextraído
- Más temperatura si el café está viejo o muy denso
- Más agitación controlada
- Ajustar ratio si hace falta más intensidad

---

## 🔶 BLOQUE 10 – AJUSTES ESPECIALES POR INTERACCIÓN

El agente debe reconocer combinaciones conflictivas:

### Natural + tueste claro
- No ir automáticamente muy grueso ni muy fino
- Buscar zona media del rango
- Priorizar balance entre dulzor y limpieza

### Lavado + tueste oscuro
- Bajar temperatura
- Ir más grueso
- Evitar sobreextracción

### Café muy fresco + molido fino
- Riesgo de flujo inestable y falsa subextracción
- Primero corregir frescura y bloom antes de cerrar más el molido

### Anaeróbico + tueste claro
- Mucho potencial, pero fácil saturar la taza
- Mantener temperatura controlada y flujo limpio

---

## 🚫 REGLAS

- No usar valores únicos fijos como punto de partida ciego
- No ignorar el sistema de rangos
- No cambiar múltiples variables a la vez en los ajustes rápidos
- No dar múltiples recetas
- No explicar teoría extensa salvo que el usuario la pida
- No dejar fuera tueste o frescura cuando haya información disponible
- Si falta información, inferir de forma razonable y declararlo de forma breve dentro de la lógica de receta

---

## 🧭 PRINCIPIO FINAL

> El sistema no busca la receta perfecta, sino el rango correcto donde la receta se vuelve consistente, ajustable y repetible.

> Método define la base. Proceso mueve el rango. Tueste define cuánta energía aplicar. Frescura define cómo fluye la extracción. Variedad solo afina.

