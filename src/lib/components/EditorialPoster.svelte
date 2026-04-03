<script>
  export let src = '';
  export let alt = '';
  export let label = '';
  export let title = '';
  export let meta = '';
  export let ratio = 'portrait';
</script>

<figure class={`poster ${ratio}`}>
  <div class="image-wrap">
    <img src={src} alt={alt} loading="lazy" />
  </div>
  <figcaption>
    {#if label}
      <span>{label}</span>
    {/if}
    <h3>{title}</h3>
    <p>{meta}</p>
  </figcaption>
</figure>

<style>
  .poster {
    display: grid;
    gap: 1rem;
    padding: 1rem;
    border: 1px solid var(--border);
    border-radius: 2rem;
    background: linear-gradient(180deg, rgba(255, 255, 255, 0.06), rgba(255, 255, 255, 0.03));
    box-shadow: var(--shadow);
    backdrop-filter: var(--blur);
    overflow: hidden;
    transform: translateY(0);
    transition:
      transform 260ms ease,
      border-color 260ms ease,
      box-shadow 260ms ease;
  }

  .poster:hover {
    transform: translateY(-8px);
    border-color: rgba(255, 120, 196, 0.35);
    box-shadow: 0 28px 90px rgba(0, 0, 0, 0.6);
  }

  .image-wrap {
    overflow: hidden;
    border-radius: 1.5rem;
    background: rgba(255, 255, 255, 0.03);
  }

  .portrait .image-wrap {
    aspect-ratio: 4 / 5;
  }

  .landscape .image-wrap {
    aspect-ratio: 16 / 10;
  }

  img {
    height: 100%;
    object-fit: cover;
    transition: transform 450ms ease;
  }

  .poster:hover img {
    transform: scale(1.04);
  }

  figcaption {
    display: grid;
    gap: 0.45rem;
    padding-inline: 0.2rem;
  }

  span {
    color: var(--highlight);
    font-size: 0.72rem;
    letter-spacing: 0.24em;
    text-transform: uppercase;
  }

  h3 {
    margin: 0;
    font-family: var(--serif);
    font-size: clamp(1.15rem, 2vw, 1.6rem);
    font-weight: 400;
  }

  p {
    margin: 0;
    color: var(--muted);
    line-height: 1.65;
  }
</style>
