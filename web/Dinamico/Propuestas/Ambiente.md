<div style="text-align:center;">
<img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Travel%20and%20places/Sun%20Behind%20Rain%20Cloud.png" alt="Man Technologist Medium-Dark Skin Tone" width="180px" />
</div>

 <!-- <div class="vocaroo-container">
        <iframe width="300" height="60" src="https://vocaroo.com/embed/1bfn2LKLm9JE?autoplay=1" frameborder="0" allow="autoplay"></iframe>
    </div> -->

# Leyes Ambientales
## Interiorizar
Aqui un contexto del por que es importante pensar ahora en estas leyes.
<iframe width="100%" height="315" src="https://www.youtube-nocookie.com/embed/ihq_TLPugZI?si=CchKDJMswyOXUVrU&amp;controls=0" title="YouTube video player" frameborder="0" allow="encrypted-media; picture-in-picture; " referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe> 


# En Paraguay
Actualmente no hay reciclador de reciduos ni separacion por tipo... 
No hay limites al plastico cuando bien se pueden volver a utilizar recipientes retornables de vidrio como en el pasado.
Todas las propuestas que se propondran abajo no Afecta el gasto publico, ya que son regulaciones.
El estado no deberia pagar para limpiar lo que otro ensucia, por eso se debe promover el reciclaje.


## Limitacion del Plastico
El uso del platico estara prohibido.
Solo las areas medicas o especificas que requieran plastico sera aprobada.

Antes se utilizaban recipientes de vidrio para todo


<div class="section">
    <div class="gallery-container">
        <div id="Ambiente_GaleriaVidrios-gallery" 
             class="contenedor-imagenes-animado"
             data-json-path="web/otros/Archivos/Imagenes/data.json">
</div>

Podriamos volver a ese tiempo, se reduciria enormemente la contaminacion por plasticos. Se fomentaria la devolucion de los envases de vidrio similar a las gaseosas coca de vidrio retornables





# Consecuencias de la Contaminacion:

## Ambiente


## Salud

## Extinciones 
Estas son varias Extinsiones de Animales en la ultima Decada.
Para Concientizar.

galeriaimagenes

Esto son solo unos cuantos, Puedes ver la lista completa en diversas webs como esta:























<!-- Galeria -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/Swiper/8.4.5/swiper-bundle.min.css">
<script src="https://cdnjs.cloudflare.com/ajax/libs/Swiper/8.4.5/swiper-bundle.min.js"></script>

<script>
async function loadGalleryData(jsonPath) {
    try {
        console.log(`Intentando cargar: ${jsonPath}`);
        const response = await fetch(jsonPath);
        console.log(`Response status: ${response.status}`);
        
        if (!response.ok) {
            throw new Error(`HTTP ${response.status}: ${response.statusText}`);
        }
        
        const data = await response.json();
        console.log('Datos cargados:', data);
        return data.galleries;
    } catch (error) {
        console.error(`Error loading gallery data from ${jsonPath}:`, error);
        return null;
    }
}

function createSwiper(container, images) {
    container.innerHTML = `
        <div class="swiper-wrapper">
            ${images.map(item => `
                <div class="swiper-slide">
                    <a href="${item.link || '#'}">
                        <img src="${item.image}" alt="${item.name || 'Imagen'}" loading="lazy" />
                    </a>
                </div>
            `).join('')}
        </div>
    `;

    return new Swiper(container, {
        slidesPerView: 'auto',
        spaceBetween: 20,
        loop: true,
        centeredSlides: true,
        autoplay: {
            delay: 3000,
            disableOnInteraction: false,
        }
    });
}

function filterGalleryData(galleryData, container) {
    const galleryKey = container.dataset.galleryKey;
    const galleryFilter = container.dataset.galleryFilter;
    const containerId = container.id.replace('-gallery', '');
    
    if (galleryKey && galleryData[galleryKey]) {
        return galleryData[galleryKey].images || [];
    }
    
    if (galleryFilter) {
        const matchingEntries = Object.entries(galleryData).filter(([key, value]) => 
            key.toLowerCase().includes(galleryFilter.toLowerCase())
        );
        
        if (matchingEntries.length > 0) {
            return matchingEntries.flatMap(([key, value]) => value.images || []);
        }
    }
    
    const matchingKey = Object.keys(galleryData).find(key => 
        key.toLowerCase() === containerId.toLowerCase()
    );
    
    if (matchingKey && galleryData[matchingKey]) {
        return galleryData[matchingKey].images || [];
    }
    
    return [];
}

async function initializeUniversalSwiper() {
    if (typeof Swiper === 'undefined') {
        console.log('Swiper no está cargado aún');
        return;
    }
    
    const galleryElements = document.querySelectorAll('.contenedor-imagenes-animado[data-json-path]');
    
    for (const container of galleryElements) {
        const jsonPath = container.dataset.jsonPath;
        
        if (!jsonPath) {
            container.innerHTML = '<p>No se especificó ruta JSON</p>';
            continue;
        }
        
        const galleryData = await loadGalleryData(jsonPath);
        
        if (!galleryData) {
            container.innerHTML = '<p>Error al cargar datos</p>';
            continue;
        }
        
        const images = filterGalleryData(galleryData, container);
        
        if (images.length > 0) {
            container.classList.add('swiper');
            createSwiper(container, images);
        } else {
            container.innerHTML = '<p>Sin Elementos</p>';
        }
    }
}

function waitForSwiperAndInit() {
    if (typeof Swiper !== 'undefined') {
        initializeUniversalSwiper();
    } else {
        setTimeout(waitForSwiperAndInit, 100);
    }
}

waitForSwiperAndInit();
</script>