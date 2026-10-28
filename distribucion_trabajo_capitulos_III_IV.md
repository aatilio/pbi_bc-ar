# Distribución del trabajo de los capítulos III y IV

## Investigación econométrica sobre Argentina

Este documento organiza el trabajo de cuatro personas para redactar el
**Capítulo III: Tratamiento estadístico y análisis de resultados** y el
**Capítulo IV: Conclusiones y recomendaciones**.

La división sigue el flujo del notebook:

1. Identificación y preparación de los datos.
2. Pruebas econométricas y selección del modelo.
3. Estimación y diagnóstico del VECM.
4. Interpretación económica, demostración de hipótesis, conclusiones y recomendaciones.

---

## 1. Estructura general del documento

### CAPÍTULO III
## TRATAMIENTO ESTADÍSTICO Y ANÁLISIS DE RESULTADOS

### 3.1. Identificación de variables

#### 3.1.1. Variable dependiente o principal

#### 3.1.2. Variables explicativas

##### 3.1.2.1. Balanza comercial relativa

##### 3.1.2.2. Tipo de cambio real

#### 3.1.3. Variable exógena

##### 3.1.3.1. Dummy COVID

#### 3.1.4. Operacionalización de variables

### 3.2. Determinación del modelo econométrico

#### 3.2.1. Tratamiento estadístico de los datos

#### 3.2.2. Estadísticas descriptivas

#### 3.2.3. Pruebas de estacionariedad ADF y KPSS

#### 3.2.4. Prueba de Zivot-Andrews

#### 3.2.5. Selección de rezagos

#### 3.2.6. Prueba de cointegración de Johansen

#### 3.2.7. Justificación del modelo VECM

#### 3.2.8. Estimación del modelo VECM

#### 3.2.9. Diagnóstico y análisis complementario

##### 3.2.9.1. Autocorrelación de los residuos

##### 3.2.9.2. Normalidad de los residuos

##### 3.2.9.3. Estabilidad del modelo

##### 3.2.9.4. Causalidad de Granger

##### 3.2.9.5. Funciones impulso-respuesta

##### 3.2.9.6. Descomposición de la varianza

#### 3.2.10. Evaluación fuera de muestra

### 3.3. Demostración de la hipótesis

#### 3.3.1. Hipótesis general

#### 3.3.2. Hipótesis específica 1

#### 3.3.3. Hipótesis específica 2

#### 3.3.4. Hipótesis específica 3

#### 3.3.5. Resumen de decisiones

### CAPÍTULO IV
## CONCLUSIONES Y RECOMENDACIONES

### 4.1. Conclusiones

### 4.2. Recomendaciones

---

## 2. Distribución entre cuatro personas

## Persona 1: variables y tratamiento de datos

### Secciones asignadas

```text
3.1 Identificación de variables
3.1.1 Variable dependiente o principal
3.1.2 Variables explicativas
3.1.3 Variable exógena
3.1.4 Operacionalización de variables
3.2.1 Tratamiento estadístico de los datos
3.2.2 Estadísticas descriptivas
```

### Contenido que debe desarrollar

- PBI real de Argentina.
- Balanza comercial:

  \[
  BC_t=X_t-M_t
  \]

- Balanza comercial relativa:

  \[
  BC/PBI_t=\frac{BC_t}{PBI_t}
  \]

- Tipo de cambio real:

  \[
  \ln(TC\ real_t)
  \]

- Dummy COVID:

  \[
  COVID_t=
  \begin{cases}
  1, & \text{2020-II y 2020-III}\\
  0, & \text{en los demás periodos}
  \end{cases}
  \]

- Fuentes de información: INDEC y BCRA.
- Periodo: 2004-I a 2026-II.
- Frecuencia: trimestral.
- Número total de observaciones: 90.
- Muestra de entrenamiento: 82 observaciones.
- Muestra holdout: 8 observaciones.
- Revisión de fechas duplicadas y valores faltantes.
- Estadísticas descriptivas.
- Gráficos iniciales de las variables.

