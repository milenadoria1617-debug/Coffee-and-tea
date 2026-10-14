<script lang="ts">
  import productos from '../data/productos.json';
  import { assetUrl } from '../assets';

  export let aleatorios = false;

  function seleccionarProductos() {
    const seleccion = [...productos];
    for (let i = seleccion.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * (i + 1));
      [seleccion[i], seleccion[j]] = [seleccion[j], seleccion[i]];
    }
    return seleccion.slice(0, 3);
  }

  $: productosVisibles = aleatorios ? seleccionarProductos() : productos;
</script>

<div class="catalogo-contenido cuadricula">
  {#each productosVisibles as producto (producto.id)}
    <div class="catalogo-item">
      <div class="catalogo-imagen">
        <img src={assetUrl(producto.imagen)} alt={`Foto de ${producto.nombre}`}>
      </div>
      <div class="item-contenido">
        <div class="informacion-producto">
          <h3>
            <a href={assetUrl(`detalle/${encodeURIComponent(producto.id)}`)} style="color: inherit; text-decoration: none;">{producto.nombre}</a>
          </h3>
        </div>
        <p class="producto-descripcion">{producto.descripcion}</p>
        <div class="precio">
          <span class="precio-label">Precio</span>
          <br>
          <span class="precio-valor">{producto.precio}</span>
        </div>
      </div>
    </div>
  {/each}
</div>
