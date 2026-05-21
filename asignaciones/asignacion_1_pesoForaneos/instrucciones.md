# Asignación 1: Optimización de Recursos Colectivos y Consenso Social 🏛️📊

## 🎯 Objetivo del Proyecto
El estudiante diseñará e implementará un script en Python que procese de forma automatizada los tokens de disponibilidad generados por la sección en WhatsApp. El núcleo del reto consiste en modelar una **Métrica Juez** o función de costo que determine matemáticamente el **Peso Ideal ($W_f$)** de influencia que se le debe otorgar a un estudiante foráneo para equilibrar de forma "justa" el sistema, protegiendo a la minoría vulnerable sin destruir el bienestar de la mayoría local.

---

## 🛠️ Especificaciones Técnicas del Script
Para resolver este problema, se recomienda ampliamente el uso de herramientas de Inteligencia Artificial (como Gemini o ChatGPT) para asistir en la generación de la estructura del código. El script final debe operar bajo las siguientes fases lógicas:

1. **Fase de Ingesta (Parsing):** El programa debe leer un archivo plano `.txt` que contenga los tokens codificados en Base64 enviados por el grupo. Debe decodificar cada token de forma segura, convirtiendo la cadena Base64 de vuelta a un objeto JSON legible en Python.
2. **Fase de Simulación Lineal:** El algoritmo debe iterar progresivamente variando un factor de peso para los estudiantes foráneos (`f = True`) en un rango continuo desde **1.0 hasta 10.0** (con incrementos discretos de 0.1). El peso de los locales se mantendrá estático en 1.0.
3. **Fase de Optimización Colectiva:** Por cada incremento de peso, el script evaluará todo el espacio de estados de bloques horarios disponibles (Lunes a Viernes, de 08-10 hasta 14-16) para hallar cuál es el bloque óptimo.
4. **Fase de Visualización:** El script debe generar, utilizando librerías de graficación (como `matplotlib` o `seaborn`), una gráfica analítica impecable que relacione el peso del foráneo en el eje $X$ con la puntuación de la métrica juez en el eje $Y$, señalando visualmente el punto crítico de equilibrio o "Peso Ideal".

---

## 🧠 Restricciones Obligatorias de la Métrica Juez
La función de costo no puede ser un simple conteo plano de asistencias. Es **estrictamente obligatorio** que su diseño incorpore el vector de preferencias ideales, denotado en el JSON como **"Quiero" (`v_d`)**, adicionalmente al vector de disponibilidad **"Puedo" (`v_p`)**. 

Su fórmula interna debe:
* **Premiar la satisfacción:** Otorgar un valor positivo base si el bloque coincide con un "Puedo", y un bono adicional si coincide con un "Quiero".
* **Penalizar la exclusión:** Aplicar un castigo numérico severo si el bloque seleccionado deja por completo a un estudiante sin posibilidad de asistir.
* **Ponderar por vulnerabilidad:** Multiplicar las recompensas y penalizaciones de cada estudiante por su peso correspondiente ($1.0$ para locales, $W_f$ actual para foráneos).

---

## 📋 Requisitos de Entrega
Cada estudiante debe cargar en su respectiva subcarpeta asignada dentro del directorio `estudiantes/` los siguientes archivos:

1. **`solucion.py` o `solucion.ipynb`:** El código fuente en Python, debidamente documentado, limpio y libre de errores de ejecución.
2. **`grafica_consenso.png`:** La imagen exportada directamente por el script donde se visualice claramente el comportamiento de la curva y el peso óptimo detectado.
3. **`defensa.md`:** Un breve reporte explicativo que responda con rigurosidad científica las siguientes preguntas:
   * ¿Cuál fue la lógica matemática/filosófica detrás del diseño de su Métrica Juez?
   * ¿Qué significado físico o social atribuye a la pendiente observada en su gráfica?
   * Basado en sus datos analizados, ¿cuál es el número exacto de la justicia para esta sección y qué bloque horario representa el consenso óptimo del sistema?

---

## 🤖 Guía de Orientación para Ingeniería de Prompts (Uso de IA)
Para desarrollar el código de forma eficiente, no intente escribir toda la sintaxis desde cero si presenta dificultades. Puede estructurar sus instrucciones a la IA dividiendo el problema. 

**Ejemplo de Prompt Base sugerido para iniciar:**
> *"Actúa como un científico de datos experto en Python. Necesito que generes un script estructurado que tome una lista de cadenas en Base64, las decodifique usando la librería `base64` y convierta el resultado de bytes a un diccionario JSON usando `json.loads`. Asegúrate de incluir un bloque `try-except` robusto con manejo de excepciones por si alguna cadena de texto llega corrupta o le falta relleno (padding), de modo que el programa avise en consola el error pero continúe procesando los elementos válidos."*

A partir de allí, proceda a encadenar prompts para solicitar la lógica del ciclo de simulación, las operaciones matemáticas de su métrica juez y el código para renderizar la gráfica. ¡Concéntrese en el diseño del modelo, deje que la IA maneje la sintaxis!
