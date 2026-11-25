# Obra a la vista

**Español** · [English](README.md)

**Obra a la vista te enseña en qué se gasta el dinero público en obra, quién se lo lleva y qué obras acaban costando más de lo que se adjudicó.**

Cada año las administraciones españolas adjudican miles de obras: colegios, carreteras, hospitales, aceras. Los datos son públicos, pero están repartidos en plataformas distintas, en formatos pensados para máquinas y sin nadie que los junte. Obra a la vista los reúne en una sola web, los explica en lenguaje claro y señala dónde merece la pena mirar.

**[Abrir Obra a la vista →](https://obra-a-la-vista.obraalavista.workers.dev)**

> Toda la información sale de fuentes oficiales y cada obra enlaza a su anuncio original. Los indicadores señalan dónde mirar; no son acusaciones.

---

## Qué encuentras

| Sección | Qué te enseña |
| --- | --- |
| **Desvíos** | Las obras que subieron de precio después de adjudicarse, cuánto subieron y en qué tipo de obra pasa más |
| **Cruces** | Quién contrata con quién: busca una empresa o una administración y ves sus relaciones, cuántos contratos hay entre ellas y si alguno subió de precio |
| **Mi zona** | La obra de tu municipio, contrate quien contrate; en la Comunidad de Madrid, también el pleno municipal y el presupuesto del ayuntamiento |
| **Comparar** | Comunidades y municipios del mismo tamaño puestos al lado, solo con indicadores que significan lo mismo en todas partes y con su margen de error |
| **Patrones** | Listas calculadas con reglas fijas e iguales para todos: empresas que se llevan casi todo lo de un órgano, obras con un único licitador, contratos menores justo por debajo del límite legal |
| **Calidad del dato** | Qué falta o no cuadra en lo que publica cada administración, y qué órganos publican sus obras más completas |

Cada obra tiene su ficha: presupuesto, adjudicación, empresa, número de ofertas, plazo de ejecución previsto, modificaciones y el enlace al anuncio oficial.

## Cómo funciona

1. **Reúne.** Descarga los anuncios de obra de la Plataforma de Contratación del Sector Público, que recoge también lo que publican las plataformas autonómicas.
2. **Ordena.** Junta las versiones de cada expediente, separa las prórrogas de las modificaciones de precio y ubica cada obra en su municipio.
3. **Cruza.** Añade el padrón del INE para comparar municipios de su tamaño y, en la Comunidad de Madrid, los plenos, las alcaldías y los presupuestos municipales.
4. **Explica.** Convierte todo en cifras que se entienden de un vistazo: medianas en lugar de medias, márgenes de error y un aviso cada vez que un dato no permite concluir algo.

## En cifras

- **Toda España:** las 17 comunidades autónomas, más Ceuta y Melilla.
- **171.000 expedientes de obra**, de enero de 2023 a noviembre de 2026.
- **132.000 obras adjudicadas**, más de **13.000 órganos de contratación** y **39.000 empresas**.
- **10.400 obras con modificaciones** publicadas después de adjudicarse.

## Por qué te puedes fiar

- **Comprobado contra la fuente.** De 180 obras elegidas al azar, 10 por comunidad, se cotejaron 175 con su página oficial: el presupuesto coincidía en todas.
- **Lo que no se sabe, se dice.** La fuente no publica cuándo termina una obra ni su coste final, así que la web nunca los presenta como si los tuviera.
- **Comparaciones justas.** No se compara una comunidad con otra cuando sus datos llegan por vías distintas, ni un municipio con otro de diferente tamaño.
- **Sin datos personales.** No se muestran nombres de personas y las opiniones se guardan sin IP, sin nombre y sin correo.

## Cómo está hecho

| Capa | Tecnología |
| --- | --- |
| Ingesta y limpieza | Python: lectura de los ficheros ATOM y CODICE de la plataforma estatal, con GitHub Actions programadas |
| Web | HTML, CSS y JavaScript sin frameworks, con gráficos SVG propios, carga por años y versión móvil |
| Publicación | **Cloudflare Workers**: los ficheros se sirven desde la red de Cloudflare y un Worker en Python con FastAPI recibe las opiniones |
| Base de datos | Postgres en Neon a través de Cloudflare Hyperdrive, con un usuario que solo puede insertar |
| Protección contra bots | **Cloudflare Turnstile** en el formulario de opiniones, más un campo trampa y un límite de envíos por IP |

---

<sub>Proyecto ciudadano e independiente de Yael Parra. Los datos pertenecen a las administraciones que los publican; Obra a la vista solo los reúne y los explica.</sub>
