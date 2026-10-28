# PBI, balanza comercial y tipo de cambio real

Repositorio de la investigación econométrica sobre Argentina. El análisis
utiliza datos trimestrales, el notebook principal y un informe en LaTeX.

## Archivos principales

- [`index.ipynb`](./index.ipynb): preparación de datos, pruebas econométricas,
  estimación del VECM, diagnósticos, pronósticos e interpretación.
- [`dt.csv`](./dt.csv): base de datos principal.
- [`results/`](./results/): tablas, gráficos y resultados generados por el
  notebook.
- [`latex/informe.tex`](./latex/informe.tex): informe compilable.
- [`distribucion_trabajo_capitulos_III_IV.md`](./distribucion_trabajo_capitulos_III_IV.md):
  guía detallada de la división del trabajo.
- [`.gitignore`](./.gitignore): archivos que no deben incorporarse al
  repositorio.

## Estructura de los capítulos

### Capítulo III: Tratamiento estadístico y análisis de resultados

```text
3.1 Identificación de variables
3.2 Determinación del modelo econométrico
3.3 Demostración de la hipótesis
```

### Capítulo IV: Conclusiones y recomendaciones

```text
4.1 Conclusiones
4.2 Recomendaciones
```

## División de tareas entre los integrantes

El trabajo se divide por bloques metodológicos completos. Cada integrante debe
entregar texto interpretativo, tablas y gráficos cuando correspondan; no basta
con copiar la salida numérica del notebook.

### Integrante 1: variables y tratamiento de datos

#### Secciones asignadas

```text
3.1 Identificación de variables
3.1.1 Variable dependiente o principal
3.1.2 Variables explicativas
3.1.3 Variable exógena
3.1.4 Operacionalización de variables
3.2.1 Tratamiento estadístico de los datos
3.2.2 Estadísticas descriptivas
```

#### Tareas

- Describir el PBI real, la balanza comercial y el tipo de cambio real.
- Explicar las transformaciones:

  \[
  BC_t=X_t-M_t,\qquad
  BC/PBI_t=\frac{BC_t}{PBI_t}
  \]

  \[
  \ln(PBI_t),\qquad \ln(TC\ real_t)
  \]

- Describir la dummy COVID, activa en 2020-II y 2020-III.
- Documentar las fuentes INDEC y BCRA.
- Explicar el periodo 2004-I a 2026-II y la frecuencia trimestral.
- Describir las 90 observaciones, las 82 observaciones de entrenamiento y las
  8 observaciones de holdout.
- Revisar fechas duplicadas, valores faltantes y orden cronológico.
- Preparar la tabla de operacionalización.
- Interpretar las estadísticas descriptivas y los gráficos iniciales.

#### Entregables

1. Tabla de operacionalización.
2. Descripción de la base.
3. Tabla de estadísticas descriptivas.
4. Gráficos de las variables.
5. Texto metodológico sobre las transformaciones.

### Integrante 2: pruebas econométricas y selección del modelo

#### Secciones asignadas

```text
3.2.3 Pruebas ADF y KPSS
3.2.4 Prueba de Zivot-Andrews
3.2.5 Selección de rezagos
3.2.6 Prueba de cointegración de Johansen
3.2.7 Justificación del modelo VECM
```

#### Tareas

- Explicar las hipótesis y reglas de decisión de ADF y KPSS.
- Interpretar los resultados en niveles y primeras diferencias.
- Justificar que las variables del sistema son \(I(1)\).
- Explicar Zivot-Andrews y las rupturas estructurales sugeridas.
- Justificar por qué las fechas de Zivot-Andrews no se incorporaron
  automáticamente como dummies.
- Presentar AIC, BIC, HQIC y FPE.
- Explicar la selección de \(p=1\).
- Calcular y explicar:

  \[
  k_{\mathrm{ar\_diff}}=p-1=0
  \]

- Presentar la prueba de Johansen y justificar \(r=1\).
- Explicar por qué variables \(I(1)\) con cointegración requieren un VECM.

#### Entregables

1. Tabla ADF y KPSS.
2. Tabla o texto de Zivot-Andrews.
3. Tabla de criterios de rezagos.
4. Tabla de Johansen.
5. Justificación escrita del VECM.

### Integrante 3: estimación y diagnóstico del VECM

#### Secciones asignadas

```text
3.2.8 Estimación del modelo VECM
3.2.9.1 Autocorrelación de los residuos
3.2.9.2 Normalidad de los residuos
3.2.9.3 Estabilidad del modelo
3.2.9.4 Causalidad de Granger
```

#### Tareas

- Presentar la especificación del VECM:

  \[
  \Delta Y_t=\Pi Y_{t-1}+\Psi COVID_t+\varepsilon_t
  \]

- Interpretar la relación de largo plazo:

  \[
  \ln(PBI)+3.3005(BC/PBI)-0.2933\ln(TC\ real)
  +\text{constante}=0
  \]

- Interpretar los coeficientes de ajuste de las tres ecuaciones.
- Interpretar constantes y coeficientes de COVID de `fitted.summary()`.
- Analizar autocorrelación residual, normalidad y estabilidad CUSUM.
- Interpretar Granger como capacidad predictiva, no como causalidad
  estructural absoluta.

