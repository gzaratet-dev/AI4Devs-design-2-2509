# Prompts para generar el Backlog, casos de usos, tickets de trabajo del MVP-LTI
### Estos prompts se generaron con el modelo Gemini 2.5 Pro
---
## Contexto del Proyecto

Este documento contiene los prompts  para la creación del Backlog del LTI. Estos prompts establecieron la base conceptual de la definición de usuarios clave, épicas iniciales, historias de usuario detalladas (incluyendo criterios de aceptación), así como el análisis comparativo de tres enfoques distintos de metodologías de Backlog, que permitieran la generación de los primeros tickets de trabajo que definieran el primer sprint de trabajo en la implementación del MVP del sistema de seguimiento de talento.

---
### 1. Prompt Origen

Como Product Manager con 15 años de experiencia, analiza el archivo LTI-GEZT que representa el Product Requirements Document básico, que permita dar contexto en la generación del Backlog inicial, que sirva para la implementación del **Mínimo Producto Viable (MVP)** que valide la **Propuesta de Valor Única (PVU)**: **"ATS colaborativo con IA contextual que reduce time-to-hire y mejora calidad del hire."**

1. Genera épicas necesarias e historias de usuario necesarias para comenzar los requerimeintos funcionales y/o no funcionales mínimos para comenzar la implementación.

2. Las reglas de las historias de usuario son las siguientes:
   - Las user stories deben estar escritas desde la perspectiva del usuario final, no desde la perspectiva interna de la organización.
   - Utilizar personajes o "personas" para entender mejor las necesidades y objetivos de los usuarios.
   - Seguir el formato estándar: "Como [tipo de usuario], quiero [realizar una acción] para [obtener un beneficio]".
   - Evitar detalles técnicos o instrucciones de implementación.
   - Mantener las historias lo suficientemente pequeñas y entregables en un sprint (10 días laborales).
   - Priorizar las historias de usuario en función de su valor para el negocio y el usuario.
   - Estimar el esfuerzo requerido para implementar cada historia.
   - Definir claramente los criterios que deben cumplirse para considerar una historia "terminada".
   - Evitar centrarse en cómo se construirá la funcionalidad.
  
3. Estructura basica de una User Story
   - **Formato estándar:** "Como [tipo de usuario], quiero [realizar una acción] para [obtener un beneficio]".
   - **Descripción:** Una descripción concisa y en lenguaje natural de la funcionalidad que el usuario desea.
   - **Criterios de Aceptación:** Condiciones específicas que deben cumplirse para considerar la User Story como "terminada", éstos deberian de seguir un formato similar a “Dado que” [contexto inicial], "cuando” [acción realizada], “entonces” [resultado esperado].
   - **Notas adicionales:**  Notas que puedan ayudar al desarrollo de la historia
   - **Tareas:** Lista de tareas y subtareas para que esta historia pueda ser completada

---
### 2. Prompt primera iteración

Como product manager y en virtud de conocer distintas metodologías de Backlog, crea dos backlog más decirme qué ventajas y desventajas hay con respecto al inicial generado anteriormente para que me ayudes a definir cuaĺ es el más adecuado para este MVP.

---
### 3. Prompt segunda iteración

Siguiendo tu recomendación de tomar el Backlo inicial ya que ofrece el mejor equilibrio para un MVP. Toma de la Épica 1 Core ATS y Onboarding (P1) las HU para el primer sprint (10 días laborales) y genera los tickets de trabajo. Aterrizalos técnicamente, tal y como se hacen en las reuniones de planificación. Estima el esfuerzo de los tickets de trabajo usando la metodología que a tu criterio sea la más conocida y eficiente. Preparlas para iniciar el primer sprint.

---
### 4. Prompt tercera iteración

incluye los criterios de aceptación (detallado) de cada historia
