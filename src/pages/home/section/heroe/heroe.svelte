<script lang="ts">
  import './heroe.css';
  import { assetUrl } from '../../../../assets';
  // Props o lógica del componente
</script>

<section class="heroe-seccion" id="heroe">
  <!-- Imagen de fondo directa en el HTML -->
  <img src={assetUrl("imagenes/fondo.jpg")} alt="Interior de la cafetería" class="heroe-fondo-img">
<div class="heroe-overlay"></div>
  <div class="heroe-contenedor">
    <div class="heroe-texto">
      <h1>
        Para una sonrisa tómate un café,
        <span class="elegante cursiva texto-secundario">
          para una alegría tómate un té
        </span>
      </h1>
      <p>Una taza que da vida y una cafetería que comparte alegría</p>
      <div>
        <a href="#catalogo" class="boton boton-secundario">
          Explorar catálogo
        </a>
      </div>
    </div>
  </div>
</section>
