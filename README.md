# ManuscritIA

Editor LaTeX con IA para escribir artículos científicos, en tu navegador. Es una aplicación web de un solo fichero, pensada como alternativa a **Prism** (OpenAI), que cierra el 1 de enero de 2027 y borrará los proyectos.

**Usar la app:** https://fborrasumh.github.io/manuscritia/

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23845323.svg)](https://doi.org/10.5281/zenodo.23845323)

**Idiomas:** español (por defecto), inglés y portugués. El selector está en la barra superior; también vale añadir `?lang=en` o `?lang=pt` a la URL.

## Qué hace

- **Proyectos LaTeX en el navegador.** Puedes crear varios proyectos, importar el ZIP que exportan Prism u Overleaf (también sin la carpeta raíz y sin `__MACOSX`) o subir ficheros sueltos (.tex, .bib, .cls, .sty e imágenes). Detecta el fichero principal y resuelve `\input` e `\include`.
- **Editor con vista previa sin red.** El código va a un lado y el documento al otro, con secciones numeradas, título, resumen, ecuaciones (MathML con Temml, incluido en la app), figuras con las imágenes del proyecto, tablas (también con booktabs), listas, teoremas, notas al pie, citas numeradas y bibliografía a partir del .bib, y `\ref`/`\eqref`. Al pulsar un párrafo de la vista previa se salta a su línea en el código.
- **Lista de problemas calculada por código, sin compilar.** Detecta llaves y entornos sin cerrar, ecuaciones que no se pueden dibujar, citas sin entrada en el .bib, `\ref` a etiquetas inexistentes, etiquetas repetidas, ficheros e imágenes que faltan, y entradas del .bib que no se citan.
- **Asistente** con el contexto del fichero abierto o del proyecto completo, más la selección. Si pides cambios, llegan como propuestas «buscar → reemplazar».
- **Arreglar con IA** cualquier problema de la lista. Después de aplicar el arreglo, el código comprueba si el problema ha desaparecido.
- **Revisión con IA** de un fichero, por partes: ortografía y gramática, claridad, coherencia y terminología, o tono académico.
- **Referencias.** Busca en Crossref, añade trabajos por DOI o por identificador de arXiv (vía DataCite) y comprueba los DOI de tu .bib. El **BibTeX lo escribe el código** a partir de los metadatos oficiales. La IA puede señalar qué afirmaciones de un párrafo necesitan cita y qué buscar.
- **Imagen a código:** convierte una foto de una ecuación, una tabla, un diagrama (TikZ) o un texto en LaTeX.
- **Dictado:** graba o sube un audio, lo transcribe (con OpenAI o Gemini) y, si quieres, lo pasa a LaTeX.
- **Comentarios** anclados al texto, y **versiones**: se guarda una antes de aplicar cambios de la IA, al importar y a mano; se conservan las 30 últimas y se pueden restaurar.
- **Exportar:** el proyecto en ZIP (listo para Overleaf o tu LaTeX local, con comentarios y versiones en `.manuscritia/` si lo eliges), el fichero principal y un PDF impreso desde la vista previa.

## La IA propone, el código comprueba

- Cada cambio que propone la IA (en el asistente, la revisión o los arreglos) se aplica solo si el texto que dice cambiar **existe tal cual** en tu fichero (se toleran diferencias de espacios) y aparece una sola vez. Si no, se marca como no aplicable.
- Se avisa si un cambio **quita o añade citas, referencias, etiquetas, entornos o ecuaciones**, si **añade cifras** que no estaban en el proyecto o si deja llaves sin cerrar. El botón «Aceptar todas» solo aplica los cambios verificados y sin avisos.
- Los DOI se comprueban en Crossref y en DataCite. Un DOI que no existe, o cuyo título no coincide con el de tu entrada, se marca.
- El LaTeX que sale de una imagen se comprueba: que las llaves y los entornos estén equilibrados, que la ecuación se pueda dibujar, que todas las filas de la tabla tengan las mismas columnas, y que los paquetes que necesita estén en el preámbulo.
- En el dictado se avisa de las cifras que aparecen en el LaTeX y no estaban en la transcripción.

## Cómo se usa la IA

Funciona con la clave de cada persona de OpenAI, Google Gemini o Anthropic Claude. La clave se guarda solo en el navegador y no hace falta servidor. El dictado necesita una clave de OpenAI o de Gemini, porque Claude no transcribe audio.

## Privacidad

- **En tu ordenador:** los proyectos, comentarios y versiones (en IndexedDB de este navegador), la clave de IA, la vista previa, la lista de problemas y las exportaciones. Si borras los datos del navegador, se borran los proyectos, así que exporta el ZIP a menudo.
- **Sale hacia tu proveedor de IA:** solo el texto que eliges en cada acción, con correos, teléfonos y DNI/NIE enmascarados. Antes del primer envío de la sesión ves una muestra y confirmas. Las imágenes y el audio no se pueden enmascarar, y la app lo avisa cada vez.
- **Sale hacia Crossref y DataCite:** las búsquedas y los DOI que compruebas, no tu texto.
- La política de seguridad de la página (CSP) bloquea cualquier otro destino.

## Límites

- **La vista previa no es una compilación.** No ejecuta TeX: no dibuja TikZ ni pgfplots, no muestra imágenes PDF/EPS, no expande macros con argumentos fuera de las ecuaciones y no reproduce la paginación ni el estilo bibliográfico exacto (las citas salen numeradas por orden de aparición). Para el PDF definitivo, exporta el ZIP y compílalo en Overleaf o en local.
- **No compila a PDF con TeX real** en esta versión. Se estudió un motor TeX en WebAssembly (BusyTeX, TeX Live 2026): necesita descargar unos 120 MB, tiene que alojarse en el mismo dominio y su licencia es AGPL. Queda para una versión posterior.
- La lista de problemas **no detecta todo** lo que detectaría LaTeX (por ejemplo, paquetes que faltan u opciones incorrectas).
- **No hay colaboración en tiempo real** ni sincronización con Zotero. Para trabajar con otras personas, comparte el ZIP.
- La IA puede equivocarse aunque el texto que cambia exista. Lee cada propuesta y **lee siempre los trabajos antes de citarlos**: que un DOI exista no significa que respalde tu afirmación.
- La exportación desde Prism se hace en Prism. La app importa el ZIP resultante, pero no se ha probado con un ZIP real exportado de Prism, sino con ZIP de estructura equivalente.

## Autoría

Fernando Borrás Rocher (Universidad Miguel Hernández de Elche).

ORCID: Fernando Borrás Rocher [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573)

## Cómo citar

Borrás Rocher, F. (2026). *ManuscritIA* (v1.0.0) [Software]. DOI: [10.5281/zenodo.23845323](https://doi.org/10.5281/zenodo.23845323)

## Licencia

MIT. Véase [LICENSE](LICENSE). Incluye Temml 0.14.0 (© 2020 Ron Kok, MIT) para dibujar las ecuaciones.
