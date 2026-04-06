<script>
  const heroImage = '/mercy/IMG_20260404_161838_289(1).jpg.jpeg';
  const introImage = '/mercy/Screenshot_20260403_120949_Instagram.jpg';
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
    { title: 'Smoke Ritual', src: '/mercy/Screenshot_20260403_121104_Instagram.jpg' },
    { title: 'Kitchen Noir', src: '/mercy/Screenshot_20260403_121232_Instagram.jpg' },
    { title: 'Cowgirl Edit', src: '/mercy/Screenshot_20260403_121702_Instagram.jpg' },
    { title: 'Side Profile', src: '/mercy/Screenshot_20260403_122221_Instagram.jpg' }
  ];
  const offerings = [
    ['Yoga & Somatic Practices', 'Movement as a form of healing, presence, and deeper connection.', '/mercy/Screenshot_20260403_121355_Instagram.jpg'],
    ['Pranayama & Meditation', 'Mindful breathing and stillness to cultivate peace and clarity.', '/mercy/Screenshot_20260403_121512_Instagram.jpg'],
    ['Holistic Beauty', 'Natural beauty rituals and organic products that nourish body and skin.', '/mercy/Screenshot_20260403_120919_Instagram.jpg'],
    ['Conscious Living', 'Slow fashion and thoughtful choices rooted in sustainability and care.', '/mercy/Screenshot_20260403_122408_Instagram.jpg']
  ];
  const archiveShots = [
    { src: '/mercy/Screenshot_20260403_122437_Instagram.jpg', alt: 'Mercy in red lace standing by a window', wide: false },
    { src: '/mercy/IMG_20260403_230604_459.jpg.jpeg', alt: 'Portrait in green dress lying in the grass', wide: true },
    { src: '/mercy/Screenshot_20260403_122015_Instagram.jpg', alt: 'Black and white bodysuit portrait', wide: false },
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
  let activeGalleryImage = null;

  function openGalleryImage(image) {
    activeGalleryImage = image;
  }

  function closeGalleryImage() {
    activeGalleryImage = null;
  }

  function handleLightboxKeydown(event) {
    if (event.key === 'Escape' && activeGalleryImage) {
      closeGalleryImage();
    }
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
    <section class="hero-panel">
      <div class="hero-topline">
        <span>Mercy Andrea</span>
        <span>Wellness / Beauty / Conscious Living</span>
      </div>
      <div class="hero-actions">
        <a class="hero-action dark" href="#archive">View Gallery</a>
        <a class="hero-action" href="#shop-favorites">Shop Favorites</a>
      </div>
      <div class="hero-art">
        <img class="hero-photo" src={heroImage} alt="Mercy portrait standing in a meadow wearing a floral dress" />
        <div class="hero-glow"></div>
        <div class="hero-footer">
          <span>Yoga and somatics</span>
          <span>Beauty and mindful living</span>
        </div>
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
      <div class="mosaic-grid">
        {#each tiles as tile}
          <button
            class="mosaic-card"
            type="button"
            aria-label={`Open ${tile.title}`}
            on:click={() => openGalleryImage({ src: tile.src, alt: tile.title, caption: tile.title })}
          >
            <img src={tile.src} alt={tile.title} />
          </button>
        {/each}
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
      <div class="archive-grid">
        {#each archiveShots as shot}
          <button
            class:wide-shot={shot.wide}
            class="archive-card"
            type="button"
            aria-label={`Open ${shot.alt}`}
            on:click={() => openGalleryImage({ src: shot.src, alt: shot.alt, caption: shot.alt })}
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
    <div class="lightbox-panel">
      <button class="lightbox-close" type="button" aria-label="Close popup" on:click={closeGalleryImage}>
        Close
      </button>
      <img class="lightbox-image" src={activeGalleryImage.src} alt={activeGalleryImage.alt} />
      <p class="lightbox-caption">{activeGalleryImage.caption}</p>
    </div>
  </div>
{/if}

<style>
  .page-stack{display:grid;gap:2rem}.line{border-top:1px solid var(--line);padding-top:1.6rem}
  .hero-panel,.intro-grid,.gallery-section,.services-section{animation:reveal .7s ease both}
  .hero-panel{display:grid;gap:.7rem}.hero-topline{display:flex;justify-content:space-between;gap:1rem;color:rgba(15,15,15,.72);font-size:.58rem;letter-spacing:.14em;text-transform:uppercase}
  .hero-actions{display:flex;flex-wrap:wrap;gap:.7rem}
  .hero-action{display:inline-flex;align-items:center;justify-content:center;padding:.86rem 1.08rem;border:1px solid rgba(17,17,17,.12);border-radius:999px;background:rgba(255,255,255,.54);font-size:.62rem;font-weight:700;letter-spacing:.14em;text-transform:uppercase;transition:transform .22s ease,border-color .22s ease,background-color .22s ease}
  .hero-action:hover{transform:translateY(-2px);border-color:rgba(17,17,17,.2);background:rgba(255,255,255,.82)}
  .hero-action.dark{color:#f7f3ec;background:#111111;border-color:#111111}
  .hero-action.dark:hover{background:#1b1b1b}
  .hero-art{position:relative;min-height:clamp(360px,64vw,620px);overflow:hidden;border-radius:.35rem;background:radial-gradient(circle at top left,rgba(255,255,255,.08),transparent 24%),linear-gradient(135deg,#050505 0%,#111111 44%,#1b1b1b 100%);box-shadow:0 30px 80px rgba(0,0,0,.22)}
  .hero-photo{position:absolute;inset:0;width:100%;height:100%;object-fit:cover;object-position:center 24%;filter:saturate(1.02) contrast(1.02)}
  .hero-glow{position:absolute;inset:0;background:linear-gradient(180deg,rgba(0,0,0,.62),rgba(0,0,0,.28) 38%,rgba(0,0,0,.56) 100%),linear-gradient(120deg,rgba(8,8,8,.6) 0%,rgba(8,8,8,.14) 48%,rgba(95,68,56,.16) 100%);pointer-events:none}
  .hero-footer{position:absolute;right:1.2rem;bottom:1rem;left:1.2rem;z-index:2;display:flex;justify-content:space-between;gap:1rem;color:rgba(255,245,235,.86);font-size:.58rem;letter-spacing:.12em;text-transform:uppercase}
  .intro-grid{display:grid;grid-template-columns:minmax(0,1.18fr) minmax(260px,.82fr);gap:1.2rem;align-items:start}
  .tag{margin:0 0 .32rem;padding:0;color:var(--orange-deep);font-family:var(--body-font);font-size:.64rem;font-weight:700;letter-spacing:.18em;text-transform:uppercase}
  h1,h2,h3,p{margin:0}.intro-copy{display:grid;gap:1rem}.intro-copy h1{max-width:20ch;font-size:clamp(1.4rem,3vw,2.45rem);line-height:1;letter-spacing:-.03em;text-transform:uppercase}
  .muted{color:var(--muted);line-height:1.6;font-size:.76rem}
  .intro-card{display:grid;gap:.8rem}.intro-thumb{min-height:245px;border-radius:.4rem;position:relative;overflow:hidden;box-shadow:var(--shadow)}.intro-thumb img{width:100%;height:100%;object-fit:cover;object-position:center 24%}
  .intro-card-copy{display:grid;gap:.4rem}.intro-card-copy span{color:#171717;font-size:.56rem;font-weight:700;letter-spacing:.14em;text-transform:uppercase}
  .codes-section{display:grid;gap:1.4rem}.codes-copy{display:grid;gap:.8rem;max-width:34rem;text-align:left}.codes-copy h2{font-size:clamp(1rem,1.8vw,1.5rem);line-height:1.16;letter-spacing:-.03em;text-transform:uppercase}.shop-stack{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:1.1rem;width:100%}.shop-card{display:grid;gap:.85rem;padding:1rem;border:1px solid rgba(214,205,194,.78);border-radius:1.4rem;background:linear-gradient(180deg,rgba(255,255,255,.92),rgba(250,246,241,.96));box-shadow:0 18px 45px rgba(22,14,10,.08)}.featured-shop-card{padding-top:.9rem}.compact-video-shop-card .shop-preview{min-height:140px}.contain-preview-shop-card .shop-preview{display:grid;place-items:center;padding:1rem;background:linear-gradient(180deg,#f7f0e8,#efe4da)}.contain-preview-shop-card .shop-preview img{object-fit:contain;max-width:min(100%,11rem);padding:.35rem}.emblem-shop-card{text-align:center}.emblem-shop-card .shop-card-meta{justify-content:center}.shop-preview{overflow:hidden;border-radius:1.05rem;min-height:160px;background:#efe7dc}.shop-preview img,.shop-preview video{width:100%;height:100%;object-fit:cover;object-position:center;display:block}.shop-emblem{display:grid;place-items:center;width:4.4rem;height:4.4rem;margin:.1rem auto .15rem;border-radius:999px;background:linear-gradient(180deg,#fcfaf6,#f1e8de);box-shadow:inset 0 1px 0 rgba(255,255,255,.9),0 14px 34px rgba(80,59,50,.08)}.shop-emblem::before{content:'';width:1.2rem;height:1.2rem;border-radius:80% 0 80% 80%;background:#8d7a72;transform:rotate(-45deg) translate(.04rem,-.04rem)}.shop-emblem-logo{padding:.65rem}.shop-emblem-logo::before{display:none}.shop-emblem-logo img{width:100%;height:100%;object-fit:contain}.shop-card-meta{display:flex;justify-content:space-between;align-items:center;gap:.7rem}.shop-kicker{color:#9a8e82;font-size:.5rem;font-weight:700;letter-spacing:.18em;text-transform:uppercase}.shop-badge{padding:.28rem .5rem;border-radius:999px;background:#f2ebe3;color:#8b7b71;font-size:.46rem;font-weight:700;letter-spacing:.12em;text-transform:uppercase}.shop-card h3{font-size:1.16rem;line-height:1.05;letter-spacing:-.03em;color:#332922}.shop-card p{font-size:.75rem;line-height:1.65}.shop-cta{display:inline-flex;justify-content:center;align-items:center;width:100%;margin-top:.2rem;padding:.9rem 1rem;border:1px solid #a28e87;border-radius:999px;background:#9f8b85;color:#fff;font-size:.58rem;font-weight:700;letter-spacing:.16em;text-transform:uppercase;transition:transform .22s ease,box-shadow .22s ease,background-color .22s ease}.shop-cta:hover{transform:translateY(-2px);box-shadow:0 12px 24px rgba(83,61,52,.16);background:#927f79}.dark-shop-cta{background:#111;color:#fff;border-color:#111}.dark-shop-cta:hover{background:#000;border-color:#000;box-shadow:0 12px 24px rgba(0,0,0,.18)}.ghost-shop-cta{background:transparent;color:#8d7d73;border-color:#e2d8cd;box-shadow:inset 0 0 0 1px rgba(255,255,255,.6)}.ghost-shop-cta:hover{background:#f7f1eb}
  .gallery-section{display:grid;gap:1.2rem}.section-head{display:flex;justify-content:space-between;gap:1rem;align-items:end}.section-head h2{max-width:min(100%,30rem);font-size:clamp(1rem,1.8vw,1.5rem);line-height:1.16;letter-spacing:-.03em;text-transform:uppercase}
  .mosaic-grid{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:.9rem}.mosaic-card{position:relative;min-height:clamp(160px,16vw,240px);overflow:hidden;border:0;border-radius:.35rem;padding:0;background:none;box-shadow:0 20px 50px rgba(22,14,10,.08);cursor:pointer;text-align:left;transition:transform .24s ease,box-shadow .24s ease;scroll-snap-align:start}.mosaic-card:hover{transform:translateY(-4px);box-shadow:0 24px 56px rgba(22,14,10,.14)}.mosaic-card img{width:100%;height:100%;object-fit:cover}
  .service-box h3{font-size:.74rem;letter-spacing:-.01em;text-transform:uppercase}
  .services-section{display:grid;gap:1.1rem}.services-grid{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:1rem}.service-box{display:grid;gap:.75rem;min-height:180px;padding:1rem;border:1px solid var(--line);border-radius:.45rem;background:rgba(255,255,255,.66);scroll-snap-align:start}.service-box img{width:100%;aspect-ratio:4/5;object-fit:cover;border-radius:.3rem}.service-box p{font-size:.74rem;line-height:1.5}
  .archive-section{display:grid;gap:1.2rem}.archive-grid{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:1rem}.archive-card{display:block;width:100%;overflow:hidden;border:0;border-radius:.45rem;padding:0;background:#fff;box-shadow:var(--shadow);cursor:pointer}.archive-card img{width:100%;height:100%;object-fit:cover}.wide-shot{grid-column:span 2}
  .lightbox{position:fixed;inset:0;z-index:40;display:grid;place-items:center;padding:1.2rem;backdrop-filter:blur(10px)}.lightbox-backdrop{position:absolute;inset:0;border:0;padding:0;background:rgba(12,10,8,.82);cursor:pointer}.lightbox-panel{position:relative;z-index:1;display:grid;gap:.8rem;width:min(100%,900px);max-height:calc(100vh - 2.4rem);padding:1rem;border:1px solid rgba(255,255,255,.14);border-radius:.7rem;background:rgba(18,16,14,.96);box-shadow:0 30px 80px rgba(0,0,0,.35)}.lightbox-image{max-height:78vh;object-fit:contain;border-radius:.45rem}.lightbox-caption{color:rgba(255,255,255,.8);font-size:.72rem;line-height:1.5;text-transform:uppercase;letter-spacing:.08em}.lightbox-close{justify-self:end;border:1px solid rgba(255,255,255,.18);border-radius:999px;padding:.65rem .9rem;background:rgba(255,255,255,.08);color:#fff;font-size:.6rem;font-weight:700;letter-spacing:.14em;text-transform:uppercase;cursor:pointer}
  @keyframes reveal{from{opacity:0;transform:translateY(18px)}to{opacity:1;transform:translateY(0)}}
  @media (max-width:960px){.intro-grid,.services-grid{grid-template-columns:1fr}.shop-stack,.services-grid,.archive-grid,.mosaic-grid{grid-template-columns:repeat(2,minmax(0,1fr))}.lightbox-panel{width:min(100%,760px)}}
  @media (max-width:680px){.hero-topline,.section-head,.hero-footer{grid-template-columns:1fr;display:grid;gap:.6rem}.shop-stack{grid-template-columns:1fr}.intro-copy h1,.intro-copy .muted{max-width:none}.mosaic-grid,.services-grid{display:grid;grid-auto-flow:column;grid-auto-columns:minmax(66%,72%);grid-template-columns:none;gap:.7rem;overflow-x:auto;padding:0 .05rem .35rem 0;scroll-snap-type:x mandatory;scrollbar-width:none;-webkit-overflow-scrolling:touch}.mosaic-grid::-webkit-scrollbar,.services-grid::-webkit-scrollbar{display:none}.mosaic-card{min-height:clamp(205px,56vw,280px)}.mosaic-card:nth-child(2),.mosaic-card:nth-child(3){min-height:clamp(205px,56vw,280px)}.archive-grid{display:block;columns:2;column-gap:.75rem}.archive-card{display:block;break-inside:avoid;margin:0 0 .75rem}.archive-card img{height:auto}.hero-footer{position:static;padding:0 1rem 1rem}.wide-shot{grid-column:auto}.service-box{gap:.6rem;min-height:0;padding:.85rem}.service-box img{aspect-ratio:4/4.4}.service-box h3{font-size:.68rem}.service-box p{font-size:.7rem;line-height:1.45}.lightbox{padding:.8rem}.lightbox-panel{padding:.8rem}.lightbox-image{max-height:70vh}.lightbox-caption{font-size:.66rem}.shop-card{padding:.9rem}}
</style>




