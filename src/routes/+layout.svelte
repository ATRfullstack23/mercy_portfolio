<script>
  import { onMount } from 'svelte';
  import '../app.css';

  const currentYear = new Date().getFullYear();
  let menuOpen = false;
  let headerScrolled = false;
  const navLinks = [
    { label: 'Home', href: '#top' },
    { label: 'Gallery', href: '#archive' },
    { label: 'Shop', href: '#shop-favorites' },
    { label: 'About', href: '#about' },
    { label: 'Contact', href: '#contact' }
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

  <slot />

  <footer class="footer-band" id="contact">
    <div>
      <p>CONTACT</p>
      <span>Mercy Andrea Studio. Wellness, beauty, and conscious living. {currentYear}</span>
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
      <a href="mailto:mercyfarrell@yahoo.com" aria-label="Email">
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
  .footer-band{display:flex;justify-content:space-between;gap:1rem;margin-top:1.2rem;padding:1.5rem 0 0;border-top:1px solid var(--line)}
  .footer-band p{margin-bottom:.2rem;font-size:.78rem;font-weight:700;letter-spacing:.12em}
  .footer-band span{color:var(--muted);font-size:.66rem;letter-spacing:.05em;text-transform:uppercase}
  .footer-links{display:flex;flex-wrap:wrap;justify-content:flex-end;gap:.7rem}
  .footer-links a{display:inline-flex;align-items:center;justify-content:center;width:2.3rem;height:2.3rem;border:1px solid rgba(28,24,21,.12);border-radius:999px;color:#241d18;background:rgba(255,255,255,.52);transition:transform .22s ease,border-color .22s ease,color .22s ease}
  .footer-links a:hover{transform:translateY(-2px);border-color:rgba(255,79,163,.38);color:#ff4fa3}
  .footer-links svg{width:.9rem;height:.9rem;stroke:currentColor;stroke-width:1.7;fill:none}
  .footer-links .icon-fill{fill:currentColor;stroke:none}
  @media (max-width:760px){.mini-top{grid-template-columns:1fr auto;gap:.8rem}.menu-toggle{display:inline-flex}.main-nav{grid-column:1 / -1;display:none;flex-direction:column;align-items:stretch;padding-top:.3rem;border-top:1px solid rgba(221,213,200,.88)}.menu-open .main-nav{display:flex}.main-nav a{padding:.95rem 0;border-radius:0;background:none}.main-nav a:hover{transform:none;color:var(--orange-deep);background:none}}
  @media (max-width:680px){.site-shell{width:min(calc(100% - 1rem),1080px);padding-top:.5rem}.footer-band{grid-template-columns:1fr;display:grid}}
</style>
