<script>
  import 'bootstrap/dist/css/bootstrap.min.css';
  import { browser } from '$app/environment';
  import { onMount } from 'svelte';
  import { page } from '$app/state';

  let isOpen = false;

  const menus = [
    {url: '/', text: 'Home'},
    {url: '/members', text: 'Members'},
    {url: '/timeline', text: 'Timeline'}
  ]

  function toggleNavbar() {
    isOpen = !isOpen;
  }

  onMount(() => {
    if(browser) {
      import('bootstrap/dist/js/bootstrap.bundle.min.js');
    }
  })
</script>

<nav class="navbar navbar-expand-lg">
  <div class="container-fluid">
    <a class="navbar-brand" href="/">KSTR</a>
    <button
      class="navbar-toggler"
      type="button"
      aria-controls="navbarNav"
      aria-expanded={isOpen}
      aria-label="Toggle navigation"
      on:click={toggleNavbar}
    >
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class={`collapse navbar-collapse ${isOpen ? 'show' : ''}`} id="navbarNav">
      <ul class="navbar-nav">
        {#each menus as menu}
        <li class="nav-item">
          <a class="nav-link {page.url.pathname === menu.url ? 'active' : ''}"
          aria-current={page.url.pathname === menu.url ? 'page' : undefined}
          href="{menu.url}">{menu.text}</a>
        </li>
        {/each}
        <!-- <li class="nav-item">
          <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">Disabled</a>
        </li> -->
      </ul>
    </div>
  </div>
</nav>

<slot />