# Trabajo Especial de Grado

Este repositorio contiene el código utilizado para realizar los experimentos planteados en el Trabajo Especial de Grado (TEG) "Estudio de Métodos de Proyecciones Alternantes para el entrenamiento de Redes Neuronales de Base Radial", presentada por Gabriel Jesús Carrizo Liendo.

## Estructura del repositorio

El repositorio está estructurado de la siguiente manera:

| Carpeta/Archivo       | Descripción                                         |
| --------------------- | --------------------------------------------------- |
| MAP/Experimentos1y2   | Jupyter Notebook con los Experimentos 1 y 2 del TEG |
| RBFNN/Experimentos3y4 | Jupyter Notebook con los Experimentos 3 y 4 del TEG |
| TEG_GabrielCarrizo    | PDF del Trabajo Especial de Grado                   |

## Experimentos

A continuación se presentan los experimentos realizados. Los resultados obtenidos se presentan brevemente en los Jupyter Notebooks asociados a los experimentos, pero se recomienda fuertemente leer el Capitulo de "Experimentos y Resultados" del TEG que se encuentra en este repositorio.

### Experimento 1
Dado que muchos de los métodos estudiados presentan un comportamiento estocástico, se consideró relevante analizar su distribución probabilística. Para ello, se generaron dos sistemas de ecuaciones lineales con la misma matriz aleatoria $A \in \mathbb{R}^{4000 \times 500}$: uno consistente con vector de términos independientes $b$ y otro inconsistente con un vector afectado por ruido $b_{LS}$, ambos generados de manera aleatoria. Con el objetivo de visualizar la distribución del número de iteraciones requeridas para la convergencia, cada método se ejecutó 500 veces por sistema, registrando el número de proyecciones realizadas en cada ejecución. La generación de estos sistemas aleatorios se explica a mayor detalle dentro del documento.

### Experimento 2
Para evaluar el desempeño de los métodos en términos de tiempo y cantidad de proyecciones, se generaron sistemas sobredeterminados, tanto consistentes como inconsistentes, de manera aleatoria. Debido a la naturaleza estocástica de los métodos y basándonos en los resultados del Experimento 1, cada método se ejecutó tres veces, tanto en CPU como en GPU, para obtener una representación realista de su rendimiento.

### Experimento 3
Dado que las variantes aleatorias de Kaczmarz generan soluciones mediante proyecciones secuenciales, se evaluó si una RBFNN, entrenada con una variante de estos métodos, tiene la capacidad de adaptar sus pesos a nuevos datos, reutilizando pesos previos.  Para ello, se entrenó una RBFNN con el 50\% del conjunto de datos de entrenamiento de MNIST, obteniendo una matriz de pesos inicial $W_0$. Esta matriz se utilizó como punto de partida para entrenar la misma RBFNN con el 75\% y 100\% de los datos entrenamiento  respectivamente, mediante el mismo algoritmo. Lo que se esperaba es que este enfoque acelerara la convergencia en comparación con un entrenamiento desde cero.

### Experimento 4
Se plantearon redes sencillas para comprobar que es más eficiente en tiempo resolver el problema de optimización $||B - \Phi W||$ que $p$ problemas del estilo $||b - \Phi w||$ para nuestros problemas de clasificación planteados. Luego, para cada uno de los tres conjuntos de datos especificados anteriormente en esta sección, se construyó una RBFNN entrenada utilizando la versión matricial de Cimmino acelerado por Gradientes Conjugados. Los tres conjuntos de datos utilizados son el conjunto MNIST, Fashion MNIST, y KMNIST.

Para la evaluación del desempeño del método, se comparó la RBFNN resultante con una RBFNN entrenada mediante la solución de mínimos cuadrados proporcionada por PyTorch, en términos de tiempo de entrenamiento y precisión de las predicciones. Nótese que los tiempos de entrenamiento pueden variar entre ejecuciones, por lo que se entrenó $30$ veces las redes y  se tomó su promedio de tiempos de ejecución. Por otro lado, para medir la precisión utilizaremos la métrica de exactitud, la cual se define como la proporción de predicciones correctas realizadas por el modelo en relación con el número total de predicciones.

## Uso

Para utilizar el código en este repositorio, se recomienda clonar el repositorio y ejecutar los Jupyter Notebooks en Google Collab. Para mayor eficiencia de ejecución, se recomiendo configurar este entorno con una GPU.

## Autor

- Gabriel Jesús Carrizo Liendo
