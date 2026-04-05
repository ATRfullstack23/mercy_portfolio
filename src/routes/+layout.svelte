<script>
  import { page } from '$app/stores';
  import { onMount } from 'svelte';
  import '../app.css';

  const currentYear = new Date().getFullYear();
  const footerFeatureImage = '/mercy/Screenshot_20260403_122626_Instagram.jpg';
  let menuOpen = false;
  let headerScrolled = false;
  const navLinks = [
    { label: 'Home', href: '/#top' },
    { label: 'Gallery', href: '/#archive' },
    { label: 'Shop', href: '/#shop-favorites' },
    { label: 'About', href: '/#about' },
    { label: 'Contact', href: '/#contact' }
  ];
  const footerNavigate = [
    { label: 'Home', href: '/#top' },
    { label: 'About', href: '/#about' },
    { label: 'Shop', href: '/#shop-favorites' },
    { label: 'Gallery', href: '/#archive' },
    { label: 'Contact', href: '/#contact' }
  ];
  const footerConnect = [
    {
      label: 'Instagram',
      href: 'https://www.instagram.com/mercyandreayoga?igsh=YjJveTIwMmZ6YmI2',
      external: true
    },
    { label: 'Contact', href: '/#contact', external: false }
  ];
  const footerSocial = [
    {
      label: 'Instagram',
      href: 'https://www.instagram.com/mercyandreayoga?igsh=YjJveTIwMmZ6YmI2',
      external: true
    },
    {
      label: 'Email',
      href: 'mailto:mercyfarrell@yahoo.com',
      external: false
    }
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
      <a class="brand-name" href="/#top">Mercy Andrea</a>
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
    {#if $page.url.pathname === '/'}
      <section class="footer-hero">
        <div class="footer-hero-visual">
          <img src={footerFeatureImage} alt="Black and white portrait of Mercy seated in a chair" />
        </div>
        <div class="footer-hero-copy">
          <p class="footer-kicker">Join The Journey</p>
          <h2>Health, wellness, and conscious beauty can be lived gently.</h2>
          <p>
            Follow along for yoga, somatics, meditation, holistic beauty, and a slower, more
            mindful way of living.
          </p>
        </div>
      </section>
    {/if}

    <div class="footer-shell">
      <div class="footer-brand">
        <a class="footer-mark" href="/#top">Mercy Andrea</a>
        <p class="footer-copy">
          Visual journal of wellness, beauty, and conscious living. Available for collaborations,
          campaigns, and partnerships worldwide.
        </p>
      </div>

      <div class="footer-column">
        <p class="footer-label">Navigate</p>
        <div class="footer-stack">
          {#each footerNavigate as item}
            <a class="footer-text-link" href={item.href}>{item.label}</a>
          {/each}
        </div>
      </div>

      <div class="footer-column">
        <p class="footer-label">Connect</p>
        <div class="footer-stack">
          {#each footerConnect as item}
            <a
              class="footer-text-link"
              href={item.href}
              target={item.external ? '_blank' : undefined}
              rel={item.external ? 'noreferrer' : undefined}
            >
              {item.label}
            </a>
          {/each}
        </div>
      </div>

      <div class="footer-column">
        <p class="footer-label">Follow</p>
        <div class="footer-links">
          {#each footerSocial as item}
            <a
              href={item.href}
              target={item.external ? '_blank' : undefined}
              rel={item.external ? 'noreferrer' : undefined}
              aria-label={item.label}
            >
              {#if item.label === 'Instagram'}
                <svg viewBox="0 0 24 24" aria-hidden="true">
                  <rect x="3" y="3" width="18" height="18" rx="5"></rect>
                  <circle cx="12" cy="12" r="4.25"></circle>
                  <circle cx="17.5" cy="6.5" r="1.1" class="icon-fill"></circle>
                </svg>
              {:else}
                <svg viewBox="0 0 24 24" aria-hidden="true">
                  <path d="M3.5 6.5h17v11h-17z"></path>
                  <path d="M4.5 7.5 12 13l7.5-5.5"></path>
                </svg>
              {/if}
            </a>
          {/each}
        </div>
      </div>
    </div>

    <p class="footer-legal">Copyright {currentYear} Mercy Andrea. All rights reserved.</p>
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
  .footer-band{display:grid;gap:2rem;margin-top:1.4rem;padding:clamp(1rem,3vw,1.5rem);border:1px solid var(--ink-edge);border-radius:1rem;background:linear-gradient(180deg,rgba(7,7,7,.99),rgba(4,4,4,.99));color:#f1ece6;box-shadow:0 26px 70px rgba(0,0,0,.26)}
  .footer-hero{display:grid;grid-template-columns:minmax(260px,.82fr) minmax(0,1fr);gap:1.1rem;align-items:end;padding-bottom:.5rem;border-bottom:1px solid var(--ink-line)}
  .footer-hero-visual{min-height:300px;overflow:hidden;border-radius:.8rem;box-shadow:0 24px 60px rgba(0,0,0,.32)}
  .footer-hero-visual img{width:100%;height:100%;object-fit:cover;filter:grayscale(1) contrast(1.05)}
  .footer-hero-copy{display:grid;gap:1rem;padding:clamp(.3rem,2vw,.8rem) 0}
  .footer-kicker{margin:0;color:rgba(255,255,255,.42);font-size:.62rem;font-weight:700;letter-spacing:.24em;text-transform:uppercase}
  .footer-hero-copy h2{margin:0;max-width:12ch;color:#f5f2ec;font-size:clamp(1.3rem,2.6vw,1.85rem);line-height:1.02;letter-spacing:-.03em}
  .footer-hero-copy p{margin:0;max-width:30rem;color:rgba(255,255,255,.68);font-size:.82rem;line-height:1.75}
  .footer-shell{display:grid;grid-template-columns:minmax(0,1.3fr) repeat(3,minmax(140px,.7fr));gap:1.5rem;align-items:start}
  .footer-brand,.footer-column,.footer-stack{display:grid}
  .footer-brand{gap:1rem;max-width:22rem}
  .footer-mark{font-family:var(--display-font);font-size:clamp(1.2rem,2.4vw,1.65rem);letter-spacing:.14em;text-transform:uppercase}
  .footer-copy{color:rgba(255,255,255,.62);font-size:.82rem;line-height:1.75}
  .footer-column{gap:.9rem}
  .footer-label{margin:0;color:rgba(255,255,255,.36);font-size:.64rem;font-weight:700;letter-spacing:.24em;text-transform:uppercase}
  .footer-stack{gap:.8rem}
  .footer-text-link{color:#f3eee8;font-size:.82rem;transition:color .22s ease,transform .22s ease}
  .footer-text-link:hover{color:#ffffff;transform:translateX(3px)}
  .footer-links{display:flex;flex-wrap:wrap;gap:.75rem}
  .footer-links a{display:inline-flex;align-items:center;justify-content:center;width:3rem;height:3rem;border:1px solid rgba(255,255,255,.12);border-radius:999px;color:#f1ece6;background:rgba(255,255,255,.02);transition:transform .22s ease,border-color .22s ease,background-color .22s ease}
  .footer-links a:hover{transform:translateY(-2px);border-color:rgba(255,255,255,.24);background:rgba(255,255,255,.06)}
  .footer-links svg{width:1rem;height:1rem;stroke:currentColor;stroke-width:1.7;fill:none}
  .footer-links .icon-fill{fill:currentColor;stroke:none}
  .footer-legal{margin:0;padding-top:1rem;border-top:1px solid var(--ink-line);color:rgba(255,255,255,.42);font-size:.72rem;text-align:center}
  @media (max-width:760px){.mini-top{grid-template-columns:1fr auto;gap:.8rem}.menu-toggle{display:inline-flex}.main-nav{grid-column:1 / -1;display:none;flex-direction:column;align-items:stretch;padding-top:.3rem;border-top:1px solid rgba(221,213,200,.88)}.menu-open .main-nav{display:flex}.main-nav a{padding:.95rem 0;border-radius:0;background:none}.main-nav a:hover{transform:none;color:var(--orange-deep);background:none}.footer-hero,.footer-shell{grid-template-columns:repeat(2,minmax(0,1fr))}.footer-hero-copy h2{max-width:14ch}}
  @media (max-width:680px){.site-shell{width:min(calc(100% - 1rem),1080px);padding-top:.5rem}.footer-hero,.footer-shell{grid-template-columns:1fr}.footer-band{padding:1rem}.footer-hero-visual{min-height:240px}.footer-copy{font-size:.78rem}.footer-text-link{font-size:.78rem}.footer-legal{text-align:left}}
</style>
