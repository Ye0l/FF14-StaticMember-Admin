<script>
  import 'bootstrap/dist/css/bootstrap.min.css';
  import { browser } from '$app/environment';
  import { onMount } from 'svelte';

  onMount(() => {
    if(browser) {
      import('bootstrap/dist/js/bootstrap.bundle.min.js');
    }
  })
</script>

<slot />