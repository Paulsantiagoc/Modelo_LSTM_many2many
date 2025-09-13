# Modelo_LSTM_many2many
Este repositorio implementa un pipeline para predecir el flujo vehicular (Flow) en cada intersección a partir de series temporales con tres variables: Occupancy, Flow y Speed. El modelo, basado en una red LSTM many-to-many, captura dependencias temporales y patrones conjuntos de estas señales para estimar el flujo futuro en cada intersección.

## Objetivo
Desarrollar un modelo de prediccion a traves de series temporales (LSTM) para predecir la el flujo vehicular en 30 intersecciones urbanas, abordando simultáneamente la influencia de otras caracteristicas como el porcentaje de ocupoacion, la velocidad y el propio flujo de cada interseccion tomando en cuenta un enfoque dinámico histórica del tráfico.

## Introducción
El tráfico urbano es una problemática creciente causada por la saturación vial, el aumento poblacional y limitaciones de infraestructura. Este proyecto propone un enfoque para mejorar la gestión del tráfico mediante la integración de:

- **Dependencias temporales**: Patrones históricos a lo largo del tiempo con la caracteristica de multiples inputs y multiples outputs

Además, el archivo `Presentacion.pptx` presenta un resumen en formato de diapositivas con los aspectos clave del trabajo realizado, complementando la comprensión del modelo y sus resultados.

---

## Metodología
El modelo se basa en:

1. **Componente temporal (LSTM)**  
   - Captura patrones **secuenciales** en el tiempo a partir de las representaciones y variables históricas. Para este estudio son 3 variables por cada interseccion.
   - El modelo utiliza una **ventana temporal de cuatro pasos**.
   
![Arquitectura GCN + LSTM](Figura_7.jpg)

---

## Datos
Los datos utilizados provienen del **Departamento de Transporte de California** e incluyen:
- Velocidad promedio, **Flow** (flujo), **Occupancy** (ocupación) vehicular y **Speed** (velocidad).
- **30 intersecciones** de la Interestatal 5 (I-5).
- **Resolución temporal**: 5 minutos.
- **Entrenamiento**: 80%
- **Prueba**: 20%

### Tabla de intersecciones analizadas
Esta tabla muestra las intersecciones analizadas, incluyendo su identificación, nombre, latitud y longitud:

| **ID**  | **Name**               | **Lat**     | **Long**       |
|---------|------------------------|-------------|----------------|
| 715947  | S OF 710               | 34.015325   | -118.17127     |
| 716930  | FERRIS                 | 34.013529   | -118.166192    |
| 718085  | TRIGGS                 | 34.011229   | -118.161247    |
| 716928  | ATLANTIC               | 34.007592   | -118.157266    |
| 718364  | GASPAR                 | 34.002455   | -118.151164    |
| 716924  | WASHINGTON 1           | 33.994935   | -118.14469     |
| 763980  | MALT                   | 33.992211   | -118.142079    |
| 716922  | GARFIELD               | 33.986224   | -118.136014    |
| 768523  | GREENWOOD              | 33.981723   | -118.130845    |
| 716920  | SLAUSON                | 33.97646    | -118.125953    |
| 715929  | GUATEMALA              | 33.971707   | -118.123095    |
| 716895  | PARAMOUNT              | 33.963867   | -118.11987     |
| 716918  | LAKEWOOD 2             | 33.958225   | -118.11239     |
| 716916  | LAKEWOOD 1             | 33.956897   | -118.110532    |
| 763990  | GARNISH                | 33.952949   | -118.105163    |
| 715920  | S OF 605               | 33.938544   | -118.094941    |
| 715916  | TINA                   | 33.924281   | -118.084952    |
| 716912  | PIONEER                | 33.920763   | -118.082501    |
| 716911  | IMPERIAL               | 33.916643   | -118.079557    |
| 716908  | SAN ANTONIO/NORWALK    | 33.911074   | -118.071686    |
| 759610  | SILVER BOW             | 33.907584   | -118.067796    |
| 716906  | FIRESTONE              | 33.903961   | -118.064046    |
| 716907  | ROSECRANS              | 33.900669   | -118.059422    |
| 763706  | FIDEL                  | 33.896666   | -118.052294    |
| 716902  | CARMENITA              | 33.892489   | -118.044573    |
| 763748  | SPRING                 | 33.89061    | -118.041088    |
| 716898  | VALLEY VIEW            | 33.882892   | -118.026822    |
| 716896  | PHOEBE                 | 33.879952   | -118.021355    |
| 762398  | OSMOND                 | 33.876316   | -118.014605    |
| 762347  | ARTESIA                | 33.875077   | -118.012367    |

---

## Resultados y comentarios
- El modelo demuestra **buen desempeño** al capturar patrones espaciales y temporales.
- Iguala a métodos tradicionales de predicción de tráfico en precisión.
- El modelo tiene problemas de Escalabilidad ya que para casos donde las redes viales son más grandes puede requerir recursos computacionales sumamente altos o incluso una orquestación distribuida.

### Graficos 
Ejemplo para 1 interseccion:
![Resultados de la intersección 1 para el set de Train](Figura_8A.png)  

---

## Instrucciones de Uso

### Entorno de prueba
- Proyecto desarrollado y probado en **Google Colab**.

### Archivos de datos
- Archivo original: `pems08_dataframe_30nodes.xls`  

### Pasos
1. **Clonar** el repositorio.
2. **Subir** ambos archivos a tu entorno de **Google Colab**.
3. **Instalar** bibliotecas necesarias (PyTorch, `pandas`, `numpy`, etc.).
4. **Procesar** los datos con el código provisto.
5. **Entrenar** el modelo de series temporales (**LSTM**).
6. **Evaluar** los resultados sobre los conjuntos de **entrenamiento** y **prueba**.

### Ejecutar el modelo
Los datos y el código fuente están disponibles en [este repositorio de GitHub](https://github.com/tu_usuario/tu_repositorio).
