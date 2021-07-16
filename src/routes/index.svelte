<script context="module">
  export const prerender = true;
</script>

<script>
  import { onMount } from 'svelte';
  import { fly, fade } from 'svelte/transition';
  import '@fontsource/goldman';

  let mounted = false;
  let entering = true;
  let hovering = false;

  onMount(() => {
    mounted = true;

    setTimeout(() => {
      entering = false;
    }, 3000);
  });
</script>

<svelte:head>
  <title>Aether Unmanned Aerial Operations</title>
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
    {#if hovering}
      <div in:fade class="copy-wrapper">
        <h1>Aether Unmanned Aerial Operations</h1>
        <p>Website coming soon.</p>
        <p>
          Contact us at <a href="mailto:info@aether.com">info@aether.com</a>.
        </p>
      </div>
    {/if}
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
  }

  h1 {
    font-family: 'Goldman';
    font-size: 2.5rem;
    margin-bottom: 0 0 1em 0;
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