### Entregables

1. Tabla de operacionalización.
2. Descripción de la base de datos.
3. Tabla de estadísticas descriptivas.
4. Gráficos de las variables.
5. Texto metodológico sobre las transformaciones utilizadas.

### Pregunta que debe responder

> ¿Qué variables se utilizan, de dónde provienen, cómo fueron transformadas y
> cómo se organizó la información?

---

## Persona 2: pruebas econométricas y selección del modelo

### Secciones asignadas

```text
3.2.3 Pruebas ADF y KPSS
3.2.4 Prueba de Zivot-Andrews
3.2.5 Selección de rezagos
3.2.6 Prueba de cointegración de Johansen
3.2.7 Justificación del modelo VECM
```

### Contenido que debe desarrollar

#### ADF y KPSS

Explicar las hipótesis, la regla de decisión y los resultados en niveles y en
primeras diferencias.

Conclusión esperada:

\[
\ln(PBI),\ BC/PBI,\ \ln(TC\ real)\sim I(1)
\]

#### Zivot-Andrews

- Explicar qué es una ruptura estructural.
- Presentar las hipótesis.
- Presentar los p-valores y las fechas sugeridas.
- Explicar por qué las fechas no se incorporaron automáticamente como dummies.
- Diferenciar esta prueba de ADF y KPSS.
- Justificar la dummy COVID por su fundamento económico y temporal.

#### Selección de rezagos

Presentar AIC, BIC, HQIC y FPE:

| Criterio | Rezago seleccionado |
|---|---:|
| AIC | 1 |
| BIC | 1 |
| HQIC | 1 |
| FPE | 1 |

Conclusión:

\[
p=1
\]

Para el VECM:

\[
k_{\mathrm{ar\_diff}}=p-1=0
\]

#### Johansen

Explicar:

\[
H_0:r\leq r_0
\]

\[
H_1:r>r_0
\]

Presentar:

| Rango | Estadístico de traza | Valor crítico al 5% | Decisión |
|---:|---:|---:|---|
| \(r=0\) | 49.5871 | 29.7961 | Se rechaza \(H_0\) |
| \(r=1\) | 10.8164 | 15.4943 | No se rechaza \(H_0\) |
| \(r=2\) | 0.0166 | 3.8415 | No se rechaza \(H_0\) |

Rango seleccionado:

\[
r=1
\]

#### Justificación del VECM

Explicar:

- Variables \(I(0)\) → VAR en niveles.
- Variables \(I(1)\) sin cointegración → VAR en diferencias.
- Variables \(I(1)\) con cointegración → VECM.

La decisión final es:

```text
Modelo: VECM
Rango de cointegración: r = 1
Rezago del VAR en niveles: p = 1
Rezagos de diferencias del VECM: k_ar_diff = 0
Variable exógena: COVID
```

### Entregables

1. Tabla ADF y KPSS.
2. Tabla o texto de Zivot-Andrews.
3. Tabla de criterios de rezagos.
4. Tabla de Johansen.
5. Texto que justifique por qué corresponde un VECM.

### Pregunta que debe responder

> ¿Por qué el modelo apropiado es un VECM y no un VAR en niveles o un VAR en
> diferencias?

---

## Persona 3: estimación y diagnóstico del VECM

### Secciones asignadas

```text
3.2.8 Estimación del modelo VECM
3.2.9.1 Autocorrelación de los residuos
3.2.9.2 Normalidad de los residuos
3.2.9.3 Estabilidad del modelo
3.2.9.4 Causalidad de Granger
```

### Contenido que debe desarrollar

#### Estimación del modelo

Presentar la especificación general:

\[
\Delta Y_t=\Pi Y_{t-1}+\Psi COVID_t+\varepsilon_t
\]

