<script>
  export let eyebrow = '';
  export let title = '';
  export let copy = '';
  export let align = 'left';
</script>

<div class={`section-heading ${align}`}>
  {#if eyebrow}
    <p class="eyebrow">{eyebrow}</p>
  {/if}
  <h2>{title}</h2>
  {#if copy}
    <p class="copy">{copy}</p>
  {/if}
</div>

<style>
  .section-heading {
    display: grid;
    gap: 1rem;
    max-width: 40rem;
    animation: rise 900ms ease both;
  }

  .section-heading.center {
    margin-inline: auto;
    text-align: center;
  }

  .eyebrow {
    margin: 0;
    color: var(--highlight);
    font-size: 0.8rem;
    letter-spacing: 0.34em;
    text-transform: uppercase;
  }

  h2 {
    margin: 0;
    font-family: var(--serif);
    font-size: clamp(2rem, 5vw, 4rem);
    line-height: 0.95;
    letter-spacing: -0.04em;
  }

  .copy {
    margin: 0;
    color: var(--muted);
    font-size: 1rem;
    line-height: 1.8;
    max-width: 34rem;
  }

  @keyframes rise {
    from {
      opacity: 0;
      transform: translateY(18px);
    }

    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
</style>
