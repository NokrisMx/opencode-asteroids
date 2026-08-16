# Asteroids

Clon del clásico arcade **Asteroids** implementado en canvas HTML5 puro, sin dependencias ni bundler.

## Descripción

Nave espacial en un campo de asteroides con envolvimiento de bordes (el espacio es toroidal). Destruye asteroides para sumar puntos: los grandes se parten en medianos, los medianos en pequeños. Incluye power-ups especiales y tipos de asteroides únicos como la estrella fugaz.

## Tecnologías

- **HTML5 Canvas** — renderizado 2D
- **JavaScript (ES6+)** — lógica del juego en un solo archivo `game.js`
- Sin frameworks, sin bundler, sin dependencias

## Cómo correr

Abre `index.html` directamente en el navegador (doble clic), o usa un servidor local:

```bash
npx serve .
```

Luego visita `http://localhost:3000`.

## Controles

| Tecla     | Acción     |
| --------- | ---------- |
| `←` `→`   | Rotar nave |
| `↑`       | Propulsar  |
| `Espacio` | Disparar   |
| `S`       | Cambiar skin |

## Skins de la nave

El juego incluye 3 skins cosméticas que cambian la silueta, el color y la llama de la nave. La selección se guarda automáticamente en `localStorage` y persiste al recargar.

| Skin        | Color     | Descripción                     |
| ----------- | --------- | ------------------------------- |
| Clásica     | Blanco    | Silueta triángulo con muesca    |
| Interceptor | Celeste   | Forma afilada y estrecha        |
| Exploradora | Verde     | Silueta pentagonal asimétrica   |

## Puntuación

| Asteroide | Puntos |
| --------- | ------ |
| Grande    | 20     |
| Mediano   | 50     |
| Pequeño   | 100    |
| Estrella fugaz | 250 |

## Características

- 3 vidas con invencibilidad temporal al reaparecer (parpadeo)
- Asteroides se parten en fragmentos más pequeños al ser destruidos
- Partículas de explosión al destruir asteroides
- **Power-up Velocidad**: al destruir un asteroide hay un 20% de probabilidad de que aparezca un hexágono celeste con "V". Al recogerlo, la nave mueve el doble de rápido durante 5 segundos (doble empuje). Se desvanece si no se recoge en 8 segundos. La llama del propulsor se vuelve celeste mientras el efecto está activo.
- **Estrella Fugaz**: un asteroide dorado que aparece una vez por nivel. Se mueve 3 veces más rápido que un asteroide pequeño, desaparece después de 5 segundos y vale 250 puntos. Tiene un brillo distintivo y una estela de fuego. No se divide al destruirlo y no bloquea el avance al siguiente nivel.
