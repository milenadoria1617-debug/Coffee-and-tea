<script lang="ts">
  import './sobrenosotros.css';
  import { assetUrl } from '../../../../assets';
  // Props o lógica del componente
</script>

<section class="sobre-nosotros-seccion" id="sobre-nosotros">
          <div class="sobre-nosotros-contendor">
            <div class="col-izq-sobre">
              <div class="contenedor-imagen">
                <img class="imagen-estudio" src={assetUrl("imagenes/sobre-nosotros.png")} alt="Barra de Coffee and Tea con una selección de cafés y tés" loading="lazy">
              </div>
            </div>
            <div class="col-der-sobre">
              <span class="sobre-nosotros-etiqueta">Nuestra esencia</span>
              <h2 class="titulo-sobre-nosotros">
                Es un aroma a hogar, un espacio especial
              </h2>
              <div class="texto-sobre">
                <p>
                  Más que café, te brindamos experiencias con un sabor único. Cada taza es una invitación a disfrutar y sentirte en casa.
                </p>
                <p>
                  Un espacio cálido y cómodo para compartir, hacer una pausa y disfrutar de esos pequeños momentos que alegran el día.
                </p>
                <p class="descripcion">
                  Ven por el aroma, quédate por el sabor. Siempre habrá una razón para volver.
                </p>
              </div>
            </div>
          </div>
        </section>
