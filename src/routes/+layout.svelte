<script>
  import 'bootstrap/dist/css/bootstrap.min.css';
  import { browser } from '$app/environment';
  import { onMount } from 'svelte';

  let isOpen = false;

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
    <a class="navbar-brand" href="#">KSTR</a>
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
        <li class="nav-item">
          <a class="nav-link active" aria-current="page" href="#">Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Features</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Pricing</a>
        </li>
        <!-- <li class="nav-item">
          <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">Disabled</a>
        </li> -->
      </ul>
    </div>
  </div>
</nav>

<slot />