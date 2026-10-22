---
title: "Lección 8 - Crear y fusionar la PR de funcionalidad"
description: "Revisa conjuntamente el filtrado, las instrucciones, la actualización de la habilidad, el perfil de QA y las pruebas; después, crea una PR y usa Agent Merge."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

La implementación del filtrado, las actualizaciones de las instrucciones, la actualización de la habilidad, el perfil de garantía de calidad (QA) y las pruebas están guardados en una misma rama. Ha llegado el momento de revisarlos juntos y abrir una pull request. Tú fusionaste la pull request (PR) de las valoraciones por estrellas; esta vez permitirás que **Agent Merge** gestione el proceso.

> [!NOTE]
> Normalmente dividiríamos la funcionalidad, las actualizaciones de las instrucciones, la actualización de la habilidad y el agente de QA en varias PR. Para simplificar el taller, hemos mantenido todo el flujo de filtrado y calidad en una sola conversación y rama, y todo ese trabajo se incluirá en esta PR.

En esta lección:

- aprenderás qué es Agent Merge y cómo automatiza el ciclo de vida de la fusión;
- inspeccionarás el cambio completo de la funcionalidad y las evidencias de verificación;
- crearás la PR de filtrado;
- habilitarás Agent Merge solo después de la revisión y confirmarás que la PR se ha fusionado.

## Escenario

Durante el flujo de filtrado has usado Copilot para planificar, implementar y verificar una funcionalidad. Ahora Tailspin Toys quiere automatizar el trabajo restante de la PR, manteniendo el control de la autorización de fusión en manos del desarrollador.

## Presentación de Agent Merge

**Agent Merge** automatiza el trabajo restante necesario para incorporar una pull request. Cuando lo habilitas, Copilot resuelve los bloqueos de la PR: corrige las comprobaciones fallidas de integración continua (CI), responde a los comentarios de revisión y vuelve a basar la rama cuando es necesario. Después, habilita la fusión automática de GitHub cuando el repositorio lo permite.

Hasta ahora has seleccionado tú mismo **Merge pull request**. Agent Merge puede asumir esa responsabilidad. Revisa el trabajo y decide que está listo antes de habilitar Agent Merge.

## Usar Agent Merge para gestionar la PR

Con todo el código creado, revisémoslo juntos, creemos la PR y dejemos que Agent Merge gestione el resto del proceso.

1. Vuelve a tu Codespace.
2. Abre el diálogo del agente introduciendo `/agent`.
3. Selecciona **Default** en la lista de opciones y pulsa <kbd>Enter</kbd>.
4. Crea una PR nueva con el comando `/pr create`.
5. Activa Agent Merge con `/pr agentmerge`.
6. Copilot supervisará el proceso de integración continua de la PR. Cuando todo termine correctamente, realizará la fusión.
7. Confirma que ves un mensaje de Copilot parecido a «PR #14 was squash-merged successfully».

> [!IMPORTANT]
> Agent Merge no omite las aprobaciones obligatorias, la protección de ramas, las colas de fusión, la configuración del repositorio ni los permisos que falten. Si se bloquea, lee el motivo indicado y completa manualmente la fusión revisada cuando el repositorio lo permita.

## Resumen y siguientes pasos

Has automatizado varias partes del proceso de desarrollo, incluida la generación, las pruebas y la validación del código y, ahora, el proceso de pull request. En esta lección:

- aprendiste qué es Agent Merge y cómo automatiza el ciclo de vida de la fusión;
- inspeccionaste el cambio completo de la funcionalidad y las evidencias de verificación;
- creaste la PR de filtrado;
- habilitaste Agent Merge solo después de la revisión y confirmaste que la PR se había fusionado.

A continuación, [explorarás más comandos de barra útiles de Copilot CLI][next-lesson] para trabajar con el contexto, los modelos, el uso compartido y la delegación opcional en la nube.

## Recursos

- [Administrar pull requests con Copilot CLI][manage-prs]
- [Referencia de comandos de Copilot CLI][cli-reference]

[previous-lesson]: ../7-qa-agent/
[next-lesson]: ../9-cli-power-tools/
[manage-prs]: https://docs.github.com/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