Como \(k_{\mathrm{ar\_diff}}=0\), no se incluyen rezagos adicionales de las
primeras diferencias.

#### Relación de largo plazo

Presentar:

\[
\ln(PBI)+3.3005(BC/PBI)-0.2933\ln(TC\ real)
+\text{constante}=0
\]

Interpretar los coeficientes de largo plazo y sus p-valores.

#### Coeficientes de ajuste

| Ecuación | Coeficiente | p-valor | Interpretación |
|---|---:|---:|---|
| \(\Delta\ln(PBI)\) | -0.0451 | 0.337 | No significativo |
| \(\Delta BC/PBI\) | -0.1354 | <0.001 | Significativo |
| \(\Delta\ln(TC\ real)\) | -0.3138 | 0.001 | Significativo |

#### Constantes y COVID

Interpretar los resultados de `fitted.summary()`:

| Ecuación | Término | Coeficiente | p-valor | Decisión al 5% |
|---|---|---:|---:|---|
| \(\ln(PBI)\) | Constante | 0.5441 | 0.332 | No significativo |
| \(\ln(PBI)\) | COVID | -0.0304 | 0.140 | No significativo |
| \(BC/PBI\) | Constante | 1.6159 | <0.001 | Significativo |
| \(BC/PBI\) | COVID | 0.0036 | 0.790 | No significativo |
| \(\ln(TC\ real)\) | Constante | 3.7387 | 0.001 | Significativo |
| \(\ln(TC\ real)\) | COVID | 0.0192 | 0.656 | No significativo |

Una constante significativa no debe interpretarse por sí sola como evidencia
de causalidad económica.

#### Diagnósticos

Desarrollar:

- Portmanteau o Ljung-Box para autocorrelación residual.
- Prueba de normalidad multivariada.
- CUSUM para estabilidad.
- Causalidad de Granger.

Resultados de CUSUM:

- \(\ln(PBI)\): \(p=0.3185\).
- \(BC/PBI\): \(p=0.6545\).
- \(\ln(TC\ real)\): \(p=0.9900\).

Resultados de Granger:

| Dirección | p-valor | Decisión |
|---|---:|---|
| \(BC/PBI \rightarrow \ln(PBI)\) | 0.443 | No se rechaza \(H_0\) |
| \(\ln(PBI) \rightarrow BC/PBI\) | 0.012 | Se rechaza \(H_0\) |

La causalidad de Granger debe interpretarse como capacidad predictiva, no como
causalidad estructural definitiva.

### Entregables

1. Tabla de la relación de largo plazo.
2. Tabla de coeficientes de ajuste.
3. Interpretación de constantes y COVID.
4. Diagnósticos del modelo.
5. Interpretación de Granger y CUSUM.

### Pregunta que debe responder

> ¿Qué relación de largo plazo existe, qué variables ajustan los desequilibrios
> y qué evidencia hay de capacidad predictiva?

---

## Persona 4: IRF, FEVD, pronósticos e hipótesis

### Secciones asignadas

```text
3.2.9.5 Funciones impulso-respuesta
3.2.9.6 Descomposición de la varianza
3.2.10 Evaluación fuera de muestra
3.3 Demostración de la hipótesis
CAPÍTULO IV: Conclusiones y recomendaciones
```

### Contenido que debe desarrollar

#### Funciones impulso-respuesta

Analizar:

- Respuesta del PBI ante un shock de la balanza comercial.
- Respuesta de la balanza comercial ante un shock del PBI.
- Respuesta del sistema ante shocks del tipo de cambio real.
- Signo, duración y significancia de las respuestas.
- Intervalos de confianza.

#### Descomposición de la varianza

Analizar qué proporción del error de pronóstico del PBI es explicada por:

- Shocks del propio PBI.
- Shocks de la balanza comercial.
- Shocks del tipo de cambio real.

También debe indicar que IRF y FEVD dependen del orden utilizado para
identificar los shocks, especialmente si se utiliza una descomposición de
Cholesky.

#### Evaluación fuera de muestra

División:

- Entrenamiento: 2004-I a 2024-II.
- Holdout: 2024-III a 2026-II.
- Observaciones reservadas: 8.

Resultados:

| Variable | RMSE | MAE | MAPE |
|---|---:|---:|---:|
| \(\ln(PBI)\) | 0.0601 | 0.0595 | 0.44% |
| \(BC/PBI\) | 0.0282 | 0.0228 | 62.26% |
| \(\ln(TC\ real)\) | 0.1299 | 0.1006 | 2.23% |

El MAPE de \(BC/PBI\) debe interpretarse con cautela porque la variable puede
acercarse a cero y cambiar de signo. Para esta variable se priorizan RMSE y
MAE.

#### Demostración de hipótesis

Debe utilizar todos los resultados anteriores.

##### Hipótesis general

Evaluar con:

- Relación de largo plazo.
- Coeficiente de ajuste.
- Granger.
- IRF.
- FEVD.

Conclusión actual: existe una relación de largo plazo, pero no se encontró
capacidad predictiva de \(BC/PBI\) hacia \(\ln(PBI)\), pues \(p=0.443\).

##### Hipótesis específica 1

Relacionarla con las pruebas de estacionariedad, si esa es la redacción
original de la hipótesis:

- ADF.
- KPSS.
- Zivot-Andrews.

##### Hipótesis específica 2

Relacionarla con la existencia de una relación de largo plazo:

- Johansen.
- Relación de cointegración.
- Coeficientes de ajuste.

##### Hipótesis específica 3

Relacionarla con la capacidad predictiva:

- Granger.
- IRF.
- FEVD.

Resultado actual:

- \(BC/PBI\) no causa predictivamente a \(\ln(PBI)\): \(p=0.443\).
- \(\ln(PBI)\) sí causa predictivamente a \(BC/PBI\): \(p=0.012\).

##### Resumen de decisiones

| Hipótesis | Prueba principal | Resultado | Decisión |
|---|---|---|---|
| General | VECM, Granger, IRF y FEVD | Relación de largo plazo, sin Granger de BC hacia PBI | Según la redacción exacta |
| Específica 1 | ADF, KPSS y ZA | Variables \(I(1)\) según el análisis conjunto | Según su formulación |
| Específica 2 | Johansen | \(r=1\) | Se confirma la cointegración |
| Específica 3 | Granger | Dirección PBI → BC/PBI | Se confirma solo en esa dirección |

### Capítulo IV

La Persona 4 debe redactar:

#### 4.1. Conclusiones

Incluir conclusiones sobre:

1. Estacionariedad e integración de las variables.
2. Selección del VECM.
3. Relación de largo plazo.
4. Coeficientes de ajuste.
5. Causalidad predictiva.
6. Estabilidad del modelo.
7. Capacidad predictiva fuera de muestra.

#### 4.2. Recomendaciones

Incluir recomendaciones sobre:

- Competitividad externa.
- Diversificación de exportaciones.
- Productividad y valor agregado.
- Infraestructura y costos logísticos.
- Coordinación de política cambiaria, monetaria y fiscal.
- Actualización de la base de datos.
- Modelos alternativos y pruebas de robustez.

### Entregables

1. Interpretación de IRF.
2. Interpretación de FEVD.
3. Evaluación de pronósticos.
4. Cuadro de decisiones de hipótesis.
5. Conclusiones.
6. Recomendaciones.

### Pregunta que debe responder

> ¿Qué implicaciones económicas tienen los resultados y qué hipótesis se
> confirman o no se confirman?

---

## 3. Orden de trabajo

El trabajo debe avanzar en este orden:

```text
Persona 1: variables y datos
        ↓
Persona 2: pruebas y selección del VECM
        ↓
Persona 3: estimación y diagnóstico
        ↓
Persona 4: interpretación, hipótesis y conclusiones
```

