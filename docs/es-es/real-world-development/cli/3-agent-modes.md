---
title: "Lección 3 - Modos del agente: Plan y Autopilot"
description: "Usa Plan para acordar un enfoque, Autopilot para crear el filtrado a partir de una incidencia e Interactive para revisar el resultado."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

Empezamos añadiendo una pequeña funcionalidad al proyecto, pero los cambios grandes requieren un proceso más sólido. GitHub Copilot CLI está diseñado para adaptarse al flujo existente de una organización y ayudarnos a construir lo correcto de la forma adecuada. En esta lección iniciarás un proceso de desarrollo guiado por un agente a partir de una incidencia, validarás el código y la funcionalidad y, finalmente, lo fusionarás en el proyecto.

> [!NOTE]
> Usarás la misma conversación y rama durante todo el flujo de la funcionalidad. Normalmente tendrías ramas o PR distintas para cada tipo de archivo, pero aquí simplificaremos el proceso para centrarnos en los conceptos principales.

En esta lección:

- iniciarás una conversación de Copilot a partir de una incidencia de GitHub;
- definirás los requisitos en el modo Plan;
- implementarás la funcionalidad con el modo Autopilot;
- revisarás el código;
- validarás manualmente la funcionalidad en un navegador reenviado.

Durante el resto del flujo actualizarás las instrucciones del repositorio, personalizarás la habilidad `quality-checks`, añadirás validación MCP, crearás un agente de QA y abrirás la PR.

## Escenario

El catálogo de Tailspin Toys crece y los visitantes necesitan filtrar los juegos por categoría y editorial. La incidencia describe la funcionalidad, pero antes de programar hay que acordar detalles como la combinación de categorías. Usarás el modo Plan para resolver esas decisiones y después autorizarás una implementación acotada con Autopilot.

## Contexto

Introducir agentes de IA en el flujo de desarrollo no cambia sus fundamentos. La mayoría de los desarrolladores siguen un proceso parecido:

1. Partir de una incidencia que describa el trabajo.
2. Crear un plan de lo que se debe construir.
3. Crear y revisar el código.
4. Ejecutar las pruebas para validarlo.
5. Validar manualmente la nueva funcionalidad.
6. Crear una pull request (PR).
7. Cuando se revise el código y finalice correctamente la integración continua, fusionarlo.

> [!NOTE]
> Los detalles exactos dependen del equipo y la organización, pero la mayoría de los procesos son una variación de este flujo.

Al seguir este enfoque, te aseguras de que el código generado por IA cumple los requisitos y pasa las mismas comprobaciones que el código escrito manualmente.

## Modos de conversación

El **modo de conversación** controla el grado de autonomía del agente. Pulsa <kbd>Shift</kbd>+<kbd>Tab</kbd> para alternar entre modos:

- **Interactive**: tú y el agente trabajáis juntos; el agente propone cambios y espera tu confirmación.
- **Plan**: el agente crea primero un plan y no puede editar los archivos del proyecto.
- **Autopilot**: el agente trabaja de forma autónoma, ejecuta pruebas y repite el proceso hasta completar la tarea.

Empieza en Plan, revisa el plan y después usa Autopilot para implementarlo.

## Empezar a partir de la incidencia

Antes de iniciar el filtrado, vuelve a tu Codespace y prepara el repositorio y el terminal.

1. Vuelve a tu Codespace. Si está detenido, reinícialo.
2. Confirma que la PR de las valoraciones por estrellas se ha fusionado.
3. Si no ves el terminal, pulsa <kbd>Control</kbd>+<kbd>\`</kbd> (Mac) o <kbd>Ctrl</kbd>+<kbd>\`</kbd> (Windows/Linux).
4. Actualiza `main` y crea una rama:

   ```bash
   git checkout main
   git pull --ff-only
   git checkout -b game-filters-cli
   ```

5. Inicia Copilot CLI:

   ```bash
   copilot --yolo
   ```

6. Pulsa dos veces <kbd>Tab</kbd> para abrir la pestaña **Issues**.
7. Pulsa <kbd>A</kbd> para mostrar todas las incidencias.
8. Selecciona **Allow users to filter games by category and publisher**.
9. Pulsa <kbd>C</kbd> para añadir la incidencia al prompt y volver a **Session**.

## Planificar la funcionalidad de filtrado

1. Pulsa <kbd>Shift</kbd>+<kbd>Tab</kbd> para cambiar al modo Plan.
2. Después de la referencia a la incidencia, introduce:

   ```text
   Create a plan for implementing this feature.
   ```

3. Responde a las preguntas sobre el filtrado según tus preferencias.
4. Cuando termine el plan, pulsa <kbd>Control</kbd>+<kbd>E</kbd> (Mac) o <kbd>Ctrl</kbd>+<kbd>E</kbd> (Windows/Linux) para expandirlo.
5. Revisa el plan y pide que revise cualquier parte que no coincida con tus decisiones.

## Aprobar Autopilot

1. Selecciona **Accept plan and build on autopilot (recommended)** o la opción equivalente de tu versión.
2. Confirma que el indicador muestra **Autopilot**.
3. Observa cómo Copilot recorre el plan, genera el código y ejecuta las pruebas.

> [!NOTE]
> La aprobación puede iniciar la implementación inmediatamente; revisa el plan antes. Si Copilot informa de dependencias ausentes o un conflicto de puertos, resuelve primero el problema de configuración.

## Revisar y verificar la implementación

1. Pulsa <kbd>Shift</kbd>+<kbd>Tab</kbd> para entrar en Interactive.
2. Introduce `/diff` y revisa la implementación y las pruebas.
3. Compárala con la incidencia y con las decisiones del plan.
4. Pulsa <kbd>Esc</kbd> para salir de la vista de diferencias.
5. Revisa las comprobaciones del proyecto y pide a Copilot que resuelva los errores.

## Explorar la nueva funcionalidad

1. Pide a Copilot que inicie la aplicación:

   ```text
   Start the app so I can try the filtering feature in my browser. Tell me the URL and leave the server running.
   ```

2. Cuando Codespaces indique que el puerto `4321` está disponible, selecciona **Open in Browser**.
3. Prueba el filtrado por categoría, por editorial y sus combinaciones.
4. Confirma que el reinicio y los resultados vacíos coinciden con la incidencia y tus decisiones.
5. Pide a Copilot que detenga el servidor de desarrollo.

## Resumen y siguientes pasos

Has usado distintos modos de conversación para crear y revisar una funcionalidad. En esta lección:

- iniciaste una conversación de Copilot desde una incidencia de GitHub;
- definiste los requisitos en Plan;
- implementaste la funcionalidad con Autopilot;
- revisaste el código;
- validaste manualmente la funcionalidad en un navegador reenviado.

Ahora profundizarás en la generación de código y en cómo hacer que siga las prácticas documentadas mediante [instrucciones personalizadas][next-lesson].

## Recursos

- [Autopilot en GitHub Copilot CLI][autopilot]
- [Referencia de comandos de Copilot CLI][cli-reference]

[autopilot]: https://docs.github.com/copilot/concepts/agents/copilot-cli/autopilot
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[previous-lesson]: ../2-add-star-rating/
[next-lesson]: ../4-custom-instructions/
