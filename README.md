# Embalaje · Arqueta Folding

Aplicación web para planear cargas de camión de cajas plegadizas: catálogo de
productos con ficha de embalaje, armado visual del camión por arrastrar y
soltar, cálculo de tarimas ocupadas, destinos con tarifas y optimización de
flete.

**Entrar:** https://proyectos-arqueta-folding.github.io/embalaje-arqueta-demo/

## Cómo funciona

Es una sola página (`index.html`, sin build step) con Alpine.js. Corre
completa en el navegador: el catálogo, los destinos y las cargas guardadas
se almacenan en `localStorage`, así que la información persiste entre
sesiones en cada equipo y no requiere servidor.

## Qué incluye

- **Armar camión** — arrastra productos al camión y ve en vivo cuántas
  tarimas ocupan, si caben y qué se queda fuera.
- **Cargas** — historial de cargas guardadas con su detalle.
- **Catálogo** — productos, clientes y ficha de embalaje (postetas por caja,
  cantidad por cama, estiba, precio).
- **Destinos y fletes** — tarifas por tipo de unidad y optimización de la
  combinación de camiones más barata.
- **Reportes** — aprovechamiento de tarimas por carga.

## Desarrollo

No hay dependencias que instalar. Para probar en local:

```bash
python3 -m http.server 8000
# abre http://localhost:8000
```
