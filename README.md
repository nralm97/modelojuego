### MODELO DE JUEGO USANDO NMF + MAPAS DE CALOR

Cuando se comparan dos o más equipos (o jugadores) se suelen utilizar datos como cantidad de remates, centros, presiones, recuperaciones, etc. normalizados a 90 minutos. Este enfoque permite tener una idea de la fuerza y de las preferencias del equipo; sin embargo, para intentar bosquejar el estilo de juego no podemos obviar las zonas del campo donde sucede cada acción.

Es por ello que este enfoque tiene en cuenta tanto la frecuencia como la ubicación de los eventos. Este procedimiento consiste en extraer los componentes significativos de los mapas de calor de eventing utilizando NMF (Factorización de matrices no negativas), una técnica de Aprendizaje no supervisado. El conocimiento del negocio (en este caso fútbol) servirá para elegir en cuántas partes se va a descomponer el heatmap original.

Se utilizaron datos de la liga española 2015/2016 extraídos de una base de datos free de Statsbomb
A continuación algunas descomposiones:

<img src="https://github.com/user-attachments/assets/831d323d-2ceb-4d4a-8653-f77ced06b5d8" width="220"/>
<img src="https://github.com/user-attachments/assets/ecbd93f3-3704-441d-99d8-d98d4ce249d4" width="220"/>
<img src="https://github.com/user-attachments/assets/a0c042cc-0bba-4128-bcd0-6dd8370c0797" width="220"/>
<img src="https://github.com/user-attachments/assets/01215f54-c654-454b-9915-434a43905f5e" width="220"/>

Los eventos elegidos fueron los siguientes: 
- Con balón.- Tiros, Centros, Regates, Asistencias de tiro, Pases hacia el área rival, Corner, Saque de meta
- Sin balón.- Recuperaciones, Faltas, Presiones
Luego se realizó una descompoción para cada tipo de evento. Además este método de trabajo permite analizar y comparar a los equipos. 

### EJEMPLO
Utilizaremos como ejemplo, una comparación entre FC Barcelona y Real Madrid C.F. temporada 2015/2016, y elegiremos como evento: "Pases hacia el área rival". Estos dos equipos fueron los que más pases de este tipo realizaron, lo cual es natural considerando el poderío ofensivo de ambos. 

<img src="https://github.com/user-attachments/assets/84dd59c9-1da8-43c3-b8bd-00b75bd06000" width="450"/>

A pesar de que los conjuntos "blanco" y "blaugrana" son parecidos en cantidad de "Pases hacia el área rival"; vemos una diferencia en cómo llegan hacia ella.

- Centros cortos o recortes cercanos al área grande. - Fue la forma más recurrente de llegar al área para Real Madrid y se ubicó primero en este aspecto, mientras que Barcelona, aunque segundo, se asemeja más al Sevilla
- Centros amplios, más pegados a las líneas laterales. - Los dirigidos por Zidane estuvieron en la media de la liga, mientras que el cuadro 'culé' no usó esta forma de juego.
- Pases desde zona central. - FBC Barcelona se diferenció ampliamente de los demás equipos por utilizar este tipo de pases para penetrar área rival.

<img src="https://github.com/user-attachments/assets/5c5c01f0-c6db-4f3a-a8d0-27a973aa869f" width="500"/>

### VALIDACIÓN
Para la validación de usó MRR, para medir qué tan bien el modelo puede hacer coincidir a un equipo contra sí mismo basándose puramente en distribuciones de ubicación de eventos y frecuencias.
Para la distancia se utilizó distancia Manhattan
