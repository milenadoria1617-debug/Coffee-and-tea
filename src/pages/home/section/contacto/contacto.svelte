<script lang="ts">
  import './contacto.css';
  import { assetUrl } from '../../../../assets';
</script>
<section id="contacto" class="seccion-contacto fondo-secundario">
          <div class="contenedor-seccion">
            <div class="contacto-cabecera">
              <span class="contacto-insignia">Hablemos</span>
              <h2 class="contacto-titulo">Ponte en Contacto</h2>
              <p class="contacto-bajada">
                Déjanos tu consulta o mensaje y nos pondremos en contacto
                contigo.
              </p>
            </div>
            <div class="tarjeta-formulario-contacto">
              <form class="formulario-contacto">
                <div class="fila-formulario">
                  <div class="campo-grupo">
                    <label for="nombre">Nombre Completo</label>
                    <input type="text" id="nombre" name="nombre" autocomplete="name" placeholder="Ej. Alex Martínez" required>
                  </div>
                  <div class="campo-grupo">
                    <label for="email">Correo Electrónico</label>
                    <input type="email" id="email" name="email" autocomplete="email" placeholder="alex@ejemplo.com" required>
                  </div>
                </div>
                <div class="campo-grupo">
                  <label for="phone">Número de contacto</label>
                  <input type="tel" id="phone" name="phone" autocomplete="tel" placeholder="300 233 3443" required>
                </div>
                <div class="campo-grupo">
                  <label for="mensaje">¿Cómo podemos ayudarte?</label>
                  <textarea id="mensaje" name="mensaje" rows="4" placeholder="Escribe aquí tu mensaje..." required></textarea>
                </div>

                <button type="submit" class="boton-enviar-contacto">
                  <span>Enviar Mensaje</span>
                </button>
              </form>
            </div>
          </div>
        </section>