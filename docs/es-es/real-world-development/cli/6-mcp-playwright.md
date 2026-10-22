---
title: "Lección 6 - Validar la funcionalidad con Playwright MCP"
description: "Inspecciona o configura Playwright MCP en Copilot CLI y úsalo para explorar la funcionalidad de filtrado en un navegador."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

Como ya hemos destacado, escribir código no es lo único que importa. También hay que trabajar con datos, servicios externos y automatizaciones adicionales para Copilot. Aquí entran en juego los servidores MCP: permiten que Copilot vaya más allá de lo incluido en la CLI y le proporcionan más herramientas y servicios.

En esta lección:

- entenderás qué es Model Context Protocol (MCP) y cómo lo usa Copilot CLI;
- añadirás el servidor MCP de Playwright si todavía no está disponible;
- pedirás al agente que controle un navegador y explore la funcionalidad de filtrado.

## Escenario

Aunque las pruebas unitarias y de extremo a extremo son importantes, validar cambios en la interfaz requiere interactuar con ella. Permitirás que Copilot use el sitio como lo haría una persona para automatizar mejor la validación y obtener más confianza en los cambios.

## ¿Qué es Model Context Protocol (MCP)?

[Model Context Protocol (MCP)][mcp-blog-post] proporciona a los agentes de IA una forma de comunicarse con herramientas y servicios externos en tiempo real. Así pueden acceder a información actualizada y realizar acciones en tu nombre.

Estas herramientas y recursos se acceden a través de un servidor MCP, que actúa como puente entre el agente y los servicios externos. Cada servidor MCP representa un conjunto distinto de herramientas y recursos.

Algunos servidores MCP populares son:

- **[GitHub MCP Server][github-mcp]**: proporciona acceso a API para administrar repositorios, incidencias y pull requests de GitHub.
- **[Playwright MCP Server][playwright-mcp-server]**: proporciona capacidades de automatización del navegador mediante Playwright.

GitHub mantiene un [registro de MCP][mcp-registry] para facilitar el descubrimiento y las contribuciones.

> [!CAUTION]
> Trata los servidores MCP como cualquier otra dependencia del proyecto. Antes de usar uno, revisa su código fuente, verifica el publicador y valora las implicaciones de seguridad.

## Añadir el servidor MCP de Playwright

Si el servidor no está disponible, añádelo para que Copilot pueda interactuar con el sitio.

> [!NOTE]
> Si Playwright MCP ya está configurado en Copilot CLI, omite estos pasos y continúa con la sección siguiente.

1. Vuelve a tu Codespace.
2. Abre el diálogo para añadir un servidor MCP con este comando:

   ```text
   /mcp add
   ```

3. Introduce `playwright` como nombre y pulsa <kbd>Tab</kbd>.
4. Confirma el tipo **STDIO** con <kbd>Enter</kbd> y pulsa <kbd>Tab</kbd>.
5. Pega lo siguiente en el diálogo **Command**:

   ```text
   npx -y @playwright/mcp@latest --headless --no-sandbox
   ```

6. Pulsa <kbd>Control</kbd>+<kbd>S</kbd> (Mac) o <kbd>Ctrl</kbd>+<kbd>S</kbd> (Windows/Linux) para guardar.
7. Pulsa <kbd>Esc</kbd> para salir del diálogo.

## Pedir a Copilot que explore la funcionalidad con Playwright

1. Usa este prompt para pedir a Copilot que valide la funcionalidad:

   ```text
   Start the app and use Playwright MCP to check filtering against the issue and our plan. Tell me what works and what doesn't, without making changes. Stop the server you started when you're done.
   ```

> [!NOTE]
> Normalmente Copilot detectará por sí solo el servidor MCP que debe usar, pero indicarlo puede producir resultados más coherentes y ahorrar tokens.

2. Observa los pasos que Copilot realiza en el navegador.
3. Lee el informe y confirma que todo funciona como esperas.

Copilot iniciará el servidor, usará Playwright, detendrá el servidor y te entregará un informe.

## Resumen y siguientes pasos

Has usado el servidor MCP de Playwright para explorar la funcionalidad en un navegador real desde Copilot CLI. En resumen:

- aprendiste qué es Model Context Protocol (MCP) y cómo lo usa Copilot CLI;
- añadiste el servidor MCP de Playwright si no estaba disponible;
- pediste al agente que controlara un navegador y explorara la funcionalidad.

A continuación, [crearás un agente personalizado de QA][next-lesson] que reunirá la habilidad y las herramientas del navegador.

## Recursos

- [¿Qué demonios es MCP y por qué todo el mundo habla de ello?][mcp-blog-post]
- [Servidor MCP de Playwright de Microsoft][playwright-mcp-server]
- [Añadir servidores MCP a Copilot CLI][add-mcp]

[previous-lesson]: ../5-agent-skills/
[next-lesson]: ../7-qa-agent/
[mcp-blog-post]: https://github.blog/ai-and-ml/llms/what-the-heck-is-mcp-and-why-is-everyone-talking-about-it/
[playwright-mcp-server]: https://github.com/microsoft/playwright-mcp
[github-mcp]: https://github.com/github/github-mcp-server
[mcp-registry]: https://github.com/mcp
[add-mcp]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/add-mcp-servers