### Primera etapa: Persona 1

Debe entregar primero:

- Variables definitivas.
- Transformaciones.
- Fuentes.
- Periodo.
- Muestra de entrenamiento.
- Muestra holdout.
- Tabla de operacionalización.

### Segunda etapa: Persona 2

Debe utilizar exactamente las variables definidas por la Persona 1 y confirmar:

- Integración \(I(1)\).
- Rezago \(p=1\).
- Rango \(r=1\).
- Modelo VECM.

### Tercera etapa: Persona 3

Debe trabajar con el modelo definitivo:

```text
VECM
r = 1
k_ar_diff = 0
COVID exógena
```

No debe cambiar las variables ni el número de rezagos sin coordinarlo con el
resto del equipo.

### Cuarta etapa: Persona 4

Debe utilizar los resultados finales de la Persona 3 para:

- Interpretar IRF y FEVD.
- Analizar los pronósticos.
- Demostrar las hipótesis.
- Redactar conclusiones y recomendaciones.

---

## 4. Resultados que todos deben utilizar

Para evitar contradicciones, todos los integrantes deben utilizar exactamente
los siguientes valores:

```text
Periodo: 2004-I a 2026-II
Observaciones totales: 90
Entrenamiento: 82
Holdout: 8

Variables endógenas:
    ln_pib
    bc_pbi
    ln_tc_real

Variable exógena:
    covid

Modelo:
    VECM

Rango de cointegración:
    r = 1

Rezago del VAR en niveles:
    p = 1

Rezagos de diferencias:
    k_ar_diff = 0
```

### Resultados econométricos clave

- Las tres variables son \(I(1)\) según el análisis conjunto de ADF y KPSS.
- Los cuatro criterios de información seleccionan un rezago.
- Johansen selecciona un rango de cointegración \(r=1\).
- El modelo final es un VECM.
- COVID se incorpora como variable exógena.
- \(BC/PBI\) no causa predictivamente a \(\ln(PBI)\): \(p=0.443\).
- \(\ln(PBI)\) causa predictivamente a \(BC/PBI\): \(p=0.012\).
- CUSUM no detecta inestabilidad estadísticamente significativa.

---

## 5. Reglas para evitar inconsistencias

- No mencionar un VAR en niveles como modelo final.
- No utilizar los resultados antiguos con \(r=3\).
- No cambiar las variables del sistema sin actualizar todo el análisis.
- No cambiar el número de rezagos sin volver a estimar el modelo.
- No interpretar Granger como causalidad estructural absoluta.
- No afirmar que la balanza comercial no tiene ninguna relación con el PBI
  únicamente porque \(p=0.443\).
- Diferenciar siempre:
  - Relación de largo plazo.
  - Causalidad predictiva.
  - Respuesta ante shocks.
  - Capacidad de pronóstico.
- La hipótesis debe evaluarse según su redacción exacta en el Capítulo I.
- No utilizar el MAPE de \(BC/PBI\) como único criterio de desempeño.
- Revisar que todas las tablas, figuras y p-valores provengan de la misma
  ejecución del notebook.

---

## 6. Revisión final antes de entregar

Cada integrante debe comprobar que su sección:

- Utiliza la misma nomenclatura: \(\ln(PBI)\), \(BC/PBI\) y
  \(\ln(TC\ real)\).
- Reporta correctamente los p-valores.
- Explica la hipótesis y la regla de decisión de cada prueba.
- Distingue entre “se rechaza” y “no se rechaza” la hipótesis nula.
- No utiliza la expresión “se acepta \(H_0\)”; se recomienda escribir “no se
  rechaza \(H_0\)”.
- Mantiene el periodo 2004-I a 2026-II.
- Mantiene la división 82/8 entre entrenamiento y holdout.
- Utiliza el VECM como modelo final.
- Entrega tablas, gráficos y texto interpretativo, no únicamente resultados
  numéricos.

