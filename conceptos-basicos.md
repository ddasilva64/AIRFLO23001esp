# Conceptos básicos

**_Apache Airflow_** es un software libre de organización de **_flujos de trabajo_**, creados mediante de scripts de **_Python_**, los cuales pueden ser monitorizados en su interfaz de usuario.  

Ejemplos de **_flujos de trabajo_** en lo que podríamos utilizar **_Airflow_**:  
- **Programación de pipelines ETL**.  
- **Generación automática de informes**.  
- **Ejecución periódica de backups**.
- Etc.  

**_¡Nota muy importante!_**: **_Airflow_** **no es una herramienta ETL**, es decir, el **objetivo de **_Airflow_** no es tratar datos** (especialmente cuando el tamaño de estos es considerable), sino las tareas que los tratan, siguiendo el **orden y el flujo definido por el usuario**.

## Componentes

  1. **_Web Server_**: Provee la **interfaz gráfica** en la cual interactuamos con los **_flujos de trabajo_** y podemos controlar el **estado de las **_tareas_**** que los componen. 

  2. **_Scheduler_**: Planificador la ejecución de las ****_tareas_** y los pipelines**.   
  
  3. **_Executor_**: Define cómo van a ser ejecutadas las **_tareas_**.  
  3.1. **_SequentialExecutor_**:  **_Tareas_** que se ejecutan secuencialmente.  
  3.2. **_LocalExecutor_**: **_Tareas_** que se ejecutan paralelamente.  
  3.3. **_CeleryExecutor_**:  **_Tareas_** que se ejecutan paralelamente.  
  etc.

  4. **_Worker_**: Proceso o subproceso que ejecuta las tareas. Dependiendo de la configuración del **_Executor_**, habrá uno o varios **_Workers_** que reciban diferentes **_tareas_**. 
  
  5. **_Metastore_**: BD donde se guardan todos los metadatos de **_Airflow_** y de los **_flujos de trabajo_** definidos. Es utilizado por el **_Scheduler_**, el **_Executor_** y el **_Webserver_** para guardar sus estados.

## Flujos de trabajo

**Directed Acyclic Graph o Grafo Acíclico Dirigido (DAG)**: Unidad principal de un **_flujo de trabajo_** en **_Airflow_**. La propiedad acíclica del grafo permite que el **_DAG_** sea ejecutado de principio a fin sin entrar en ningún bucle. Informalmente **un DAG "fluye" en solo una dirección, es decir, todas las aristas fluyen en una dirección**. 

**_Tareas_**: Los **nodos** del grafo (**_DAG_**).  

**_Relaciones y dependencias entre las tareas_**: Las **aristas dirigidas** del grafo (**_DAG_**).  

<p><br></p>

![Grafo de tareas](https://i.imgur.com/7gjdEmD.png)  
_Grafo de tareas_

<p><br></p>

![Dirección única del DAG](https://i.imgur.com/oNVichM.png)  
_Dirección única del DAG_

<p><br></p>

![Un DAG no puede tener ciclos](https://i.imgur.com/W7KfffP.png)  
_Un DAG no puede tener ciclos_

<p><br></p>

![DAG en Python](https://i.imgur.com/M8xeRjM.png)  
_DAG en Python_

<p><br></p>

Características de un **_DAG_**:

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

## Scheduler
