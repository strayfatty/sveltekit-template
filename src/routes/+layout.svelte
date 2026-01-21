<script lang="ts">
  import './layout.css';
  import favicon from '$lib/assets/favicon.ico';
  import * as Sidebar from '$lib/components/ui/sidebar';
  import AppSidebar from '$lib/components/app-sidebar.svelte';
  import Header from '$lib/components/header.svelte';

	let { children } = $props();
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<Sidebar.Provider>
  <AppSidebar />
  <main class="w-full">
    <Header />
    {@render children()}
  </main>
</Sidebar.Provider>
