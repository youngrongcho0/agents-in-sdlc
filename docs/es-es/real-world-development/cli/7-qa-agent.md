---
title: "Lección 7 - Crear y usar un agente de QA"
description: "Crea un agente personalizado de QA que combine los requisitos de la incidencia, la habilidad quality-checks y Playwright MCP."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

Has usado la habilidad `quality-checks` para ejecutar comprobaciones automatizadas y Playwright MCP para observar la experiencia de filtrado en un navegador. Ahora reunirás esas capacidades en un agente personalizado con un proceso de QA bien definido.

En esta lección:

- explorarás cómo trabaja un agente personalizado con instrucciones, habilidades y herramientas MCP;
- crearás e inspeccionarás un perfil reutilizable de garantía de calidad;
- seleccionarás el agente de QA y revisarás sus hallazgos frente a la incidencia.

## Escenario

Tailspin Toys quiere revisar de forma coherente los requisitos, la calidad del código, las comprobaciones automatizadas, la cobertura y el comportamiento en el navegador antes de abrir una pull request (PR). Un agente personalizado puede coordinar ese proceso y generar un informe reutilizable.

## ¿Qué es un agente personalizado?

Un agente personalizado es una versión especializada de Copilot definida en un perfil Markdown. El perfil describe su propósito, instrucciones y herramientas disponibles. En este taller definirás un rol de QA en `.github/agents/qa.agent.md` y lo seleccionarás en Copilot CLI.

Cada personalización tiene una función distinta. Las instrucciones del repositorio describen los estándares del equipo. La habilidad `quality-checks` empaqueta comprobaciones repetibles. Playwright MCP proporciona herramientas del navegador. El perfil de QA indica a Copilot cómo combinar esas capacidades para evaluar los requisitos e informar de los resultados.

## Crear el perfil de QA

1. Vuelve a tu Codespace y confirma que la conversación de filtrado está en modo Interactive.
2. Pide al agente predeterminado que cree el agente personalizado:

   ```text
   Create a custom agent named QA in .github/agents/qa.agent.md. It should check features against their issues and agreed requirements, follow the repository instructions, run the quality-checks skill, use Playwright MCP to verify behavior, and add tests when coverage is missing.

   Have it report each requirement as pass, fail, or blocked with supporting evidence. It must ask before changing implementation code, and it must not commit changes or open pull requests.

   Just create the profile for now so I can review it.
   ```

## Inspeccionar el perfil

1. Introduce `/diff` y abre `.github/agents/qa.agent.md`.
2. Lee el frontmatter. `description` es obligatorio; `name` es opcional, pero proporciona un nombre claro.
3. Confirma que el perfil parte de los requisitos, sigue las instrucciones, ejecuta `quality-checks` y usa Playwright MCP.
4. Confirma que informa con evidencias, pide permiso antes de cambiar código y no crea commits ni pull requests.
5. Si falta alguna responsabilidad o límite, pide al agente predeterminado que revise el perfil.

## Ejecutar QA contra la incidencia

1. Activa el agente:

   ```text
   /agent QA
   ```

> [!NOTE]
> Como acabas de crear el agente, puede que todavía no aparezca en la lista. El comando lo activará igualmente.

2. Pide al agente que revise la funcionalidad:

   ```text
   Review the filtering feature against the issue and the decisions in our plan. Is it ready for a PR?
   ```

3. Lee el informe cuando termine.

## Resumen y siguientes pasos

Has añadido un rol especializado reutilizable y revisado su trabajo. En esta lección:

- exploraste cómo trabaja un agente personalizado con instrucciones, habilidades y herramientas MCP;
- creaste e inspeccionaste un perfil reutilizable de garantía de calidad;
- seleccionaste el agente de QA y revisaste sus hallazgos frente a la incidencia.

Ya tienes la implementación, la actualización de la habilidad, el perfil de QA, las pruebas y el informe de verificación listos para revisar. A continuación, [reunirás todo en una PR de funcionalidad y usarás Agent Merge][next-lesson].

## Recursos

- [Crear agentes personalizados para Copilot CLI][create-agents]
- [Configuración de agentes personalizados][agent-config]

[previous-lesson]: ../6-mcp-playwright/
[next-lesson]: ../8-create-pull-request/
[create-agents]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/create-custom-agents-for-cli
[agent-config]: https://docs.github.com/copilot/reference/custom-agents-configuration
