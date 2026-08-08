# Mining Anomalous Similarity-Based Association Rules as Exceptions to Dominant Rules Using Particle Swarm Optimization

Este proyecto documenta el descubrimiento de reglas de asociación anómalas basadas en similitud mediante el uso de Particle Swarm Optimization (PSO).

## Información General
* **Autor**: Erik Fernando Casillas Velasco
* **Institución**: Centro de Investigación Científica y de Educación Superior de Ensenada (CICESE), Unidad Académica Monterrey
* **Curso**: Minería de Datos
* **Fecha**: 6 de agosto de 2026
* **Estado del Proyecto**: Artículo preliminar. La metodología dominante está confirmada, pero los resultados anómalos son preliminares y están pendientes de una ejecución canónica reproducible.

## Síntesis del Proyecto
El proyecto propone una metodología integrada para descubrir reglas dominantes y reglas anómalas en conjuntos de datos mixtos. Las reglas anómalas se definen como excepciones condicionadas respecto a las regularidades o reglas dominantes. El enfoque utiliza partículas mixtas dentro de un algoritmo PSO para representar tanto condiciones continuas como categóricas, evitando la discretización rígida.

## Metodología
La arquitectura del método se organiza en tres etapas consecutivas:

1. **Preparación del conjunto de datos**: 
   * Se utiliza el Cardiovascular Disease Dataset con 70,000 observaciones. 
   * Las variables categóricas conservan sus valores nominales. 
   * Las variables continuas se procesan con un recorte (clipping) híbrido y normalización, usando cuantiles extremos y el intervalo intercuartílico.
2. **Minería de reglas dominantes**: 
   * Un primer PSO descubre reglas dominantes ($X \rightarrow Y$) utilizando criterios de soporte, confianza, lift, factor de certeza y complejidad. 
   * Se emplean funciones de activación triangular y gaussiana truncada para evaluar la similitud en las variables continuas.
3. **Minería condicionada de reglas anómalas**: 
   * Para cada regla dominante, se fija el antecedente $X$. 
   * Un segundo PSO optimiza condiciones adicionales $Z$ para buscar excepciones que conduzcan al consecuente opuesto, formando la estructura $X \wedge Z \rightarrow \neg Y$.

## Configuración Experimental y Resultados
* **Configuración Dominante**: Se emplearon 500 partículas y 50 iteraciones evaluadas sobre tres semillas distintas (55, 13, 33).
* **Resultados Dominantes**: 
   * Se encontraron 4,754 pBest (mejores posiciones personales) válidos. 
   * Tras aplicar un filtro de redundancia mediante Jaccard difuso, se consolidaron 1,742 familias de reglas representativas. 
   * De este grupo, 166 familias mostraron una alta estabilidad al aparecer en las tres semillas evaluadas.
* **Resultados Anómalos (Preliminares)**: 
   * En un barrido de validación, se encontraron 15 familias de excepciones para tres reglas dominantes seleccionadas. 
   * Dos de estas familias de reglas anómalas conservaron su estabilidad en múltiples semillas con una confianza mínima de 0.70.

## Limitaciones y Consideraciones Técnicas
* **Problema de Reproducibilidad**: La celda de código correspondiente al barrido completo de reglas anómalas en el notebook contiene un error sintáctico (una cadena de texto sin cierre), lo que impide ejecutarlo linealmente en su estado actual. Los resultados anómalos descritos provienen únicamente de las salidas guardadas y requieren reejecución.
* **Interpretación de Resultados**: Las masas equivalentes reportadas no son conteos exactos de pacientes. Las asociaciones encontradas funcionan como ejemplos exploratorios de la metodología técnica, por lo que no demuestran causalidad ni poseen validez clínica para inferencias médicas.
