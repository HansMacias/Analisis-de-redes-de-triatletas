# Análisis de Variabilidad de la Frecuencia Cardíaca (HRV): Comparativa entre Sujetos Normales y Triatletas

Este cuaderno de Google Colab implementa un análisis exhaustivo de la Variabilidad de la Frecuencia Cardíaca (HRV) para comparar sujetos normales con triatletas, utilizando una combinación de métricas de dominio del tiempo, no lineales, espectrales y de redes complejas. El objetivo principal es identificar diferencias fisiológicas significativas y proporcionar un reporte estructurado para el monitoreo y la inferencia clínica.

## Estructura del Proyecto

El análisis se divide en las siguientes fases:

1.  **Carga y Preprocesamiento de Datos**: Carga de archivos de intervalos RR (Normales e Triatletas) y preparación de las series de tiempo.

2.  **Métricas No Lineales**: Cálculo de Detrended Fluctuations Analysis (DFA), Sample Entropy (SampEn) y Multiscale Entropy (MSE) utilizando la librería `nolds`.

3.  **Análisis Geométrico y Espectral**: Implementación del Mapa de Poincaré (SD1, SD2) y análisis espectral (Potencia LF, HF, LF/HF) mediante el método de Welch.

4.  **Métricas de Dominio del Tiempo y Estadísticas Clásicas**: Cálculo de Mean RR, SDNN, RMSSD y pNN50. Integración de la d de Cohen para evaluar la magnitud de las diferencias.

5.  **Análisis de Redes Complejas (Visibility Graphs)**:
    *   Implementación de algoritmos para construir Visibility Graphs a partir de las series de RR.
    *   Cálculo de 10 métricas de red avanzadas (Grado Promedio, Coeficiente de Agrupamiento, Longitud Media del Camino, Grado Máximo, Número de Nodos, Número de Aristas, Número de Clique, Número de Cliques Máximos, Grado Máximo del Clique Más Grande, Tamaño del Clique Más Grande) en ventanas de 500 puntos.
    *   Visualización de grafos de visibilidad con cliques resaltados, comparativas de cliques maximales y análisis de propiedades de red.

6.  **Inferencia Basada en Magnitud (MBI)**: Clasificación de las diferencias entre grupos en categorías clínicas (Trivial, Posible, Probable, Muy Probable).

7.  **Reporte Estructurado y Visualizaciones**: Generación de un reporte completo en español con una jerarquía de 11 carpetas, incluyendo:
    *   Gráficas comparativas para cada métrica (barras, mapas de Poincaré, PSD).
    *   Visualizaciones de redes complejas (grafos individuales, espacios de fase de resiliencia, propiedades de red).
    *   Tablas CSV consolidadas con todos los resultados numéricos y la clasificación MBI.
    *   Un dashboard de monitoreo fisiológico.

## Archivos de Entrada

El cuaderno espera 5 archivos `.txt` para sujetos Normales (ej. `N1_RR_cor.txt`, `N2_RR_cor.txt`, etc.) y 5 archivos `.txt` para Triatletas (ej. `I1_RR_cor.txt`, `I2_RR_cor.txt`, etc.). Estos archivos deben contener series de intervalos RR (RR-i) en milisegundos, una por línea. Se asume una longitud de serie adecuada para el análisis de ventanas (ej. 4000 puntos para 8 ventanas de 500).

## Salida

La ejecución final del cuaderno produce un archivo ZIP llamado `Reporte_HRV_Definitivo_Estructurado.zip`, que contiene toda la estructura de carpetas, gráficas y tablas CSV generadas. Este reporte está diseñado para ser una herramienta integral para el análisis y monitoreo de la HRV.

## Librerías Utilizadas

*   `numpy`
*   `pandas`
*   `matplotlib`
*   `seaborn`
*   `nolds`
*   `networkx`
*   `scipy`
*   `google.colab.files`
