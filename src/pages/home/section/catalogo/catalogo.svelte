<script lang="ts">
  import './catalogo.css';
  import { assetUrl } from '../../../../assets';
  import { onMount } from 'svelte';

  const originalScripts: { attributes: string[][]; content: string }[] = [];
  onMount(() => {
    const previousClass = document.body.className;
    const previousStyle = document.body.getAttribute('style');
    const titleElement = document.head.querySelector('title');
    const previousTitleId = titleElement?.getAttribute('id');
    
    
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
      
      
    };
  });
</script>

<section id="catalogo" class="fondo-principal">
          <div class="contenedor-seccion">
            <div class="catalogo-header">
              <span>Colección Exclusiva</span>

              <h2>Explora nuestros productos</h2>
            </div>

            <div style="display: flex; justify-content: flex-end; margin-bottom: 1.5rem; width: 100%;"><a href="catalogo.html" class="boton-catalogo" style="flex: 0 0 auto !important; width: auto !important; display: inline-flex; padding: 0.65rem 1rem;">Ver catálogo completo</a></div><div class="catalogo-contenido cuadricula">
              <div class="catalogo-item">
                <div class="catalogo-imagen">
                  <img src={assetUrl("imagenes/nathan-dumlao-zUNs99PGDg0-unsplash-copia.jpg")} alt="Foto de heart of melon">
                </div>
                <div class="item-contenido">
                  <div class="informacion-producto">
                    <h3><a href="detalle.html?titulo=heart+of+melon&amp;precio=Precio%0A++++++++++++++++++++%0A++++++++++++++++++++%24+50.000&amp;desc=Un+sorbo+de+felicidad+en+cada+taza+.+Cafe+preparado+con%0A++++++++++++++++++++pasion+%2C+sabor+que+enamora+y+un+momento+perfecto+para%0A++++++++++++++++++++disfrutar+.&amp;img=%2Fimagenes%2Fnathan-dumlao-zUNs99PGDg0-unsplash-copia.jpg" style="color: inherit; text-decoration: none;">heart of melon</a></h3>
                  </div>
                  <p class="producto-descripcion">
                    Un sorbo de felicidad en cada taza . Cafe preparado con
                    pasion , sabor que enamora y un momento perfecto para
                    disfrutar .
                  </p>
                  <div class="precio">
                    <span class="precio-label">Precio</span>
                    <br>
                    <span class="precio-valor">$ 50.000</span>
                  </div>
                </div>
              </div>

              <div class="catalogo-item">
                <div class="catalogo-imagen">
                  <img src={assetUrl("imagenes/te-elle-gourmet-68df7d1065ed6.jpg")} alt="Foto de Spring">
                </div>
                <div class="item-contenido">
                  <div class="informacion-producto">
                    <h3><a href="detalle.html?titulo=Spring&amp;precio=Precio%0A++++++++++++++++++++%0A++++++++++++++++++++%24+50.000&amp;desc=Calidez+en+sobra+sorbo.+Una+taza+de+te+que+invita+a%0A++++++++++++++++++++relajarse%2C+disfrutar+y+convertir+cualquier+momentos+en+pausa%0A++++++++++++++++++++llena+de+encanto+.&amp;img=%2Fimagenes%2Fte-elle-gourmet-68df7d1065ed6.jpg" style="color: inherit; text-decoration: none;">Spring</a></h3>
                  </div>
                  <p class="producto-descripcion">
                    Calidez en sobra sorbo. Una taza de te que invita a
                    relajarse, disfrutar y convertir cualquier momentos en pausa
                    llena de encanto .
                  </p>
                  <div class="precio">
                    <span class="precio-label">Precio</span>
                    <br>
                    <span class="precio-valor">$ 50.000</span>
                  </div>
                </div>
              </div>

              <div class="catalogo-item">
                <div class="catalogo-imagen">
                  <img src={assetUrl("imagenes/images.jpg")} alt="Foto de confectionery">
                </div>
                <div class="item-contenido">
                  <div class="informacion-producto">
                    <h3><a href="detalle.html?titulo=confectionery&amp;precio=Precio%0A++++++++++++++++++++%0A++++++++++++++++++++%24+50.000&amp;desc=El+postre+que+enamora+a+primera+vista.+Cremoso+%2C+suave+y+con%0A++++++++++++++++++++el+delicioso+sabor+del+cafe+que+convierte+cada+bocado+en+una%0A++++++++++++++++++++experiencia+inolvidable+.&amp;img=%2Fimagenes%2Fimages.jpg" style="color: inherit; text-decoration: none;">confectionery</a></h3>
                  </div>
                  <p class="producto-descripcion">
                    El postre que enamora a primera vista. Cremoso , suave y con
                    el delicioso sabor del cafe que convierte cada bocado en una
                    experiencia inolvidable .
                  </p>
                  <div class="precio">
                    <span class="precio-label">Precio</span>
                    <br>
                    <span class="precio-valor">$ 50.000</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </section>