<script>
  import { onMount } from 'svelte';

  const currentYear = new Date().getFullYear();
  let menuOpen = false;
  let headerScrolled = false;
  const navLinks = [
    { label: 'Home', href: '#top' },
    { label: 'Journey', href: '#collections' },
    { label: 'Practice', href: '#plans' },
    { label: 'Journal', href: '#archive' }
  ];
  const heroImage = '/mercy/Screenshot_20260403_121830_Instagram.jpg';
  const introImage = '/mercy/Screenshot_20260403_120949_Instagram.jpg';
  const metrics = [
    { value: 'Body', label: 'movement and healing' },
    { value: 'Mind', label: 'breath and meditation' },
    { value: 'Spirit', label: 'conscious living' }
  ];
  const partnerLinks = [
    {
      brand: 'Remilia Hair',
      code: '',
      link: 'https://rstr.co/remiliahair/mercyremilia',
      note: 'Shop Mercy’s Remilia Hair favorites.'
    },
    {
      brand: 'The Royal Codes',
      code: '',
      link: 'https://rstr.co/theroyalcodes/464',
      note: 'Curated access through Mercy’s Royal Codes link.'
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
      note: 'Use code C16 for Mercy’s Canoly link.'
    }
  ];
  const tiles = [
    { title: 'Smoke Ritual', src: '/mercy/Screenshot_20260403_121104_Instagram.jpg' },
    { title: 'Kitchen Noir', src: '/mercy/Screenshot_20260403_121232_Instagram.jpg' },
    { title: 'Cowgirl Edit', src: '/mercy/Screenshot_20260403_121702_Instagram.jpg' },
    { title: 'Side Profile', src: '/mercy/Screenshot_20260403_122221_Instagram.jpg' }
  ];
  const featureImage = '/mercy/Screenshot_20260403_121617_Instagram.jpg';
  const approachImage = '/mercy/Screenshot_20260403_121314_Instagram.jpg';
  const workflow = [
    ['01', 'Yoga & Somatics', 'Movement is shared as a pathway to healing, grounding, and deeper connection with the body.'],
    ['02', 'Pranayama & Meditation', 'Breathwork and mindfulness practices create space for calm, clarity, and inner peace.'],
    ['03', 'Conscious Living', 'Slow fashion, ethical choices, and intentional beauty rituals guide the lifestyle behind the visuals.']
  ];
  const offerings = [
    ['Yoga & Somatic Practices', 'Gentle movement, embodied awareness, and rituals that celebrate healing and connection.', '/mercy/Screenshot_20260403_121355_Instagram.jpg'],
    ['Pranayama & Meditation', 'Breath-led practices and mindful pauses that support balance, clarity, and presence.', '/mercy/Screenshot_20260403_121512_Instagram.jpg'],
    ['Holistic Beauty', 'A natural approach to beauty with products and rituals that nourish body, skin, and spirit.', '/mercy/Screenshot_20260403_120919_Instagram.jpg'],
    ['Slow & Conscious Living', 'Thoughtful fashion, sustainable choices, and everyday wellness reflected through a softer lifestyle lens.', '/mercy/Screenshot_20260403_122408_Instagram.jpg']
  ];
  const planPoints = [
    'Modeling and acting began in her early 20s',
    'Wellness became the deeper focus in her 30s',
    'Yoga, somatics, meditation, and breathwork are central practices',
    'Natural beauty and conscious consumerism shape the lifestyle she shares'
  ];
  const planImage = '/mercy/Screenshot_20260403_122437_Instagram.jpg';
  const ctaImage = '/mercy/Screenshot_20260403_122626_Instagram.jpg';
  const archiveShots = [
    { src: '/mercy/Screenshot_20260403_121213_Instagram.jpg', alt: 'Black dress portrait indoors', wide: false },
    { src: '/mercy/IMG_20260403_230604_459.jpg.jpeg', alt: 'Portrait in green dress lying in the grass', wide: true },
    { src: '/mercy/Screenshot_20260403_122015_Instagram.jpg', alt: 'Black and white bodysuit portrait', wide: false },
    { src: '/mercy/Screenshot_20260403_122608_Instagram.jpg', alt: 'Soft white dress portrait holding camera', wide: false },
    { src: '/mercy/Screenshot_20260403_122521_Instagram.jpg', alt: 'Red lace indoor portrait', wide: true },
    { src: '/mercy/Screenshot_20260403_122115_Instagram.jpg', alt: 'Black and white tailored portrait', wide: false },
    { src: '/mercy/IMG_20260403_231438_148.jpg.jpeg', alt: 'Green dress portrait seated in the grass', wide: false },
    { src: '/mercy/Screenshot_20260403_121913_Instagram.jpg', alt: 'Boudoir portrait on bed', wide: true },
    { src: '/mercy/Screenshot_20260403_122310_Instagram.jpg', alt: 'Black and white leather jacket portrait', wide: false },
    { src: '/mercy/Screenshot_20260403_121547_Instagram.jpg', alt: 'Oversized sweater pose by window', wide: false },
    { src: '/mercy/Screenshot_20260403_122038_Instagram.jpg', alt: 'Black and white seated bed portrait', wide: false },
    { src: '/mercy/Screenshot_20260403_121333_Instagram.jpg', alt: 'Window portrait in black lace', wide: false },
    { src: '/mercy/Screenshot_20260403_122806_Instagram.jpg', alt: 'Black and white seated side profile portrait', wide: false }
  ];

  onMount(() => {
    const updateHeader = () => {
      headerScrolled = window.scrollY > Math.max(48, window.innerHeight * 0.18);
    };

    updateHeader();
    window.addEventListener('scroll', updateHeader, { passive: true });

    return () => window.removeEventListener('scroll', updateHeader);
  });
