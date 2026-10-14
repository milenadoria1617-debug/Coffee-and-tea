<script lang="ts">
  import './catalogo.css';
  import Productos from '../../../../components/Productos.svelte';
  import { assetUrl } from '../../../../assets';
</script>

<section id="catalogo" class="fondo-principal">
  <div class="contenedor-seccion">
    <div class="catalogo-header">
      <span>Colección Exclusiva</span>
      <h2>Explora nuestros productos</h2>
    </div>
    <div style="display: flex; justify-content: flex-end; margin-bottom: 1.5rem; width: 100%;">
      <a href={assetUrl('catalogo')} class="boton-catalogo" style="flex: 0 0 auto !important; width: auto !important; display: inline-flex; padding: 0.65rem 1rem;">Ver catálogo completo</a>
    </div>
    <Productos aleatorios />
  </div>
</section>
