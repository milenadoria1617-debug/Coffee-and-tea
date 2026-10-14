<script lang="ts">
  import './catalogo.css';
  import Productos from '../../components/Productos.svelte';
  import { assetUrl } from '../../assets';
  import { onMount } from 'svelte';
  import Navbar from '../home/section/navbar/navbar.svelte';
  import Footer from '../home/section/footer/footer.svelte';
  const originalScripts: { attributes: string[][]; content: string }[] = [{"attributes":[["src","navbar.js"]],"content":""}];
  onMount(() => {
    const previousClass = document.body.className;
    const previousStyle = document.body.getAttribute('style');
    const titleElement = document.head.querySelector('title');
    const previousTitleId = titleElement?.getAttribute('id');
    
    document.body.className = "";
    document.body.setAttribute('style', "");
    const mountedScripts: HTMLScriptElement[] = [];
    let cancelled = false;
    // Re-run the original page scripts after Svelte mounts their original DOM.
    queueMicrotask(async () => {
      for (const original of originalScripts) {
        if (cancelled) break;
        const script = document.createElement('script');
        for (const [name, value] of original.attributes) {
          script.setAttribute(name, name === 'src' ? assetUrl(value) : value);
        }
        script.textContent = original.content.replace(/\b(?:window\.)?location\.search\b/g, '(window.__svelteProductSearch ?? window.location.search)');
        const loaded = script.src ? new Promise<void>((resolve) => {
          script.onload = () => resolve();
          script.onerror = () => resolve();
        }) : Promise.resolve();
        mountedScripts.push(script);
        document.body.appendChild(script);
        await loaded;
      }
    });
    return () => {
      cancelled = true;
      mountedScripts.forEach((script) => script.remove());
      
      document.body.className = previousClass;
      if (previousStyle === null) document.body.removeAttribute('style');
      else document.body.setAttribute('style', previousStyle);
    };
  });
</script>
<svelte:head><meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Document</title></svelte:head>

  <Navbar pageAttributes={{"id":"barra-navegacion","class":"navbar"}} pageLinks={["#heroe","#heroe","#sobre-nosotros","#catalogo","#contacto"]} />
    <div class="contenedor-principal">
     
      <main>
        <section class="heroe-seccion" id="heroe">
          <div class="heroe-contenedor">
            <div class="heroe-texto">
              <h1>
                Para una sonrisa tomaté un cafe,<span class="elegante cursiva texto-secundario">
                  <span style="color: #f2df07 !important">para una alegria tomaté un té</span></span>
              </h1>
              <p>Una taza que da vida y una cafeteria que comparte alegria</p>
              <div>
                <a href="#catalogo" class="boton boton-secundario">
                  Explorar catalogo
                </a>
              </div>
            </div>
            <div class="heroe-imagen-contenedor">
              <img src={assetUrl("imagenes/tranquilidad-café-interior-ambiente-urbano-fotografía-diseño-moderno-luz-natural-estética-minimalista-descubra-una-serena-381843134.webp")} alt="">
            </div>
          </div>
        </section>
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

  <section id="catalogo" class="fondo-principal">
  <div class="contenedor-seccion">
    <div class="catalogo-header">
      <span>Colección Exclusiva</span>
    
    
      <h2>Explora nuestros productos</h2>
    </div>

    <Productos />
  </div>
</section>
   
      
  <section id="contacto" class="seccion-contacto fondo-secundario">
  <div class="contenedor-seccion">
    <div class="contacto-cabecera">
      <span class="contacto-insignia">Hablemos</span>
      <h2 class="contacto-titulo">Ponte en Contacto</h2>
      <p class="contacto-bajada">Déjanos tu consulta o mensaje y nos pondremos en contacto contigo.</p>
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
</main>
    </div>


  <Footer pageAttributes={{"class":"sitio-footer fondo-principal","id":"pie-de-pagina"}} pageLinks={["#heroe","#sobre-nosotros","#catalogo","#contacto"]} />

  
  


