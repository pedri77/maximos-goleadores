# ¿Cuántos goles metió Pelé? — Informe de datos (auditoría de las cuentas)

Generado el 02-10-2026 a partir de `data/fuentes.json` y `data/goleadores.json` (episodio cci-17).
Todas las cifras salen de las fuentes citadas, con URL; ninguna está estimada.

## 1. La tesis, en una línea

**El ranking de máximos goleadores de la historia no existe.** No hay una lista oficial, y las que se
publican difieren en cientos de goles según qué partidos decidan contar. Este episodio no publica un
ranking nuevo: publica **la reconciliación de las reglas**, jugador a jugador.

## 2. El mismo jugador, nueve cifras

Pelé, según quién cuente (todas publicadas, todas con URL en `data/goleadores.json`):

| Cifra | Quién la publica | Qué cuenta |
|---|---|---|
| **747** | documentación del Santos | solo lo oficial: 643 Santos + 67 selección + 37 Cosmos |
| **757** | prensa, como «oficial» | 643 + 77 de selección + 37 (otra definición de partido oficial) |
| **762** | tabla de goles «reconocidos oficialmente» | desglose 604 club + 49 + 26 + 83 selección |
| **778** | **RSSSF** | además selecciones B/Olímpica/juvenil, regionales y de **ciudad**, pretemporada y partidos anulados |
| **1.091** | el propio Santos | todos sus goles con el club: 643 oficiales + **448 en amistosos** |
| **1.279** | The New York Times | 1.279 en 1.363 partidos, «incluye partidos de exhibición» |
| **1.281** | **FIFA** (recogida por ESPN) | 1.281 en 1.363 partidos, incluyendo no oficiales |
| **1.282** | documento del estado de São Paulo | 1.282 en 1.367 partidos |
| **1.283** | **Guinness World Records** | su récord «incluyendo amistosos» |

**Rango: de 747 a 1.283.** La diferencia no es un error de nadie: son 536 goles de diferencia y la
explicación entera está en una palabra, *amistoso*. En la época de Pelé los partidos de exhibición con
el Santos eran acontecimientos masivos, y decidir si cuentan es exactamente decidir el récord.

Con Bican pasa igual: **722** (reconocidos), **805** (estimación al superarle Ronaldo), **821** (lo que
sostiene la federación checa), **950+** (RSSSF, que avisa de que incluye reservas y partidos
internacionales no oficiales).

## 3. Lo que hace la máquina, y por qué sale mal

Sumar los goles de Wikidata sin mirar (`P54`, goles por etapa) da:

| Jugador | Suma ingenua de Wikidata | Cifra publicada |
|---|---:|---:|
| Pelé | **3.656** | 757-1.283 |
| Messi | 1.738 | ~850 |
| Cristiano Ronaldo | 1.012 | ~994 |
| Maradona | 471 | 345 oficiales |

No es un error de la consulta: las fichas mezclan etapas duplicadas, solapadas y totales de temporada
dentro del campo de goles. Es el ejemplo perfecto de por qué el episodio no es un ranking: **la primera
regla de una auditoría es no sumar cosas que miden distinto.**

## 4. Los criterios, citados

- **RSSSF** (`rsssf.org/players/prolific.html`, actualizado 19-07-2026) dice literalmente que incluye
  «all leagues (incl. regional-, reserve-, amateur-)», «all selections: A, B, Ol, U, league, armee,
  senior, regional, city, etc.» y «all cancelled games».
- **IFFHS** (vía el artículo de Wikipedia, con URL a su nota de 21-09-2024) se limita a «top-level
  competitions» de club y selección; excluyó en su día los goles de guerra de Bican y luego lo
  reconoció con otra cifra.
- **Wikipedia** publica una tabla aparte de goles «reconocidos oficialmente», que es la que da 762 a
  Pelé y 722 a Bican.

Las tres son fuentes serias. Discrepan porque **miden cosas distintas**, no porque una mienta.

## 5. Límites, declarados

- Solo hombres mayores; la serie estudia también listas femeninas en otro momento.
- Las cifras «+» son cotas mínimas según la propia fuente (carreras de las que falta detalle de temporada).
- No se hace scraping de Transfermarkt, FBref ni worldfootball.
- **Ninguna fotografía de jugador**: el episodio y la web usan ilustración genérica de la casa.

## 6. Verificaciones

1. La tabla de RSSSF se leyó de su página el 02-10-2026 y las cifras de los 14 primeros jugadores se
   transcribieron con su número de partidos.
2. La lista de la IFFHS se leyó a través del artículo de Wikipedia, que la cita con URL y fecha
   (21-09-2024) para cada jugador.
2b. La nueve cifras de Pelé se verificaron una a una contra su fuente: el PDF de números del estado de
   São Paulo (1.282; Santos 1.091 = 643 oficiales + 448 amistosos), la nota del Santos (1.091), la nota
   de ESPN con la cifra de FIFA (1.281), el obituario del NYT (1.279) y Guinness (1.283).
3. Pendiente y anotado: comprobar a mano, en la ficha individual de RSSSF (`pbicandata.html`,
   `pdeakdata.html`), el detalle partido a partido de Bican y Deák, los dos casos con «+».

## 7. Qué enseña la web (siguiente paso)

Un selector de criterio («solo oficial», «oficial ampliado», «todo lo publicado») que reordena a los
jugadores en vivo, con la cifra moviéndose delante del lector y el desglose de qué entra en cada regla.
Es el inverso de un ranking: no dice quién es el mejor, enseña cuánto depende de la regla.
