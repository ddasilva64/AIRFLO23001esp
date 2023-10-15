# Introducción a Apache Airflow

## Introducción

Airflow es una plataforma creada por la comunidad para crear, programar y supervisar flujos de trabajo de forma programada.

**_Apache Airflow_** es una plataforma de gestión de flujo de trabajo de código abierto escrita en **_Python_**, donde los flujos de trabajo se crean a través de scripts en ese lenguaje. Fue creada por Airbnb en octubre de 2014 como solución para la gestión de flujos de trabajo dentro de la empresa.​ Al crear **_Airflow_**, Airbnb logró manejar más fácilmente sus flujos de trabajo y controlarlos gracias a la interfaz de usuario incluida en la herramienta.​ Desde el principio, el proyecto fue distribuido como código abierto y se convirtió en un proyecto de Incubadora de apache en marzo de 2016 y un proyecto de software de nivel superior de la **_Fundación Apache_** en enero de 2019.  

**_Airflow_** está escrito en **_Python_** y los workflows son creados vía scripts en ese lenguaje. **_Airflow_** Está diseñado bajo el principio de "configuración como código". Si bien hay otras plataformas de flujos de trabajo que también trabajan bajo el principio "configuración como código", la mayoría utiliza **_XML_**. Al utilizarse **_Python_** en **_Airflow_**, los desarrolladores pueden importar bibliotecas y clases para ayudarles crear sus flujos de trabajo.  

[Fuente Wikipedia](https://es.wikipedia.org/wiki/Apache_Airflow)

## ¿Para qué sirve Airflow?

### Flujo de trabajo (**_workflow_**)

Es el estudio de los aspectos operacionales de una actividad de trabajo: cómo se estructuran las tareas, cómo se realizan, cuál es su orden correlativo, cómo se sincronizan, cómo fluye la información que soporta las tareas y cómo se le hace seguimiento al cumplimiento de las tareas. Generalmente los problemas de flujo de trabajo se modelan con **_redes de Petri_**.  

Si bien el concepto de **_workflow_** no es específico a la tecnología de la información, una parte esencial del software para trabajo colaborativo (**_groupware_**) es justamente el **_workflow_**.

Una aplicación de **_workflow_** automatiza la secuencia de acciones, actividades o tareas utilizadas para la ejecución del proceso, incluyendo el seguimiento del estado de cada una de sus etapas y la aportación de las herramientas necesarias para gestionarlo.

Se pueden distinguir tres tipos de actividad:

1. **Actividades colaborativas**: Un conjunto de usuarios trabajan sobre un mismo repositorio de datos para obtener un resultado común. Tiene entidad el trabajo de cada uno de ellos en sí mismo.  
2. **Actividades cooperativas**: Un conjunto de usuarios trabajan sobre su propio conjunto particular, estableciendo los mecanismos de cooperación entre ellos. No tiene entidad el trabajo de ninguno de ellos si no es visto desde el punto de vista global del resultado.  
3. **Actividades de coordinación**.

Objetivos de un sistema de **_workflow_**:  

- Reflejar, mecanizar y **automatizar los métodos** y organización **en el sistema de información.**  
- Establecer los **mecanismos de control y seguimiento de los procedimientos organizativos**.  
- **Independizar** el método y **flujo de trabajo de las personas que lo ejecutan.**  
- **Facilitar la movilidad del personal**.  
- Soportar procesos de **reingeniería de negocio**.  
- **Agilizar** el proceso de **intercambio de información y la toma de decisiones** de una organización, empresa o institución.  
- Adicionalmente **optimizar el servicio**.  
- **Mejorar la gestión del conocimiento**.  

[Fuente Wikipedia](https://es.wikipedia.org/wiki/Flujo_de_trabajo)

### Canal de datos (**_data pipeline_**)

Un **_data pipeline_** es un término utilizado para describir un **_workflow_** que consta de una o más tareas que ingieren, mueven y transforman datos sin procesar desde uno o más orígenes a un destino. Por lo general, los datos en el destino se utilizan para análisis, aprendizaje automático u otras funciones comerciales. Generalmente, puede separar las canalizaciones de datos en dos categorías: batch o procesamiento por lotes (el más común) y canalizaciones de procesamiento en tiempo real.  

[Fuente Wiki Data Engineering](https://dataengineering.wiki/Concepts/Data+Pipeline)

<p><br></p>

![Ejemplo de uso de Airflow en la venta de paraguas](https://i.imgur.com/JnhHQS1.png)
_Ejemplo de uso de Airflow en la venta de paraguas_

<p><br></p>

![Ejemplo de uso de Airflow por equipo de Ventas y de Data](https://i.imgur.com/0kjBOLg.png)
_Ejemplo de uso de Airflow por equipo de Ventas y de Data_

<p><br></p>

[Ejemplo de uso de Airflow por equipo de Ventas y de Data -organización de tareas-](https://i.imgur.com/cr43MSJ.png)
_Ejemplo de uso de Airflow por equipo de Ventas y de Data -organización de tareas-_

<p><br></p>

**_Airflow_** organiza el **_workflow_**, pero no realiza los trabajos en sí. Un ejemplo simple de entender es el siguiente: si en medio de una tarea estamos procesando un **_dataframe_** de n millones de registros, esto va a ocupar mucha memoria y CPU, lo que se puede llegar a colapsar el sistema. El rendimiento en el Data es crucial por lo que tener todos los procesos en una misma máquina puede hacerla o muy costosa o ineficiente. Siempre es bueno distribuir las tareas complejas en diferentes máquinas para mejor eficiencia y reducir costos.

## ¿Por qué usar Airflow?

- Open-source.
- Se puede utilizar Python.
- Interfaz sencilla.
- Muchos roles utilizan Airflow.
- > 70% de profesionales del Data entrevistados por Apache, lo usan a diario.
- Es el proyecto más apoyado por desarrolladores en GitHub.
- Muchas empresas están adquiriendo esta herramienta.

<p><br></p>

![Airflow es open-source](https://i.imgur.com/VbhO1bE.png)
_Airflow es open-source_

<p><br></p>

![Perfiles que acostumbran a usar Airflow](https://i.imgur.com/1M0OGbQ.png)
_Perfiles que acostumbran a usar Airflow_

<p><br></p>

![Uso promedio diario de Airflow](https://i.imgur.com/K33yFSI.png)  
_Uso promedio diario de Airflow_

<p><br></p>

![Evolución en GitHub](https://i.imgur.com/j6zTEoI.png)
_Evolución en GitHub_

<p><br></p>

![Empresas que usan Airflow](https://i.imgur.com/lmernOL.png)
_Empresas que usan Airflow_

<p><br></p>

En mi trabajo la evolución ha sido:

1. Programas **_batch en Java_**.
2. **_QlikView_**.
3. **_Power BI_**.
4. **_Pentaho Data Integration (PDI)_**.

Inevitablemente, acabas llegando a **_Python_** y al **_workflow_**. He automatizado en jobs de **_PDI_** scripts en **_Python_** (de manera síncrona), pero comienzan a surgir nuevas necesidades y complejidades en esta “_capa de la cebolla_”, como carga de procesador, etc.

Solución para organizar el workflow: Apache Airflow, por supuesto!!! 😃

## Resumen

1. Desarrollar **_workflows_** con **_Python_**.
2. **_Organizar_** procesos.
3. **_Monitorizar_** ejecuciones.
4. Una **_herramienta muy usada_**.
5. Un **_job scheduler_** con esteroides (CRON ++).