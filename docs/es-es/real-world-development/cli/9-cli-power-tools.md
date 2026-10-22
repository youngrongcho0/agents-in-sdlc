---
title: "Lección 9 - Comandos de barra en GitHub Copilot CLI"
description: "Explora comandos de barra para administrar el contexto, seleccionar modelos, compartir sesiones y delegar trabajo opcionalmente."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

Como cualquier buena herramienta de CLI, GitHub Copilot CLI incluye muchos comandos de barra para interactuar con ella. Estos comandos exponen funciones avanzadas, información interna y opciones de configuración. Ya has usado `/diff`, `/mcp`, `/skills`, `/agent` y `/pr`. Exploremos otros comandos útiles.

En esta lección:

- usarás `/context` y `/compact` para explorar cómo administra Copilot el contexto;
- usarás `/model` para explorar los modelos disponibles;
- aprenderás cómo `/share` puede exportar o compartir una sesión;
- explorarás comandos opcionales para trabajo paralelo, worktrees y delegación al cloud agent.

## Escenario

Has completado el flujo principal de la CLI. Ahora revisarás algunas capacidades adicionales: administrar el contexto, cambiar de modelo, compartir sesiones y delegar opcionalmente en [Copilot cloud agent][about-cloud-agent].

## Explorar el contexto de Copilot CLI

En tareas grandes puedes alcanzar el máximo de la ventana de contexto. Copilot CLI compacta la conversación automáticamente cuando es necesario, y también puedes inspeccionarla o compactarla con comandos de barra.

1. Vuelve a tu Codespace e inicia Copilot CLI desde la raíz del repositorio si aún no está abierto.
2. Introduce:

   ```text
   /context
   ```

3. Observa el modelo, el uso actual de tokens y la división entre instrucciones del sistema, herramientas, mensajes y espacio libre.
4. Compacta la conversación:

   ```text
   /compact
   ```

5. Introduce `/context` de nuevo y compara el resultado.

> [!NOTE]
> Copilot CLI compacta el contexto automáticamente cuando la ventana se llena. Usa `/compact` para elegir el momento. Usa `/clear` o `/new` al cambiar a una tarea no relacionada y querer una conversación nueva.

## Elegir el modelo

1. Introduce:

   ```text
   /model
   ```

2. Explora los modelos disponibles y la información de uso.
3. Mantén el modelo actual, selecciona otro o pulsa <kbd>Esc</kbd> para cerrar la lista.

## Compartir una sesión

El trabajo en equipo y el intercambio de aprendizajes ayudan a mejorar el uso de las herramientas de IA. El comando `/share` puede exportar una sesión a un archivo Markdown o HTML, crear un enlace compartible o publicar un GitHub gist.

1. Introduce `/help` y revisa las opciones de `/share` de tu versión.
2. Si quieres compartir la sesión, elige el destino adecuado, como `/share file` para exportarla a Markdown.
3. Revisa el contenido exportado antes de enviarlo o publicarlo. Las exportaciones pueden incluir prompts, respuestas y detalles del proyecto.

Publicar un enlace o gist es opcional. No publiques contenido del repositorio o de la conversación que el equipo no quiera compartir.

## Opcional: escalar o delegar

El taller principal ha terminado. Copilot CLI también ofrece comandos para tareas más grandes:

- `/fleet` puede dividir subtareas independientes entre subagentes y ejecutarlas en paralelo.
- `/worktree` puede crear un worktree aislado para otra tarea.
- `/delegate` puede enviar una tarea a Copilot cloud agent, que trabaja de forma asíncrona y puede abrir una pull request.

Estos comandos son opcionales porque pueden crear worktrees adicionales o trabajo remoto. Inicia una tarea nueva y bien delimitada antes de probarlos y revisa el resultado mediante el flujo habitual. Si quieres profundizar en el trabajo asíncrono, continúa con el [taller de cloud agent][cloud-workshop].

## Resumen y siguientes pasos

Los comandos de barra permiten configurar Copilot CLI, compartir sesiones y ver qué ocurre internamente. En esta lección:

- usaste `/context` y `/compact` para explorar la administración del contexto;
- usaste `/model` para explorar los modelos;
- aprendiste que `/share` puede exportar o compartir una sesión;
- exploraste comandos opcionales para trabajo paralelo, worktrees y delegación.

Hay más comandos de barra disponibles. Ahora [revisarás lo aprendido][next-lesson] y algunos pasos siguientes.

## Recursos

- [Referencia de comandos de Copilot CLI][cli-reference]
- [Administración del contexto en Copilot CLI][context-management]
- [Información sobre Copilot cloud agent][about-cloud-agent]

[previous-lesson]: ../8-create-pull-request/
[next-lesson]: ../10-review/
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[context-management]: https://docs.github.com/copilot/concepts/agents/copilot-cli/context-management
[about-cloud-agent]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[cloud-workshop]: ../../cloud/