#### Resultados de referencia

| Ecuación | Coeficiente de ajuste | p-valor |
|---|---:|---:|
| \(\Delta\ln(PBI)\) | -0.0451 | 0.337 |
| \(\Delta BC/PBI\) | -0.1354 | <0.001 |
| \(\Delta\ln(TC\ real)\) | -0.3138 | 0.001 |

| Dirección | p-valor |
|---|---:|
| \(BC/PBI \rightarrow \ln(PBI)\) | 0.443 |
| \(\ln(PBI) \rightarrow BC/PBI\) | 0.012 |

#### Entregables

1. Tabla de la relación de largo plazo.
2. Tabla de coeficientes de ajuste.
3. Interpretación de constantes y COVID.
4. Diagnósticos del modelo.
5. Interpretación de Granger y CUSUM.

### Integrante 4: IRF, FEVD, pronósticos e hipótesis

#### Secciones asignadas

```text
3.2.9.5 Funciones impulso-respuesta
3.2.9.6 Descomposición de la varianza
3.2.10 Evaluación fuera de muestra
3.3 Demostración de la hipótesis
CAPÍTULO IV: Conclusiones y recomendaciones
```

#### Tareas

- Interpretar las funciones impulso-respuesta.
- Analizar la respuesta del PBI ante shocks de la balanza comercial.
- Interpretar la FEVD del PBI y la importancia relativa de cada shock.
- Explicar la dependencia de IRF y FEVD respecto del orden de identificación.
- Describir el entrenamiento 2004-I--2024-II y el holdout
  2024-III--2026-II.
- Interpretar RMSE, MAE y MAPE.
- Demostrar la hipótesis general y las hipótesis específicas usando todos los
  resultados anteriores.
- Elaborar el cuadro resumen de decisiones.
- Redactar las conclusiones y recomendaciones del Capítulo IV.

#### Resultados de referencia

| Variable | RMSE | MAE | MAPE |
|---|---:|---:|---:|
| \(\ln(PBI)\) | 0.0601 | 0.0595 | 0.44% |
| \(BC/PBI\) | 0.0282 | 0.0228 | 62.26% |
| \(\ln(TC\ real)\) | 0.1299 | 0.1006 | 2.23% |

El MAPE de \(BC/PBI\) debe interpretarse con cautela porque la variable puede
acercarse a cero y cambiar de signo; deben priorizarse RMSE y MAE.

#### Entregables

1. Interpretación de IRF.
2. Interpretación de FEVD.
3. Evaluación de pronósticos.
4. Cuadro de decisiones de hipótesis.
5. Conclusiones.
6. Recomendaciones.

## Orden de trabajo

```text
Integrante 1: variables y datos
        ↓
Integrante 2: pruebas y selección del VECM
        ↓
Integrante 3: estimación y diagnóstico
        ↓
Integrante 4: interpretación, hipótesis y conclusiones
```

El Integrante 1 debe entregar primero las variables y transformaciones. El
Integrante 2 debe confirmar la integración, los rezagos y el rango antes de que
el Integrante 3 interprete la estimación. El Integrante 4 debe utilizar los
resultados finales del modelo, sin modificar especificaciones por separado.

## Resultados que todos deben mantener

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

Modelo final:
    VECM

Rango de cointegración:
    r = 1

Rezago del VAR en niveles:
    p = 1

Rezagos de diferencias:
    k_ar_diff = 0
```

## Reglas para evitar inconsistencias

- No presentar un VAR en niveles como modelo final.
- No utilizar los resultados antiguos con \(r=3\).
- No cambiar variables, rezagos o rango sin volver a estimar el modelo.
- Diferenciar entre relación de largo plazo, causalidad predictiva, respuesta
  ante shocks y capacidad de pronóstico.
- No afirmar que la balanza comercial no tiene ninguna relación con el PBI
  únicamente porque Granger presenta \(p=0.443\).
- No interpretar Granger como causalidad estructural definitiva.
- No utilizar el MAPE de \(BC/PBI\) como único criterio de desempeño.
- Evaluar cada hipótesis según su redacción exacta en el Capítulo I.
- Mantener la diferencia entre “se rechaza \(H_0\)” y “no se rechaza \(H_0\)”.
- Verificar que todas las tablas y figuras provengan de la misma ejecución del
  notebook.

## Verificación antes de entregar

Cada integrante debe comprobar que su sección:

- Utiliza la misma nomenclatura: \(\ln(PBI)\), \(BC/PBI\) y
  \(\ln(TC\ real)\).
- Reporta correctamente estadísticos y p-valores.
- Explica hipótesis y reglas de decisión.
- Incluye interpretación económica, no solo resultados numéricos.
- Mantiene el periodo 2004-I--2026-II.
- Mantiene la división 82/8 entre entrenamiento y holdout.
- Utiliza el VECM como modelo final.
- Entrega tablas, gráficos y texto revisado.

Para obtener el detalle completo de cada tarea, consultar
[`distribucion_trabajo_capitulos_III_IV.md`](./distribucion_trabajo_capitulos_III_IV.md).
