<script>
  const heroImage = '/mercy/landing-main.jpg';
  const introImage = '/mercy/Screenshot_20260403_121830_Instagram.jpg';
  const shopHeading = 'Selected links and codes.';
  const partnerLinks = [
    {
      brand: 'Remilia Hair',
      code: '',
      link: 'https://rstr.co/remiliahair/mercyremilia',
      note: 'Shop Mercyâ€™s Remilia Hair favorites.'
    },
    {
      brand: 'The Royal Codes',
      code: '',
      link: 'https://rstr.co/theroyalcodes/464',
      note: 'Curated access through Mercyâ€™s Royal Codes link.'
    },
    {
      brand: 'Sana',
      code: '707',
      link: 'https://sanausa.com/mercy',
      note: 'Use code 707 at checkout.'
    },
    {
      brand: 'Canoly',
      code: 'C16',
      link: 'https://canoly.com/?ref=MERCYFARRELL',
      note: 'Use code C16 for Mercyâ€™s Canoly link.'
    }
  ];
  const tiles = [
    { title: 'Smoke Ritual', src: '/mercy/Screenshot_20260403_121355_Instagram.jpg' },
    { title: 'Kitchen Noir', src: '/mercy/Screenshot_20260403_121232_Instagram.jpg' },
    { title: 'Cowgirl Edit', src: '/mercy/Screenshot_20260403_121702_Instagram.jpg' },
    { title: 'Side Profile', src: '/mercy/Screenshot_20260403_122221_Instagram.jpg' }
  ];
  const offerings = [
    ['Yoga & Somatic Practices', 'Movement as a form of healing, presence, and deeper connection.', '/mercy/Screenshot_20260403_121104_Instagram.jpg'],
    ['Pranayama & Meditation', 'Mindful breathing and stillness to cultivate peace and clarity.', '/mercy/Screenshot_20260403_121512_Instagram.jpg'],
    ['Holistic Beauty', 'Natural beauty rituals and organic products that nourish body and skin.', '/mercy/Screenshot_20260403_120919_Instagram.jpg'],
    ['Conscious Living', 'Slow fashion and thoughtful choices rooted in sustainability and care.', '/mercy/Screenshot_20260403_122408_Instagram.jpg']
  ];
  const archiveShots = [
    { src: '/mercy/Screenshot_20260403_122437_Instagram.jpg', alt: 'Mercy in red lace standing by a window', wide: false },
    { src: '/mercy/Screenshot_20260403_122015_Instagram.jpg', alt: 'Black and white bodysuit portrait', wide: false },
    { src: '/mercy/IMG_20260403_230604_459.jpg.jpeg', alt: 'Portrait in green dress lying in the grass', wide: true },
    { src: '/mercy/mercy-white-dress-window-portrait.jpeg', alt: 'Mercy in a soft white dress posing by a bright window', wide: false },
    { src: '/mercy/Screenshot_20260403_122115_Instagram.jpg', alt: 'Black and white tailored portrait', wide: false },
    { src: '/mercy/Screenshot_20260403_122521_Instagram.jpg', alt: 'Red lace indoor portrait', wide: true },
    { src: '/mercy/IMG_20260403_231438_148.jpg.jpeg', alt: 'Green dress portrait seated in the grass', wide: false },
    { src: '/mercy/Screenshot_20260403_121617_Instagram.jpg', alt: 'Mercy wearing a textured knit by a large window', wide: false },
    { src: '/mercy/Screenshot_20260403_121913_Instagram.jpg', alt: 'Boudoir portrait on bed', wide: true },
    { src: '/mercy/mercy-red-lace-chair-portrait.jpeg', alt: 'Mercy reclining in a chair wearing a red lace set', wide: false },
    { src: '/mercy/Screenshot_20260403_122310_Instagram.jpg', alt: 'Black and white leather jacket portrait', wide: false },
    { src: '/mercy/Screenshot_20260403_121547_Instagram.jpg', alt: 'Oversized sweater pose by window', wide: false },
    { src: '/mercy/Screenshot_20260403_122038_Instagram.jpg', alt: 'Black and white seated bed portrait', wide: false },
    { src: '/mercy/Screenshot_20260403_121333_Instagram.jpg', alt: 'Window portrait in black lace', wide: false },
    { src: '/mercy/Screenshot_20260403_122806_Instagram.jpg', alt: 'Black and white seated side profile portrait', wide: false }
  ];
  let activeGalleryList = [];
  let activeGalleryIndex = 0;
  $: activeGalleryImage = activeGalleryList.length > 0 ? activeGalleryList[activeGalleryIndex] : null;

  function openGallery(list, index, type) {
    activeGalleryList = list.map(item => ({
      src: item.src,
      alt: type === 'tiles' ? item.title : item.alt,
      caption: type === 'tiles' ? item.title : item.alt
    }));
    activeGalleryIndex = index;
  }

  function closeGalleryImage() {
    activeGalleryList = [];
  }

  function nextGalleryImage(e) {
    if (e) e.stopPropagation();
    if (activeGalleryList.length > 0) {
      activeGalleryIndex = (activeGalleryIndex + 1) % activeGalleryList.length;
    }
  }

  function prevGalleryImage(e) {
    if (e) e.stopPropagation();
    if (activeGalleryList.length > 0) {
      activeGalleryIndex = (activeGalleryIndex - 1 + activeGalleryList.length) % activeGalleryList.length;
    }
  }

  function handleLightboxKeydown(event) {
    if (!activeGalleryImage) return;
    if (event.key === 'Escape') closeGalleryImage();
    if (event.key === 'ArrowRight') nextGalleryImage();
    if (event.key === 'ArrowLeft') prevGalleryImage();
  }

  function getShopCard(item) {
    const cardMap = {
      'Remilia Hair': {
        eyebrow: 'Hair Ritual',
        badge: 'Featured',
        note: 'Selected favorites.',
        cta: 'Shop Now',
        ctaTone: 'dark',
        emblem: true,
        logo: '/brands/remilia-logo.avif'
      },
      'The Royal Codes': {
        eyebrow: 'Jewelry Edit',
        badge: 'Direct Link',
        note: 'Direct link.',
        cta: 'Visit Site',
        ctaTone: 'ghost'
      },
      Sana: {
        eyebrow: 'Wellness Support',
        badge: `Code ${item.code}`,
        note: 'Code 707.',
        cta: 'Shop Collection',
        ctaTone: 'ghost'
      },
      Canoly: {
        eyebrow: 'Beauty Ritual',
        badge: `Code ${item.code}`,
        note: 'Code C16.',
        cta: 'Discover',
        ctaTone: 'dark',
        emblem: true,
        logo: '/brands/canoly_logo-05.avif'
      }
    };

    return (
      cardMap[item.brand] ?? {
        eyebrow: 'Trusted Link',
        badge: item.code ? `Code ${item.code}` : 'Featured',
        cta: 'Visit Site',
        ctaTone: 'ghost'
      }
    );
  }