</script>

<svelte:head>
  <title>Mercy Andrea | Wellness Journal</title>
  <meta
    name="description"
    content="Mercy Andrea shares a visual journey through wellness, yoga, somatics, meditation, holistic beauty, and conscious living."
  />
</svelte:head>

<div class="site-shell">
  <header class:menu-open={menuOpen} class:scrolled={headerScrolled} class="mini-top">
    <div class="brand-wrap">
      <span class="brand-index">01 / Wellness Journal</span>
      <a class="brand-name" href="#top">Mercy Andrea</a>
    </div>

    <button
      class="menu-toggle"
      type="button"
      aria-label="Toggle navigation menu"
      aria-expanded={menuOpen}
      on:click={() => (menuOpen = !menuOpen)}
    >
      <span></span>
      <span></span>
      <span></span>
    </button>

    <nav class="main-nav">
      {#each navLinks as link}
        <a href={link.href} on:click={() => (menuOpen = false)}>{link.label}</a>
      {/each}
    </nav>
  </header>

  <main class="page-stack" id="top">
    <section class="hero-panel">
      <div class="hero-topline">
        <span>Mercy Andrea</span>
        <span>Wellness / Beauty / Conscious Living</span>
      </div>
      <div class="hero-art">
        <img class="hero-photo" src={heroImage} alt="Mercy portfolio hero portrait outdoors by a wooden fence" />
        <div class="hero-glow"></div>
        <div class="hero-chip">
          <div class="chip-mark"></div>
          <div>
            <strong>Visual Journal</strong>
            <span>wellness</span>
          </div>
        </div>
        <div class="hero-footer">
          <span>Yoga, somatics, and meditation</span>
          <span>Beauty with conscious living</span>
        </div>
      </div>
    </section>

    <section class="intro-grid line">
      <div class="intro-copy">
        <p class="tag">About</p>
        <h1>Welcome to a sanctuary of wellness, beauty, and mindful living.</h1>
        <p class="muted">
          Mercy is a model and wellness enthusiast dedicated to sharing her passion for holistic
          living through an evolving visual journey. Her work brings together elegance,
          self-expression, and a deeper connection to body, mind, and spirit.
        </p>
      </div>
      <article class="intro-card">
        <div class="intro-thumb">
          <img src={introImage} alt="Mercy standing in a blue dress by a rustic gate" />
        </div>
        <div class="intro-card-copy">
          <span>My Journey</span>
          <p class="muted">Modeling and acting began in her early 20s, later evolving into a deeper exploration of yoga, somatics, and meditation.</p>
        </div>
      </article>
    </section>

    <section class="codes-section line">
      <div class="codes-copy">
        <p class="tag">Shop Favorites</p>
        <h2>Trusted links and codes shared through Mercy’s wellness and beauty routine.</h2>
        <p class="muted">
          A curated list of brands Mercy loves, with direct shopping links and selected discount
          codes where available.
        </p>
      </div>
      <div class="codes-grid">
        {#each partnerLinks as item}
          <article class="code-card">
            <span class="code-kicker">{item.brand}</span>
            <h3>{item.brand}</h3>
            <a class="code-link" href={item.link} target="_blank" rel="noreferrer">{item.link}</a>
            <p class="muted">{item.note}</p>
            {#if item.code}
              <div class="code-badge">Code {item.code}</div>
            {/if}
          </article>
        {/each}
      </div>
    </section>

    <section class="metrics-row line">
      {#each metrics as item}
        <article class="metric-card">
          <strong>{item.value}</strong>
          <span>{item.label}</span>
        </article>
      {/each}
    </section>

    <section class="gallery-section line" id="collections">
      <div class="section-head">
        <div>
          <p class="tag">Visual Journey</p>
          <h2>Images that hold beauty, softness, presence, and self-expression.</h2>
        </div>
      </div>
      <div class="mosaic-grid">
        {#each tiles as tile}
          <article class="mosaic-card">
            <img src={tile.src} alt={tile.title} />
            <span>{tile.title}</span>
          </article>
        {/each}
      </div>
    </section>

    <section class="feature-band">
      <div class="feature-image">
        <img src={featureImage} alt="Mercy wearing a textured knit by a large window" />
      </div>
      <div class="feature-copy">
        <p class="tag light">My Passion</p>
        <h2>Harmony between body, mind, and spirit shapes everything shared here.</h2>
        <p class="muted light-copy">
          Mercy's Instagram reflects this philosophy through healing movement, breath practices,
          meditation, and a holistic approach to beauty that honors both the body and the planet.
        </p>
      </div>
    </section>

    <section class="approach-layout line">
      <div class="approach-copy">
        <p class="tag">Conscious Living</p>
        <h2>Slow fashion, natural beauty, and mindful rituals guide the energy of this space.</h2>
      </div>
      <div class="approach-visual">
        <div class="approach-shot">
          <img src={approachImage} alt="Mercy in black lace seated on a white chair" />
        </div>
        <div class="approach-note">
          <span>Directional</span>
          <p class="muted">Each section is shaped around healing, mindfulness, and a more beautiful, intentional way of living.</p>
        </div>
      </div>
      <div class="workflow-list">
        {#each workflow as item}
          <article class="workflow-card">
            <span>{item[0]}</span>
            <h3>{item[1]}</h3>
            <p class="muted">{item[2]}</p>
          </article>
        {/each}
      </div>
    </section>

    <section class="services-section line">
      <div class="section-head">
        <div>
          <p class="tag">What I Share</p>
          <h2>Practices and values woven through Mercy Andrea's daily wellness journey.</h2>
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

    <section class="plans-layout line" id="plans">
      <div class="plans-copy">
        <p class="tag">Wellness Notes</p>
        <h2>A life that moved from self-expression in front of the camera toward deeper inner alignment.</h2>
        <p class="muted">
          What began in modeling and acting has grown into a practice of yoga, somatics,
          pranayama, meditation, and more conscious choices around beauty and fashion.
        </p>
      </div>
      <article class="plans-card">
        <img class="plans-image" src={planImage} alt="Mercy in red lace standing by a window" />
        <div class="plans-meta">
          <span>Mercy Andrea</span>
          <strong>Holistic Living</strong>
        </div>
        <ul>
          {#each planPoints as point}
            <li>{point}</li>
          {/each}
        </ul>
      </article>
    </section>

    <section class="archive-section line" id="archive">
      <div class="section-head">
        <div>
          <p class="tag">Archive</p>
          <h2>A visual journal of beauty, reflection, softness, and mindful living.</h2>
        </div>
      </div>
      <div class="archive-grid">
        {#each archiveShots as shot}
          <article class:wide-shot={shot.wide} class="archive-card">
            <img src={shot.src} alt={shot.alt} />
          </article>
        {/each}
      </div>
    </section>

    <section class="cta-banner">
      <div class="cta-visual">
        <img src={ctaImage} alt="Black and white silhouette portrait in chair" />
      </div>
      <div class="cta-copy">
        <p class="tag cta-tag">Join The Journey</p>
        <h2>Health, wellness, and conscious beauty can be lived gently.</h2>
        <p class="muted cta-muted">
          Follow along for yoga, somatics, meditation, holistic beauty, and a slower, more mindful way of living.
        </p>
      </div>
    </section>
  </main>

  <footer class="footer-band">
    <div>
      <p>MERCY ANDREA STUDIO</p>
      <span>Wellness, beauty, and conscious living. {currentYear}</span>
    </div>
    <div class="footer-links">
      <a
        href="https://www.instagram.com/mercyandreayoga?igsh=YjJveTIwMmZ6YmI2"
        target="_blank"
        rel="noreferrer"
        aria-label="Instagram"
      >
        <svg viewBox="0 0 24 24" aria-hidden="true">
          <rect x="3" y="3" width="18" height="18" rx="5"></rect>
          <circle cx="12" cy="12" r="4.25"></circle>
          <circle cx="17.5" cy="6.5" r="1.1" class="icon-fill"></circle>
        </svg>
      </a>
      <a href="mailto:mercy@ateliermode.com" aria-label="Email">
        <svg viewBox="0 0 24 24" aria-hidden="true">
          <path d="M3.5 6.5h17v11h-17z"></path>
          <path d="M4.5 7.5 12 13l7.5-5.5"></path>
        </svg>
      </a>
    </div>
  </footer>
</div>

<style>
  .site-shell{width:min(calc(100% - 1.4rem),1080px);margin:0 auto;padding:.75rem 0 2rem;color:var(--text)}
  .mini-top{position:sticky;top:.6rem;z-index:30;display:grid;grid-template-columns:auto 1fr;align-items:center;gap:1rem;padding:.9rem 1rem;margin-bottom:.6rem;border:1px solid transparent;border-radius:1rem;background:transparent;box-shadow:none;transition:background-color .24s ease,border-color .24s ease,box-shadow .24s ease,color .24s ease}
  .brand-wrap{display:grid;gap:.22rem}
  .brand-index{color:rgba(17,17,17,.72);font-size:.56rem;letter-spacing:.16em;text-transform:uppercase;text-shadow:0 1px 0 rgba(255,255,255,.18);transition:color .24s ease,text-shadow .24s ease}
  .brand-name{color:#171717;font-family:var(--display-font);font-size:.86rem;font-weight:600;letter-spacing:.08em;text-transform:uppercase;text-shadow:0 1px 0 rgba(255,255,255,.22);transition:color .24s ease,text-shadow .24s ease}
  .main-nav{display:flex;justify-content:flex-end;align-items:center;gap:.35rem;flex-wrap:wrap}
  .main-nav a{color:#171717;font-family:var(--body-font);padding:.62rem .78rem;border-radius:999px;font-size:.62rem;font-weight:700;letter-spacing:.12em;text-transform:uppercase;text-shadow:0 1px 0 rgba(255,255,255,.18);transition:background-color .22s ease,color .22s ease,transform .22s ease,text-shadow .22s ease}
  .main-nav a:hover{color:#111111;background:rgba(17,17,17,.08);transform:translateY(-1px)}
  .menu-toggle{display:none;justify-self:end;align-items:center;justify-content:center;width:3rem;height:3rem;padding:0;border:1px solid rgba(245,242,236,.16);border-radius:999px;background:transparent;cursor:pointer;transition:background-color .24s ease,border-color .24s ease}
  .menu-toggle span{display:block;width:.3rem;height:.3rem;background:#171717;border-radius:50%;box-shadow:none;transition:transform .22s ease,opacity .22s ease,background-color .24s ease,box-shadow .24s ease}
  .menu-toggle span+span{margin-top:.2rem}
  .menu-open .menu-toggle span:nth-child(1){transform:translateY(.34rem)}
  .menu-open .menu-toggle span:nth-child(2){opacity:.55}
  .menu-open .menu-toggle span:nth-child(3){transform:translateY(-.34rem)}
  .mini-top.scrolled{background:rgba(244,239,231,.76);border-color:rgba(28,24,21,.08);box-shadow:0 16px 34px rgba(17,17,17,.08)}
  .mini-top.scrolled .brand-index{color:rgba(17,17,17,.58);text-shadow:none}
  .mini-top.scrolled .brand-name{color:#171717;text-shadow:none}
  .mini-top.scrolled .main-nav a{color:#221d18;text-shadow:none}
  .mini-top.scrolled .main-nav a:hover{color:#171717;background:rgba(17,17,17,.06)}
  .mini-top.scrolled .menu-toggle{border-color:rgba(17,17,17,.12);background:rgba(255,255,255,.34)}
  .mini-top.scrolled .menu-toggle span{background:#171717;box-shadow:none}
  .page-stack{display:grid;gap:2rem}.line{border-top:1px solid var(--line);padding-top:1.6rem}
  .hero-panel,.intro-grid,.metrics-row,.gallery-section,.feature-band,.approach-layout,.services-section,.plans-layout,.cta-banner,.footer-band{animation:reveal .7s ease both}
  .hero-panel{display:grid;gap:.7rem}.hero-topline{display:flex;justify-content:space-between;gap:1rem;color:rgba(15,15,15,.72);font-size:.58rem;letter-spacing:.14em;text-transform:uppercase}
  .hero-art{position:relative;min-height:clamp(360px,64vw,620px);overflow:hidden;border-radius:.35rem;background:radial-gradient(circle at top left,rgba(255,255,255,.08),transparent 24%),linear-gradient(135deg,#050505 0%,#111111 44%,#1b1b1b 100%);box-shadow:0 30px 80px rgba(0,0,0,.22)}
  .hero-photo{position:absolute;inset:0;width:100%;height:100%;object-fit:cover;object-position:center 24%;filter:saturate(1.02) contrast(1.02)}
  .hero-glow{position:absolute;inset:0;background:linear-gradient(180deg,rgba(0,0,0,.62),rgba(0,0,0,.28) 38%,rgba(0,0,0,.56) 100%),linear-gradient(120deg,rgba(8,8,8,.6) 0%,rgba(8,8,8,.14) 48%,rgba(255,79,163,.1) 100%);pointer-events:none}
  .hero-chip{position:absolute;right:3.6%;top:36%;z-index:2;display:flex;align-items:center;gap:.75rem;padding:.7rem .85rem;border-radius:.35rem;background:rgba(250,244,235,.92);box-shadow:0 14px 40px rgba(0,0,0,.14)}
  .chip-mark{width:1.8rem;height:1.8rem;border-radius:.2rem;background:linear-gradient(90deg,#111 0 12%,transparent 12% 20%,#111 20% 32%,transparent 32% 38%,#111 38% 46%,transparent 46% 100%),linear-gradient(#111 0 14%,transparent 14% 24%,#111 24% 34%,transparent 34% 40%,#111 40% 48%,transparent 48% 100%),#fff;border:1px solid rgba(0,0,0,.12)}
  .hero-chip strong,.hero-chip span{display:block;color:#171717;text-transform:uppercase}.hero-chip strong{font-size:.62rem;letter-spacing:.1em}.hero-chip span{margin-top:.18rem;font-size:.54rem;letter-spacing:.14em;opacity:.6}
  .hero-footer{position:absolute;right:1.2rem;bottom:1rem;left:1.2rem;z-index:2;display:flex;justify-content:space-between;gap:1rem;color:rgba(255,245,235,.86);font-size:.58rem;letter-spacing:.12em;text-transform:uppercase}
  .intro-grid{display:grid;grid-template-columns:minmax(0,1.5fr) minmax(220px,.7fr);gap:1.5rem;align-items:start}
  .tag{margin:0 0 .32rem;padding:0;color:var(--orange-deep);font-family:var(--body-font);font-size:.56rem;font-weight:700;letter-spacing:.18em;text-transform:uppercase}.tag.light{color:#ff9acb}.cta-tag{color:rgba(23,10,2,.72)}
  h1,h2,h3,p{margin:0}.intro-copy{display:grid;gap:1rem}.intro-copy h1{max-width:13ch;font-size:clamp(1.4rem,3vw,2.45rem);line-height:1;letter-spacing:-.03em;text-transform:uppercase}
  .muted{color:var(--muted);line-height:1.6;font-size:.76rem}
  .intro-card{display:grid;gap:.8rem}.intro-thumb{min-height:245px;border-radius:.4rem;position:relative;overflow:hidden;box-shadow:var(--shadow)}.intro-thumb img{width:100%;height:100%;object-fit:cover;object-position:center 24%}
  .intro-card-copy{display:grid;gap:.4rem}.intro-card-copy span,.approach-note span{color:#171717;font-size:.56rem;font-weight:700;letter-spacing:.14em;text-transform:uppercase}
  .codes-section{display:grid;gap:1rem}.codes-copy{display:grid;gap:.8rem;max-width:38rem}.codes-copy h2{max-width:min(100%,30rem);font-size:clamp(1rem,1.8vw,1.5rem);line-height:1.16;letter-spacing:-.03em;text-transform:uppercase}.codes-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:1rem}.code-card{display:grid;gap:.55rem;padding:1.05rem 1rem;border:1px solid var(--line);border-radius:.55rem;background:rgba(255,255,255,.62);box-shadow:0 16px 40px rgba(22,14,10,.05)}.code-kicker{color:var(--orange-deep);font-size:.52rem;font-weight:700;letter-spacing:.16em;text-transform:uppercase}.code-card h3{font-size:1.05rem;line-height:1.05;letter-spacing:-.03em;text-transform:uppercase}.code-link{color:#3e3830;font-size:.74rem;line-height:1.55;word-break:break-word}.code-badge{width:fit-content;padding:.42rem .62rem;border-radius:999px;background:#101010;color:#f5f2ec;font-size:.58rem;font-weight:700;letter-spacing:.12em;text-transform:uppercase}
  .metrics-row{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:1rem}.metric-card{display:grid;gap:.25rem;padding:.3rem 0}.metric-card strong{font-size:clamp(1.25rem,2.2vw,1.95rem);line-height:1;letter-spacing:-.04em}.metric-card span{color:var(--muted);font-size:.66rem;letter-spacing:.04em;text-transform:uppercase}
  .gallery-section{display:grid;gap:1.2rem}.section-head{display:flex;justify-content:space-between;gap:1rem;align-items:end}.section-head h2,.feature-copy h2,.approach-copy h2,.plans-copy h2,.cta-copy h2{max-width:min(100%,30rem);font-size:clamp(1rem,1.8vw,1.5rem);line-height:1.16;letter-spacing:-.03em;text-transform:uppercase}
  .mosaic-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:.9rem}.mosaic-card{position:relative;min-height:clamp(180px,24vw,280px);overflow:hidden;border-radius:.35rem;box-shadow:0 20px 50px rgba(22,14,10,.08);transition:transform .24s ease,box-shadow .24s ease}.mosaic-card:hover{transform:translateY(-4px);box-shadow:0 24px 56px rgba(22,14,10,.14)}.mosaic-card img{width:100%;height:100%;object-fit:cover}.mosaic-card span{position:absolute;left:.8rem;bottom:.8rem;padding:.28rem .42rem;color:#fff;font-size:.52rem;letter-spacing:.12em;text-transform:uppercase;background:rgba(0,0,0,.3);border-radius:999px}
  .feature-band{display:grid;grid-template-columns:minmax(0,.95fr) minmax(0,1.05fr);gap:1.4rem;padding:1.35rem;border-radius:.7rem;background:#0b0b0b;color:#fff}.feature-image{min-height:310px;border-radius:.45rem;position:relative;overflow:hidden}.feature-image img{width:100%;height:100%;object-fit:cover;object-position:center 18%}.feature-image::after{content:'';position:absolute;inset:0;background:linear-gradient(180deg,rgba(0,0,0,.08),rgba(0,0,0,.22))}.feature-copy{display:grid;align-content:center;gap:1rem;padding:.4rem .2rem}.light-copy{color:rgba(255,255,255,.74)}
  .approach-layout{display:grid;grid-template-columns:minmax(0,.75fr) minmax(220px,.55fr) minmax(0,1fr);gap:1.4rem;align-items:start}.approach-copy,.plans-copy{display:grid;gap:.95rem}.approach-shot{min-height:220px;border-radius:.4rem;position:relative;overflow:hidden;box-shadow:var(--shadow)}.approach-shot img{width:100%;height:100%;object-fit:cover;object-position:center 20%}.approach-note{display:grid;gap:.25rem;padding-top:.55rem}.workflow-list{display:grid;gap:1rem}.workflow-card{display:grid;gap:.45rem;padding-bottom:1rem;border-bottom:1px solid var(--line)}.workflow-card:last-child{padding-bottom:0;border-bottom:0}.workflow-card span{color:var(--orange-deep);font-size:.56rem;font-weight:700;letter-spacing:.16em;text-transform:uppercase}.workflow-card h3{font-size:.8rem;letter-spacing:-.01em;text-transform:uppercase}.workflow-card p{font-size:.74rem;line-height:1.5}.service-box h3{font-size:.74rem;letter-spacing:-.01em;text-transform:uppercase}
  .services-section{display:grid;gap:1.1rem}.services-grid{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:1rem}.service-box{display:grid;gap:.75rem;min-height:180px;padding:1rem;border:1px solid var(--line);border-radius:.45rem;background:rgba(255,255,255,.66);transition:transform .22s ease,border-color .22s ease}.service-box img{width:100%;aspect-ratio:4/5;object-fit:cover;border-radius:.3rem}.service-box p{font-size:.74rem;line-height:1.5}.service-box:hover{transform:translateY(-4px);border-color:rgba(255,90,18,.3)}
  .plans-layout{display:grid;grid-template-columns:minmax(0,1.05fr) minmax(280px,.8fr);gap:1.4rem;align-items:start}.plans-card{display:grid;gap:1.15rem;padding:1.2rem;border-radius:.6rem;background:#111;color:#fff;box-shadow:0 30px 60px rgba(17,17,17,.2)}.plans-image{width:100%;aspect-ratio:4/5;object-fit:cover;border-radius:.45rem}.plans-meta{display:grid;gap:.35rem}.plans-meta span{color:rgba(255,255,255,.62);font-size:.58rem;letter-spacing:.14em;text-transform:uppercase}.plans-meta strong{font-size:clamp(1.3rem,2.6vw,1.95rem);line-height:1;letter-spacing:-.04em}.plans-card ul{display:grid;gap:.7rem;margin:0;padding:0;list-style:none}.plans-card li{position:relative;padding-left:1rem;color:rgba(255,255,255,.78);font-size:.76rem;line-height:1.5}.plans-card li::before{content:'';position:absolute;left:0;top:.55rem;width:.38rem;height:.38rem;border-radius:50%;background:#ff4fa3}
  .archive-section{display:grid;gap:1.2rem}.archive-grid{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:1rem}.archive-card{overflow:hidden;border-radius:.45rem;background:#fff;box-shadow:var(--shadow)}.archive-card img{width:100%;height:100%;object-fit:cover}.wide-shot{grid-column:span 2}
  .cta-banner{position:relative;display:grid;grid-template-columns:minmax(260px,.8fr) minmax(0,1fr) auto;align-items:end;gap:1rem;min-height:320px;padding:clamp(1.4rem,4vw,2.2rem);overflow:hidden;border-radius:.75rem;background:radial-gradient(circle at top left,rgba(255,255,255,.08),transparent 24%),linear-gradient(135deg,#050505 0%,#111111 44%,#1b1b1b 100%);box-shadow:0 30px 80px rgba(0,0,0,.24)}.cta-banner::after{content:'';position:absolute;right:5%;top:15%;width:42%;height:3px;background:rgba(255,255,255,.18);transform:rotate(-24deg);box-shadow:0 12px 0 rgba(255,255,255,.12),0 24px 0 rgba(255,255,255,.08)}.cta-visual,.cta-copy{position:relative;z-index:1}.cta-visual{align-self:stretch;overflow:hidden;border-radius:.6rem;box-shadow:0 24px 60px rgba(0,0,0,.35)}.cta-visual img{width:100%;height:100%;object-fit:cover;filter:grayscale(1) contrast(1.05)}.cta-copy h2{font-size:clamp(1.35rem,3.6vw,2.4rem);max-width:none;color:#f5f2ec}.cta-muted{max-width:28rem;color:rgba(255,255,255,.68)}
  .footer-band{display:flex;justify-content:space-between;gap:1rem;margin-top:1.2rem;padding:1.5rem 0 0;border-top:1px solid var(--line)}.footer-band p{margin-bottom:.2rem;font-size:.78rem;font-weight:700;letter-spacing:.12em}.footer-band span{color:var(--muted);font-size:.66rem;letter-spacing:.05em;text-transform:uppercase}.footer-links{display:flex;flex-wrap:wrap;justify-content:flex-end;gap:.7rem}.footer-links a{display:inline-flex;align-items:center;justify-content:center;width:2.3rem;height:2.3rem;border:1px solid rgba(28,24,21,.12);border-radius:999px;color:#241d18;background:rgba(255,255,255,.52);transition:transform .22s ease,border-color .22s ease,color .22s ease}.footer-links a:hover{transform:translateY(-2px);border-color:rgba(255,79,163,.38);color:#ff4fa3}.footer-links svg{width:.9rem;height:.9rem;stroke:currentColor;stroke-width:1.7;fill:none}.footer-links .icon-fill{fill:currentColor;stroke:none}
  @keyframes reveal{from{opacity:0;transform:translateY(18px)}to{opacity:1;transform:translateY(0)}}
  @media (min-width:961px){.plans-layout{grid-template-columns:minmax(0,1.12fr) minmax(260px,.62fr);gap:1.1rem}.plans-card{gap:.9rem;padding:1rem}.plans-image{aspect-ratio:4/4.4;max-height:370px}.plans-copy{max-width:32rem}}
  @media (max-width:960px){.intro-grid,.feature-band,.approach-layout,.plans-layout,.services-grid,.cta-banner{grid-template-columns:1fr}.codes-grid,.services-grid,.archive-grid{grid-template-columns:repeat(2,minmax(0,1fr))}.footer-band{grid-template-columns:1fr;display:grid}.hero-chip{top:auto;right:1rem;bottom:3rem}.cta-visual{max-height:420px}}
  @media (max-width:760px){.mini-top{grid-template-columns:1fr auto;gap:.8rem}.menu-toggle{display:inline-flex}.main-nav{grid-column:1 / -1;display:none;flex-direction:column;align-items:stretch;padding-top:.3rem;border-top:1px solid rgba(221,213,200,.88)}.menu-open .main-nav{display:flex}.main-nav a{padding:.95rem 0;border-radius:0;background:none}.main-nav a:hover{transform:none;color:var(--orange-deep);background:none}}
  @media (max-width:680px){.site-shell{width:min(calc(100% - 1rem),1080px);padding-top:.5rem}.hero-topline,.section-head,.hero-footer,.footer-band{grid-template-columns:1fr;display:grid;gap:.6rem}.codes-grid,.services-grid,.mosaic-grid,.archive-grid,.metrics-row{grid-template-columns:1fr}.hero-chip{position:static;width:fit-content;margin:1rem}.hero-footer{position:static;padding:0 1rem 1rem}.wide-shot{grid-column:auto}.cta-banner{min-height:260px;align-items:start}}
</style>



