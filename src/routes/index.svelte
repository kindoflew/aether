<script context="module">
  export const prerender = true;
</script>

<script>
  import { onMount } from 'svelte';
  import { fly } from 'svelte/transition';
  import '@fontsource/goldman';

  let mounted = false;
  let entering = true;
  let hovering = false;

  onMount(() => {
    mounted = true;

    setTimeout(() => {
      entering = false;
    }, 2800);
  });
</script>

<svelte:head>
  <title>Aether Unmanned Aerial Operations</title>
  <meta name="description" content="Aether Operations provides aerial photography and videography using state-of-the-art drone technology. Servicing the needs of any industry including real estate, geospatial, entertainment, and live events.">
  <meta property="og:image" content="aether-logo.png">
  <meta property="og:title" content="Aether Unmanned Aerial Operations">
  <meta property="og:description" content="Providing unmanned aerial photography and videography.">
</svelte:head>

<section>
  <div class="flex-item">
    {#if mounted}
      <div in:fly={{ x: -1000, duration: 3500 }} on:introend={() => (hovering = true)}>
        <img src="aether-logo.png" alt="Aether Logo" class:entering class:hovering />
      </div>
    {/if}
  </div>
  <div class="flex-item">
      <div class="copy-wrapper">
        <h1 class:show-text={hovering}>Aether Unmanned Aerial Operations</h1>
        <p class:show-text={hovering}>Website coming soon.</p>
        <p class:show-text={hovering}>
          Contact us at <a href="mailto:info@aetheroperations.com">info@aetheroperations.com</a>.
        </p>
      </div>
  </div>
</section>

<style>
  section {
    min-height: 19rem;
  }

  section,
  .copy-wrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .flex-item {
    flex: 1 0;
  }

  h1,
  p {
    color: white;
    opacity: 0;
    transition: opacity 1s ease-in;
  }

  .show-text {
    opacity: 1;
  }

  h1 {
    font-family: 'Goldman';
    font-size: 2.5rem;
    text-align: center;
  }

  p {
    margin: 0.5rem;
  }

  img {
    transition: transform 0.5s linear;
  }

  .entering {
    transform: rotate(8deg);
  }

  .hovering {
    animation: 3s infinite hover;
  }

  @keyframes hover {
    from,
    to {
      transform: translate3d(0, 0, 0);
    }
    50% {
      transform: translate3d(0, 0.5rem, 0);
    }
  }

  a {
    color: #7fb6c9;
    text-decoration: none;
  }

  a:hover {
    text-decoration: underline;
  }

  @media (max-width: 500px) {
    h1 {
      font-size: 2rem;
    }
  }
</style>
