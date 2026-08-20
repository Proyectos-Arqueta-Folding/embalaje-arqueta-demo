# Embalaje · Arqueta Folding

Aplicación web para planear cargas de camión de cajas plegadizas: catálogo de
productos con ficha de embalaje, armado visual del camión por arrastrar y
soltar, cálculo de tarimas ocupadas, destinos con tarifas y optimización de
flete.

**Entrar:** https://proyectos-arqueta-folding.github.io/embalaje-arqueta-demo/

## Cómo funciona

Es una sola página (`index.html`, sin build step) con Alpine.js, sin servidor
propio. Tiene dos modos:

- **Compartido** (recomendado) — los datos viven en Supabase, así que lo que
  guarda una computadora lo ven todas. La app se refresca sola cada 20
  segundos; abajo a la derecha aparece "Sincronizado".
- **Local** — si no hay Supabase configurado, todo se guarda en el
  `localStorage` del navegador. Funciona igual, pero cada equipo tiene sus
  propios datos. La etiqueta de abajo dice "Modo local · solo este equipo".

### Conectar Supabase (una sola vez)

1. Crea un proyecto gratis en [supabase.com](https://supabase.com).
2. En **SQL Editor → New query**, pega y ejecuta `supabase/schema.sql`.
   Eso crea las tablas y carga el catálogo inicial (clientes, productos,
   camiones y destinos).
3. En **Project Settings → API** copia la *Project URL* y la llave *anon*.
4. En `index.html`, al final del archivo, llena las dos constantes:

   ```js
   const SUPABASE_URL = "https://xxxxxxxx.supabase.co";
   const SUPABASE_ANON_KEY = "eyJ...";
   ```

5. Sube el cambio. Listo: todas las computadoras comparten los mismos datos.

> **Sobre la seguridad:** la app no tiene login, así que entra con la llave
> anon, que es pública y viaja en el HTML. Con las políticas de
> `schema.sql`, cualquiera que conozca la dirección de la app puede leer y
> escribir. Si eso no es aceptable, hay que agregar login de Supabase y
> cambiar las políticas de `anon` a `authenticated`.

### Tamaño de la vista

Arriba del camión hay dos controles para agrandar o achicar las tarimas y las
tarjetas de producto. Es una preferencia de cada equipo: se guarda en el
navegador y no se comparte.

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
