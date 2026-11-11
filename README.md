# Catálogo Vue — Actividad 1 (Unidad 4)

**Materia:** Interacción de Servicios Digitales
**Alumno:** Juan Luis Cano Ponce
**Framework asignado:** Vue 3 (Vite + Vue Router)

App "Catálogo" que consume la API pública [Fake Store API](https://fakestoreapi.com/products), lista productos, filtra por texto y muestra el detalle de cada producto en otra ruta.

## Instrucciones

```bash
npm install
npm run dev        # desarrollo en http://localhost:5173
npm run build      # build de producción en /dist
npm run preview    # servir el build para medir con Lighthouse
```

Requiere Node.js 18 o superior.

## Estructura

```
src/
├── main.js            # arranque de la app
├── App.vue            # layout general (encabezado + <router-view>)
├── router/index.js    # rutas: "/" y "/producto/:id"
├── views/Home.vue     # lista + filtro por texto (ref, computed)
├── views/Detail.vue   # detalle del producto (props de ruta)
└── style.css
```

## Capturas

> Agrega aquí tus capturas (`docs/lista.png`, `docs/filtro.png`, `docs/detalle.png`, `docs/lighthouse.png`):
>
> `![Lista](docs/lista.png)`

## Métricas

| Métrica | Valor |
|---|---|
| Tiempo de desarrollo | _(anota tus horas reales)_ |
| Líneas de código (JS + Vue, sin CSS) | 115 |
| Líneas totales (incluye CSS e index.html) | 168 |
| Bundle JS (producción) | 96.92 kB (37.83 kB gzip) |
| Bundle CSS (producción) | 1.53 kB (0.72 kB gzip) |
| Bundle total | ≈ 98.9 kB (≈ 38.9 kB gzip) |
| Lighthouse (Performance / Accessibility / Best Practices / SEO) | _(mídelo con `npm run preview`)_ |

Build medido con Vite 5.4 y Vue 3.5.

## Fila de la matriz comparativa

| Framework | Reactividad | Renderizado | Bundle (kB) | Lighthouse | Curva de aprendizaje | Caso de uso ideal |
|---|---|---|---|---|---|---|
| Vue 3 (Vite, Nuxt opcional) | Proxies (`ref`/`reactive`) con dependencias rastreadas automáticamente | CSR con Vite; SSR/SSG con Nuxt | ≈ 98.9 (≈ 38.9 gzip) | _(tu resultado)_ | Baja-media | Dashboards y apps medianas con equipos pequeños o juniors |
