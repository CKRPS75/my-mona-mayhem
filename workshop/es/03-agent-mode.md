<!-- l10n-sync: source-file="workshop/03-agent-mode.md" -->
# Parte 3: Construye el juego con flujos de trabajo agénticos

---

En esta parte, Copilot pasa de planificar a implementar. En lugar de escribir código línea a línea, describes lo que quieres y Copilot realiza el trabajo en todos los archivos que tenga que modificar.

## Tarea 1: Conecta la batalla

<!-- track:vscode:start -->
1. Cambia a modo **Agent** en Copilot Chat.
2. Introduce este prompt:
<!-- track:vscode:end -->

<!-- track:cli:start -->
1. Devuelve Copilot CLI a su flujo de programación habitual (o mantente en autopilot si quieres que siga avanzando hasta que lo detengas).
2. Si te resulta útil, menciona el archivo de la página para proporcionar contexto adicional: `@src/pages/index.astro`.
3. Introduce este prompt:
<!-- track:cli:end -->

   > Add client-side JavaScript to the battle page that:
   > 1. When the Battle button is clicked, gets both usernames from the inputs
   > 2. Validates both are filled (show error if not)
   > 3. Fetches both users' contribution data in parallel from our API
   > 4. Renders contribution graphs as colored grids — each day is a colored square using GitHub's color palette
   > 5. Shows a VS badge between the two users
   > 6. Displays username, total contributions, and date range for each user
   > 7. Handles loading states and errors
   > 8. Also triggers on Enter key in input fields.
   > 9. Simple UI for now that is already scaffolded.
   >
   > Use TypeScript interfaces for the contribution data structure.

<!-- track:vscode:start -->
3. Deja que Agent Mode implemente el cambio en `index.astro`.
4. Revisa los cambios propuestos en la vista de diferencias antes de aceptarlos.
<!-- track:vscode:end -->

<!-- track:cli:start -->
4. Deja que Copilot CLI implemente el cambio en `src/pages/index.astro`.
5. Usa `/diff` para inspeccionar los cambios generados y apruébalos.
<!-- track:cli:end -->

## Tarea 2: Prueba la batalla

> **⚠️ ¿No ves cambios?** Si la página de batalla no se ha actualizado, detén el servidor (`Ctrl+C`), reinícialo con `npm run dev` y actualiza el navegador.

1. Introduce `octocat` y `torvalds` como nombres de usuario y haz clic en **Battle**.
2. Deberías ver los dos gráficos de contribuciones uno junto al otro, con cuadrículas de colores.
3. Prueba los casos de error:
   - Deja uno o ambos campos vacíos y haz clic en Battle: debería aparecer un error de validación.
   - Introduce un nombre de usuario no válido: la aplicación debería mostrar un error de la API.
4. Pulsa **Enter** en cualquiera de los campos: debería iniciar la batalla igual que al hacer clic.

## Tarea 3: Itera con Copilot

Si algo no funciona como esperabas, proporciona comentarios de seguimiento directamente a Copilot. Por ejemplo:

- *«Los cuadrados de contribuciones son demasiado grandes; hazlos de 12x12 px»*
- *«Añade una descripción emergente al pasar el cursor que muestre la fecha y el número de contribuciones»*
- *«El estado de carga necesita una animación de pulso»*

<!-- track:vscode:start -->
Agent Mode gestiona de forma natural los cambios en varios archivos y las iteraciones. Cada prompt de seguimiento se basa en la conversación anterior, así que puedes perfeccionar la implementación progresivamente sin empezar de cero.
<!-- track:vscode:end -->

<!-- track:cli:start -->
Las sesiones de Copilot CLI conservan su historial, por lo que cada prompt de seguimiento se apoya en el anterior. Usa `/session` o `/context` para consultar lo que Copilot mantiene en el contexto y ejecuta `/review` después de una iteración importante si quieres una revisión adicional de errores o pulido.
<!-- track:cli:end -->

## Consejos para esta parte

- **Sé específico sobre lo que quieres**: los requisitos claros producen mejores resultados.
- **Divide las tareas grandes en prompts más pequeños** si Copilot se desvía.
- **Revisa los cambios antes de aceptarlos**: inspeccionar código generado es más rápido que reescribirlo después.
- **Prueba la aplicación inmediatamente después de cada implementación** para que los problemas sigan localizados.

## ✅ Parte 3 completada

Has aprendido a:

- Usar Copilot para **implementar funcionalidades en varios archivos**.
- **Iterar sobre los resultados** con prompts de seguimiento concretos.
- Gestionar el **ciclo completo de una funcionalidad**: implementación, revisión, pruebas y perfeccionamiento.