</script>

<svelte:head>
  <title>Mercy Andrea | Portfolio</title>
  <meta
    name="description"
    content="Mercy Andrea shares a visual journey through wellness, beauty, yoga, somatics, meditation, and conscious living."
  />
  <meta property="og:title" content="Mercy Andrea | Portfolio" />
  <meta
    property="og:description"
    content="Wellness, beauty, yoga, somatics, meditation, and conscious living."
  />
  <meta property="og:image" content={heroImage} />
  <meta property="og:image:alt" content="Soft white dress portrait holding camera" />
  <meta name="twitter:card" content="summary_large_image" />
  <meta name="twitter:title" content="Mercy Andrea | Portfolio" />
  <meta
    name="twitter:description"
    content="Wellness, beauty, yoga, somatics, meditation, and conscious living."
  />
  <meta name="twitter:image" content={heroImage} />
</svelte:head>

<svelte:window on:keydown={handleLightboxKeydown} />

<main class="page-stack" id="top">
    <section class="hero-panel stack-hero" id="top">
      <nav class="hero-nav-solid">
        <span>Editorial Portfolio</span>
        <span>Wellness / Beauty / Conscious Living</span>
      </nav>
      
      <div class="hero-top-content">
         <h1 class="magazine-title dark-text">MERCY<br/>ANDREA</h1>
         <div class="credibility-block dark-text">
           <span>Fashion & Lifestyle</span>
         </div>
      </div>

      <div class="hero-art boxed">
        <img class="hero-photo" src={heroImage} alt="Mercy portrait standing in a meadow wearing a floral dress" />
      </div>
    </section>

    <section class="intro-grid line" id="about">
      <div class="intro-copy">
        <p class="tag">About</p>
        <h1>Model, wellness enthusiast, and advocate for holistic living.</h1>
        <p class="muted">
          Welcome to Mercy's sanctuary of wellness and beauty, where yoga, somatics, meditation,
          and conscious living shape the journey she shares.
        </p>
      </div>
      <article class="intro-card">
        <div class="intro-thumb">
          <img src={introImage} alt="Mercy standing in a blue dress by a rustic gate" />
        </div>
        <div class="intro-card-copy">
          <span>My Journey</span>
          <p class="muted">From modeling and acting in her early 20s to a deeper wellness practice in her 30s.</p>
        </div>
      </article>
    </section>

    <section class="codes-section line" id="shop-favorites">
      <div class="codes-copy">
        <p class="tag">Shop</p>
        <h2>{shopHeading}</h2>
        <p class="muted">Quick access to partner links.</p>
      </div>
      <div class="shop-stack">
        {#each partnerLinks as item}
          {@const card = getShopCard(item)}
          <article class:featured-shop-card={card.preview || card.previewVideo} class:compact-video-shop-card={card.compactVideo} class:emblem-shop-card={card.emblem} class:contain-preview-shop-card={card.previewContain} class="shop-card">
            {#if card.previewVideo}
              <div class="shop-preview">
                <video
                  src={card.previewVideo}
                  autoplay
                  muted
                  loop
                  playsinline
                  preload="metadata"
                  aria-label={`${item.brand} featured preview video`}
                ></video>
              </div>
            {:else if card.preview}
              <div class="shop-preview">
                <img src={card.preview} alt={`${item.brand} featured card image`} />
              </div>
            {/if}
            {#if card.emblem}
              <div class:shop-emblem-logo={card.logo} class="shop-emblem" aria-hidden="true">
                {#if card.logo}
                  <img src={card.logo} alt="" />
                {/if}
              </div>
            {/if}
            <div class="shop-card-meta">
              <span class="shop-kicker">{card.eyebrow}</span>
              <span class="shop-badge">{card.badge}</span>
            </div>
            <h3>{item.brand}</h3>
            <p class="muted">{card.note ?? item.note}</p>
            <a class:ghost-shop-cta={card.ctaTone === 'ghost'} class:dark-shop-cta={card.ctaTone === 'dark'} class="shop-cta" href={item.link} target="_blank" rel="noreferrer">
              {card.cta}
            </a>
          </article>
        {/each}
      </div>
    </section>

    <section class="gallery-section line" id="collections">
      <div class="section-head">
        <div>
          <p class="tag">Visual Journey</p>
          <h2>Selected frames.</h2>
        </div>
      </div>
      <div class="swipe-container">
        <div class="swipe-track">
          {#each tiles as tile, i}
            <button
              class="swipe-card"
              type="button"
              aria-label={`Open ${tile.title}`}
              on:click={() => openGallery(tiles, i, 'tiles')}
            >
              <img src={tile.src} alt={tile.title} />
            </button>
          {/each}
        </div>
      </div>
    </section>

    <section class="services-section line">
      <div class="section-head">
        <div>
          <p class="tag">My Passion</p>
          <h2>Harmony of body, mind, spirit, and conscious beauty.</h2>
        </div>
      </div>
      <div class="services-grid">
        {#each offerings as item}
          <article class="service-box">
            <img src={item[2]} alt={item[0]} />
            <h3>{item[0]}</h3>
            <p class="muted">{item[1]}</p>
          </article>
        {/each}
      </div>
    </section>

    <section class="archive-section line" id="archive">
      <div class="section-head">
        <div>
          <p class="tag">Gallery</p>
          <h2>Selected images across editorial, fashion, and lifestyle work.</h2>
        </div>
      </div>
      <div class="masonry-gallery">
        {#each archiveShots as shot, i}
          <button
             class="masonry-item"
             type="button"
             aria-label={`Open ${shot.alt}`}
             on:click={() => openGallery(archiveShots, i, 'archive')}
          >
            <img src={shot.src} alt={shot.alt} />
          </button>
        {/each}
      </div>
    </section>

</main>

{#if activeGalleryImage}
  <div class="lightbox" role="dialog" aria-modal="true" aria-label="Gallery image popup" tabindex="-1">
    <button class="lightbox-backdrop" type="button" aria-label="Close popup" on:click={closeGalleryImage}></button>
    <button class="lightbox-close" type="button" aria-label="Close popup" on:click={closeGalleryImage}>
      ✕ CLOSE
    </button>
    <button class="lightbox-nav prev" type="button" aria-label="Previous image" on:click={prevGalleryImage}>&#10094;</button>
    <button class="lightbox-nav next" type="button" aria-label="Next image" on:click={nextGalleryImage}>&#10095;</button>
    <img class="lightbox-image" src={activeGalleryImage.src} alt={activeGalleryImage.alt} />
  </div>
{/if}

<style>
  :global(body) { background: #fff; color: #000; -webkit-font-smoothing: antialiased; overflow-x: hidden; }
  .page-stack{display:flex;flex-direction:column;gap:6rem;overflow:hidden}.line{border-top:5px solid #000;padding-top:3rem}
  .hero-panel,.intro-grid,.gallery-section,.services-section{animation:reveal .7s ease both; min-width: 0;}
  .hero-panel{display:block;width:100%;height:100vh;position:relative}
  .hero-panel.stack-hero { display: flex; flex-direction: column; gap: 2rem; padding: 2rem 2rem 0; height: auto; }
  .hero-art.full-bleed{position:absolute;inset:0;width:100%;height:100%;overflow:hidden;background:#000}
  .hero-art.boxed{position:relative;width:100%;height:75vh;overflow:hidden;background:#000}
  .hero-photo{position:absolute;inset:0;width:100%;height:100%;object-fit:cover;object-position:center 24%;filter:contrast(1.1) grayscale(10%)}
  .hero-glow.dark-gradient{position:absolute;inset:0;background:linear-gradient(0deg, rgba(0,0,0,0.7) 0%, transparent 50%, rgba(0,0,0,0.4) 100%);pointer-events:none}
  .hero-overlay{position:absolute;inset:0;display:flex;flex-direction:column;justify-content:space-between;padding:2rem;z-index:10}
  .hero-nav-transparent{display:flex;justify-content:space-between;color:#fff;font-size:0.75rem;font-weight:900;letter-spacing:0.18em;text-transform:uppercase}
  .hero-nav-solid{display:flex;justify-content:space-between;color:#000;font-size:0.75rem;font-weight:900;letter-spacing:0.18em;text-transform:uppercase}
  .hero-center{display:flex;flex-direction:column;align-items:center;text-align:center;gap:1.5rem;margin-top:auto;margin-bottom:auto}
  .hero-top-content{display:flex;flex-direction:column;align-items:center;text-align:center;gap:1.5rem;}
  .magazine-title{font-size:clamp(4rem, 12vw, 10rem);line-height:0.85;font-weight:900;color:#fff;letter-spacing:-0.05em;margin:0}
  .magazine-title.dark-text{color:#000}
  .credibility-block{display:flex;flex-wrap:wrap;justify-content:center;gap:1rem;color:#fff;font-size:0.85rem;font-weight:800;letter-spacing:0.2em;text-transform:uppercase}
  .credibility-block.dark-text{color:#000}
  .credibility-block .dot{opacity:0.5}
  .intro-grid{display:grid;grid-template-columns:1fr 1fr;gap:3rem;align-items:start}
  .tag{margin:0 0 .5rem;padding:0;color:#000;font-size:.7rem;font-weight:900;letter-spacing:.2em;text-transform:uppercase}
  h1,h2,h3,p{margin:0}.intro-copy{display:grid;gap:1rem}.intro-copy h1{font-size:clamp(3rem,6vw,5rem);font-weight:900;line-height:0.9;letter-spacing:-.04em;text-transform:uppercase;color:#000}
  .muted{color:#000;line-height:1.6;font-size:1rem;font-weight:600;}
  .intro-card{display:grid;gap:1.5rem}.intro-thumb{aspect-ratio:3/4;border-radius:0;position:relative;overflow:hidden;border:1px solid #000}.intro-thumb img{width:100%;height:100%;object-fit:cover;object-position:center}
  .intro-card-copy{display:grid;gap:.6rem;border-left:4px solid #000;padding-left:1rem;}.intro-card-copy span{color:#000;font-size:.7rem;font-weight:900;letter-spacing:.18em;text-transform:uppercase}
  .codes-section{display:flex;flex-direction:column;gap:2rem}.codes-copy{display:grid;gap:1rem;max-width:40rem;text-align:left}.codes-copy h2{font-size:clamp(2rem,4vw,3.5rem);line-height:0.9;letter-spacing:-.04em;text-transform:uppercase;font-weight:900}.shop-stack{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:0;width:100%;border:2px solid #000;border-right:none;border-bottom:none}.shop-card{display:grid;grid-template-rows:auto auto 1fr;gap:1.2rem;padding:1.5rem;border-right:2px solid #000;border-bottom:2px solid #000;border-radius:0;background:#fff}
  .featured-shop-card{padding-top:1.5rem}
  .shop-preview{overflow:hidden;border-radius:0;aspect-ratio:1;border:1px solid #000;background:#fff}.shop-preview img,.shop-preview video{width:100%;height:100%;object-fit:cover;object-position:center;display:block}
  .contain-preview-shop-card .shop-preview{display:grid;place-items:center;background:#000;padding:2rem}.contain-preview-shop-card .shop-preview img{object-fit:contain;max-width:min(100%,11rem)}
  .shop-emblem{display:grid;place-items:center;width:4.4rem;height:4.4rem;margin:.1rem auto .15rem;border-radius:0;border:1px solid #000;background:#000;}
  .shop-emblem-logo{padding:.65rem;background:#fff}.shop-emblem-logo img{width:100%;height:100%;object-fit:contain}
  .shop-card-meta{display:flex;justify-content:space-between;align-items:center;gap:.7rem;border-bottom:1px solid #000;padding-bottom:.5rem}.shop-kicker{color:#000;font-size:.6rem;font-weight:900;letter-spacing:.2em;text-transform:uppercase}.shop-badge{padding:.3rem .6rem;border:1px solid #000;border-radius:0;background:#000;color:#fff;font-size:.5rem;font-weight:900;letter-spacing:.18em;text-transform:uppercase}
  .shop-card h3{font-size:1.4rem;font-weight:900;line-height:1;letter-spacing:-.04em;text-transform:uppercase;color:#000}.shop-card p{font-size:.8rem;line-height:1.5}
  .shop-cta{display:inline-flex;justify-content:center;align-items:center;width:100%;margin-top:auto;padding:1rem;border:1px solid #000;border-radius:0;background:#000;color:#fff;font-size:.65rem;font-weight:900;letter-spacing:.2em;text-transform:uppercase;text-decoration:none}
  .dark-shop-cta{background:#000;color:#fff;border-color:#000}
  .ghost-shop-cta{background:#fff;color:#000;border-color:#000}
  .gallery-section{display:flex;flex-direction:column;gap:2rem;min-width:0;overflow:hidden;}.section-head{display:flex;justify-content:space-between;gap:1rem;align-items:end;margin-bottom:1rem}.section-head h2{font-size:clamp(2rem,4vw,3.5rem);font-weight:900;line-height:0.9;letter-spacing:-.04em;text-transform:uppercase;color:#000}
  
  .swipe-container{width:100%;min-width:0;}
  .swipe-track{display:flex;width:100%;gap:4px;overflow-x:auto;scroll-snap-type:x mandatory;scrollbar-width:none;background:#fff;padding-bottom:.5rem;}
  .swipe-track::-webkit-scrollbar{display:none}
  .swipe-card{flex:0 0 25vw;aspect-ratio:3/4;overflow:hidden;border:0;border-radius:0;padding:0;background:#fff;cursor:pointer;opacity:1;transition:opacity .3s;scroll-snap-align:start;}
  .swipe-card.wide-shot{flex:0 0 45vw;aspect-ratio:auto;}
  .swipe-card:hover{opacity:.8}.swipe-card img{width:100%;height:100%;object-fit:cover;object-position:center;filter:contrast(1.05);display:block}

  .services-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:2rem;width:100%}
  .service-box{display:flex;flex-direction:column;gap:1rem}
  .service-box img{width:100%;aspect-ratio:1;object-fit:cover;filter:contrast(1.05)}
  .service-box h3{font-size:1.1rem;font-weight:900;text-transform:uppercase;letter-spacing:-.04em;line-height:1.2}
  .archive-section{display:flex;flex-direction:column;gap:2rem;min-width:0;overflow:hidden;}
  .masonry-gallery{column-count:4;column-gap:4px;width:100%}
  .masonry-item{display:inline-block;width:100%;margin-bottom:4px;break-inside:avoid;border:none;padding:0;background:#000;cursor:pointer;transition:opacity 0.3s}
  .masonry-item:hover{opacity:0.8}
  .masonry-item img{width:100%;height:auto;display:block;filter:contrast(1.05)}
  
  .lightbox{position:fixed;inset:0;z-index:50;display:grid;place-items:center;padding:0;backdrop-filter:none}.lightbox-backdrop{position:absolute;inset:0;border:0;padding:0;background:rgba(0,0,0,.95);cursor:pointer}.lightbox-image{position:relative;z-index:1;max-height:85vh;max-width:calc(100vw - 12rem);object-fit:contain;border-radius:0;user-select:none}.lightbox-close{position:absolute;top:2rem;right:2rem;z-index:10;border:1px solid #fff;border-radius:0;padding:.8rem 1.2rem;background:transparent;color:#fff;font-size:.65rem;font-weight:900;letter-spacing:.2em;text-transform:uppercase;cursor:pointer;transition:background .2s,color .2s}.lightbox-close:hover{background:#fff;color:#000}.lightbox-nav{position:absolute;top:50%;transform:translateY(-50%);z-index:10;background:transparent;border:1px solid #fff;color:#fff;padding:1rem 1.5rem;font-size:1.5rem;cursor:pointer;transition:background .2s, color .2s;border-radius:0;display:grid;place-items:center;min-width:4rem}.lightbox-nav.prev{left:2rem}.lightbox-nav.next{right:2rem}.lightbox-nav:hover{background:#fff;color:#000}
  @keyframes reveal{from{opacity:0;transform:translateY(18px)}to{opacity:1;transform:translateY(0)}}
  @media (max-width:960px){.intro-grid{grid-template-columns:1fr}.shop-stack,.services-grid{grid-template-columns:repeat(2,minmax(0,1fr))}.masonry-gallery{column-count:3}.swipe-card{flex:0 0 35vw;}.swipe-card.wide-shot{flex:0 0 65vw;}}
  @media (max-width:680px){.page-stack{gap:2rem}.hero-panel.stack-hero{padding:1rem 1rem 0}.hero-overlay{padding:1.5rem}.hero-nav-transparent,.hero-nav-solid{flex-direction:column;align-items:center;gap:0.5rem;text-align:center}.magazine-title{font-size:4rem}.credibility-block{font-size:0.6rem;gap:0.5rem}.section-head,.hero-footer{grid-template-columns:1fr;display:grid;gap:.6rem}.shop-stack{grid-template-columns:1fr}.intro-copy h1,.intro-copy .muted{max-width:none}.services-grid{display:grid;grid-auto-flow:column;grid-auto-columns:minmax(80%,85%);grid-template-columns:none;gap:2px;overflow-x:auto;padding:0 0 1rem 0;scroll-snap-type:x mandatory;scrollbar-width:none;-webkit-overflow-scrolling:touch}.services-grid::-webkit-scrollbar{display:none}.hero-footer{position:static;padding:0 1rem 1rem;color:#000;}.service-box{gap:.6rem;padding:1.5rem}.lightbox-nav{padding:0.5rem;min-width:2.5rem;font-size:1rem;border-color:rgba(255,255,255,.3)}.lightbox-nav.prev{left:0.5rem}.lightbox-nav.next{right:0.5rem}.lightbox-close{top:0.75rem;right:0.75rem;padding:0.6rem 0.8rem;font-size:0.6rem}.lightbox-image{max-width:calc(100vw - 6rem)}.swipe-track::-webkit-scrollbar{display:none}.swipe-card{flex:0 0 60vw;}.swipe-card.wide-shot{flex: 0 0 85vw;}.masonry-gallery{column-count:2;column-gap:2px}.masonry-item{margin-bottom:2px}}
</style>




