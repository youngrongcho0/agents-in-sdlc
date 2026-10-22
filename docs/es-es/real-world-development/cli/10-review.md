---
title: "Lección 10 - Resumen y próximos pasos"
description: "Recapitula el flujo de Copilot CLI, dos pull requests, las personalizaciones reutilizables y otros recursos."
authors:
  - geektrainer
lastUpdated: 2026-09-29
---

Has usado GitHub Copilot CLI durante un flujo continuo de Tailspin Toys. Has:

- preparado un Codespace, instalado Copilot CLI, explorado el proyecto y encontrado la incidencia de filtrado;
- añadido valoraciones por estrellas, revisado el resultado en un navegador reenviado y fusionado manualmente tu primera pull request (PR);
- partido de la incidencia de filtrado, definido el enfoque en Plan, creado la funcionalidad en Autopilot y revisado el resultado en Interactive;
- orientado al agente con instrucciones personalizadas, personalizado `quality-checks` y usado la habilidad para ejecutar pruebas unitarias, lint y comprobaciones de tipos;
- añadido el servidor Playwright Model Context Protocol (MCP) y usado un navegador real para explorar el filtrado;
- creado y seleccionado un agente personalizado de garantía de calidad (QA) para evaluar requisitos, cobertura, resultados y evidencias del navegador;
- revisado el cambio completo y autorizado Agent Merge para la PR de filtrado;
- explorado comandos de barra para contexto, modelos, uso compartido y delegación opcional en la nube.

## Lo que has entregado

El taller contiene dos hitos de PR, cada uno en su propia rama a partir de `main` actualizado:

1. **Valoraciones por estrellas:** muestra `starRating` y un estado explícito sin valoración en las tarjetas de juegos.
2. **Filtrado y flujo de calidad:** implementa el filtrado, actualiza las instrucciones y las aplica a la funcionalidad, personaliza el informe de `quality-checks`, crea un perfil de QA e incluye las pruebas correspondientes.

Desde la planificación del filtrado hasta la apertura de su PR usaste la misma conversación y rama. Combinamos ese trabajo en una única PR para simplificar el taller.

## Distintos tipos de verificación

Comprobaste el código de varias formas: pruebas automatizadas, inspección propia en el navegador y exploración del navegador por Copilot mediante MCP. La habilidad `quality-checks` ejecutó pruebas unitarias, lint y comprobaciones de tipos y las incluyó en el nuevo formato. QA combinó esos resultados con una revisión de los requisitos y la cobertura antes de la PR.

Las pruebas nuevas deben cubrir carencias reales; que una ejecución de QA no necesite pruebas nuevas puede ser correcto. Revisa el código y las evidencias antes de autorizar la fusión y actualiza las evidencias afectadas después de los cambios.

## Buenas prácticas

El contexto y las herramientas que proporcionas a Copilot determinan su trabajo. En este taller actualizaste instrucciones, personalizaste una habilidad, creaste un perfil de QA y configuraste un servidor MCP. Reutiliza estas personalizaciones y ajústalas cuando cambien las necesidades del equipo. Las instrucciones fijan estándares, las habilidades describen tareas repetibles, los agentes personalizados definen roles especializados y los servidores MCP conectan herramientas externas. Revisa los cambios y resultados reales, no solo el resumen del agente.

Adapta el **modo y el modelo** a la tarea. Usa **Plan** para pensar el enfoque, **Interactive** para mantener el control en cambios concretos y **Autopilot** para tareas bien delimitadas. Elige un modelo rápido para cambios rutinarios y otro más capaz para tareas complejas.

El contexto sigue siendo tan importante como la infraestructura. Describir claramente *qué* quieres construir, *por qué* y *cómo* cambia de forma significativa el resultado.

## Más cosas que explorar

Has cubierto el flujo principal. También puedes probar:

- `/review` para pedir al agente de revisión que analice cambios;
- `/rubber-duck` para hablar de un problema y obtener otra perspectiva;
- `/fleet` para coordinar subtareas independientes en paralelo;
- `/worktree` para aislar una tarea;
- `/delegate` para enviar una tarea a Copilot cloud agent.

## Próximos pasos

La mejor forma de mejorar con cualquier herramienta es seguir usándola: para código de producción, proyectos personales o esa pequeña aplicación que llevas años imaginando. Comparte lo que aprendas con tu equipo y aprende de sus experiencias. Y, como siempre, explora la documentación.

Si quieres ampliar Tailspin Toys desde el terminal, continúa con la serie opcional [Foundry Backer Concierge][foundry]. Para comparar otros entornos, explora el [taller de VS Code][vscode], el [taller de la aplicación GitHub Copilot][app] o el [taller de Copilot cloud agent][cloud].

## Recursos

- [Información sobre GitHub Copilot CLI][about-cli]
- [Referencia de comandos de Copilot CLI][cli-reference]
- [Personalizar Copilot CLI][customize-cli]
- [Administrar pull requests con Copilot CLI][manage-prs]

[previous-lesson]: ../9-cli-power-tools/
[foundry]: ../8-foundry-agent/
[vscode]: ../../vscode/
[app]: ../../app/
[cloud]: ../../cloud/
[about-cli]: https://docs.github.com/copilot/concepts/agents/about-copilot-cli
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[customize-cli]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot
[manage-prs]: https://docs.github.com/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests
