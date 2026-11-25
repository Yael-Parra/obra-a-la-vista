<p align="right"><a href="README.md">English</a> · <b>Español</b></p>

<h1 align="center">Obra a la vista</h1>

<p align="center"><b>En qué se gasta el dinero público en obra en España, quién se lo lleva y qué obras acaban costando más de lo que se adjudicó.</b></p>

<p align="center">
  <img src="https://img.shields.io/badge/España-17%20comunidades%20%2B%20Ceuta%20y%20Melilla-3E1D26?style=flat-square"/>
  <img src="https://img.shields.io/badge/171.000-expedientes-BE5A3C?style=flat-square"/>
  <img src="https://img.shields.io/badge/datos-2023%20a%202026-A04A5A?style=flat-square"/>
  <img src="https://img.shields.io/badge/publicado%20en-Cloudflare%20Workers-8A7B6C?style=flat-square"/>
</p>

<p align="center">
  <a href="https://obra-a-la-vista.obraalavista.workers.dev"><b>Abrir Obra a la vista →</b></a>
</p>

---

## El problema

Cada año las administraciones españolas adjudican miles de obras: colegios, carreteras, hospitales, aceras. Los datos son públicos, pero están repartidos en plataformas distintas, publicados en formatos pensados para máquinas, y nadie los junta. En la práctica, casi nadie puede responder preguntas sencillas como «¿qué obras de mi pueblo subieron de precio?» o «¿a qué empresas contrata siempre este ayuntamiento?».

**Obra a la vista reúne esos datos en una sola web, los explica en lenguaje claro y señala dónde merece la pena mirar**, siempre con el enlace al anuncio oficial.

> Toda la información sale de fuentes oficiales. Los indicadores señalan dónde mirar; no son acusaciones.

## Cómo funciona

1. **Reúne.** Descarga los anuncios de obra de la Plataforma de Contratación del Sector Público, que recoge también lo que publican las plataformas autonómicas.
2. **Ordena.** Junta las versiones de cada expediente, separa las prórrogas de las modificaciones de precio y ubica cada obra en su municipio.
3. **Cruza.** Añade el padrón del INE para comparar municipios de su tamaño y, en la Comunidad de Madrid, los plenos, las alcaldías y los presupuestos municipales.
4. **Explica.** Convierte todo en cifras que se entienden de un vistazo, con un aviso cada vez que un dato no permite concluir algo.

## Las ideas detrás

Unos pocos principios dan forma a cada pantalla:

- **Primero lo importante.** La portada abre con las obras que subieron de precio y con quién contrata con quién. Todo lo demás está un nivel más abajo, para quien quiera profundizar.
- **Medianas, no medias.** Un desvío enorme no debe deformar la imagen, así que la cifra de referencia es siempre la mediana, y las comparaciones llevan su margen de error.
- **Solo comparaciones justas.** No se ordenan comunidades cuando sus datos llegan a la plataforma estatal por vías distintas, y un municipio solo se compara con otros de su tamaño.
- **Decir lo que no se sabe.** La fuente no publica cuándo termina una obra ni cuánto costó al final, así que la web nunca los presenta como si los tuviera.
- **Comprobado contra la fuente.** De 180 obras elegidas al azar, 10 por comunidad, se cotejaron 175 a mano con su página oficial, y el presupuesto coincidía en todas.
- **Sin datos personales.** No se muestran nombres de personas, y las opiniones se guardan sin IP, sin nombre y sin correo.

## Qué hay dentro

| Sección | Qué te enseña |
| --- | --- |
| **Desvíos** | Las obras que subieron de precio después de adjudicarse, cuánto subieron y en qué tipo de obra pasa más |
| **Cruces** | Busca una empresa o una administración y ves sus relaciones, cuántos contratos hay entre ellas y si alguno subió de precio |
| **Mi zona** | La obra de tu municipio, contrate quien contrate |
| **Comparar** | Comunidades y municipios del mismo tamaño puestos al lado, solo con indicadores que significan lo mismo en todas partes |
| **Patrones** | Listas calculadas con reglas fijas e iguales para todos: empresas que se llevan casi todo lo de un órgano, obras con un único licitador, contratos menores justo por debajo del límite legal |
| **Calidad del dato** | Qué falta o no cuadra en lo que publica cada administración, y qué órganos publican sus obras más completas |

Cada obra tiene su ficha: presupuesto, adjudicación, empresa, número de ofertas, plazo de ejecución previsto, modificaciones y el enlace al anuncio oficial.

**En cifras:** 171.000 expedientes de obra de enero de 2023 a noviembre de 2026, 132.000 obras adjudicadas, más de 13.000 órganos de contratación, 39.000 empresas y 10.400 obras modificadas después de adjudicarse.

## Cómo está hecho

| Capa | Tecnología |
| --- | --- |
| Ingesta y limpieza | Python: lectura de los ficheros ATOM y CODICE de la plataforma estatal, con GitHub Actions programadas |
| Web | HTML, CSS y JavaScript sin frameworks, con gráficos SVG propios, carga por años y versión móvil |
| Publicación | **Cloudflare Workers**: los ficheros se sirven desde la red de Cloudflare y un Worker en Python con FastAPI recibe las opiniones |
| Base de datos | Postgres en Neon a través de Cloudflare Hyperdrive, con un usuario que solo puede insertar |
| Protección contra bots | **Cloudflare Turnstile** en el formulario de opiniones, más un campo trampa y un límite de envíos por IP |

## Estado

En marcha y con toda España. Los datos se actualizan desde las fuentes oficiales, y la página de metodología de la web explica cada regla y cada limitación conocida.

---

## Sobre mí

<p align="center">
  <a href="https://www.linkedin.com/in/yael-parra/">
    <img src="https://img.shields.io/badge/Yael%20Parra-3E1D26?style=for-the-badge"/>
    &nbsp;
    <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/>
  </a>
</p>

Soy consultora de IA y construyo producto. Trabajo en los dos lados: ayudo a las empresas a adoptar la IA y construyo las herramientas.

Obra a la vista es un proyecto ciudadano e independiente. Lo diseñé de principio a fin: el flujo de datos, las reglas de cada indicador, la experiencia y el despliegue.

Si trabajas en algo que cruce datos, IA e interés público y quieres hablar, me encuentras en [linkedin.com/in/yael-parra](https://www.linkedin.com/in/yael-parra/).

<sub>Los datos pertenecen a las administraciones que los publican; Obra a la vista solo los reúne y los explica.</sub>
