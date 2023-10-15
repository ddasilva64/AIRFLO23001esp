# Conceptos básicos

## DAG (Directed Acyclic Graph)

**_Airflow_** utiliza grafos acíclicos dirigidos (**_DAG_**) para gestionar la organización del **_workflow_**. Las tareas y dependencias se definen en **_Python_** y luego **_Airflow_** gestiona la programación de tareas y la ejecución. Los **_DAG_** se pueden ejecutar en un horario definido (por ejemplo, cada hora o cada día) o en función de la ocurrencia de eventos externos (por ejemplo, un archivo que aparece en Hive​). Los programadores anteriores basados en **_DAG_** como Oozie y Azkaban tendían a depender de múltiples archivos de configuración y árboles del sistema de archivos para crear un **_DAG_**, mientras que en **_Airflow_**, los **_DAG_** a menudo se pueden escribir en un solo archivo **_Python_**. [Wikipedia](https://es.wikipedia.org/wiki/Apache_Airflow)  

### Grafo acíclico dirigido

En Ciencias de la computación y Matemáticas un grafo acíclico dirigido o **_DAG_** (Directed Acyclic Graph), es un grafo dirigido **que no tiene ciclos**; esto significa que para cada vértice v, no hay un camino directo que empiece y termine en v. Los **_DAG_** aparecen en modelos donde no tiene sentido que un vértice tenga un camino directo a él mismo; por ejemplo, si un arco u→v indica que v es parte de u, crear un ciclo v→u indicaría que u es subconjunto de sí mismo y de v, lo cual es imposible. Informalmente **un DAG "fluye" en solo una dirección, es decir, todas las aristas fluyen hacia una dirección**.  

<p><br></p>

![Grafo de tareas](https://i.imgur.com/7gjdEmD.png)  
_Grafo de tareas_

<p><br></p>

![Dirección única del DAG](https://i.imgur.com/oNVichM.png)  
_Dirección única del DAG_

Cada **DAG** da lugar a un ordenamiento parcial ≤ sobre sus vértices, donde u ≤ v exactamente cuando existe un camino directo desde u a v. Muchos **_DAG_** pueden generar el mismo ordenamiento parcial de los vértices siendo el de menor número de arcos denominado la reducción transitiva y el que mayor número de arcos la Clausura transitiva. En particular, la clausura transitiva es el orden de accesibilidad ≤. Es decir, **un DAG no pueden tener ciclos. Una arista que sale de un nodo no puede volver a ese nodo.**  

![Un DAG no puede tener ciclos](https://i.imgur.com/W7KfffP.png)  
_Un DAG no puede tener ciclos_

<p><br></p>

![DAG en Python](https://i.imgur.com/M8xeRjM.png)  
_DAG en Python_

<p><br></p>

- **Fuente**: Vértice sin flujos (relaciones) de entrada.  
- **Sifón o sumidero**: Vértice sin flujos (relaciones) de salida.  
- Un **DAG** finito **tiene por lo menos una fuente y un sifón**.  
- **Profundidad de un vértice**: En un DAG finito, es la **longitud del camino más largo que existe desde una fuente a dicho vértice**.  
- **Altura de un vértice**: **Longitud más larga** del camino que exista **desde el vértice a un sifón**.  
- **Longitud de un DAG finito**: **Longitud (número de arcos) del camino directo más largo**. Dicha longitud **es igual a la máxima altura de todas las fuentes** e **igual a la máxima profundidad de todos los sifones**.  

<p><br></p>

![DAG en la interface de Airflow](https://i.imgur.com/cfWD7E8.png)  
_DAG en la interface de Airflow_

<p><br></p>

## Tasks y operators

