<script lang="ts">
  import favicon from '$lib/assets/favicon.ico';
  import AppSidebarExternalLink from '$lib/components/app-sidebar-external-link.svelte';
  import AppSidebarGroup from '$lib/components/app-sidebar-group.svelte';
  import AppSidebarLink from '$lib/components/app-sidebar-link.svelte';
  import * as Sidebar from "$lib/components/ui/sidebar";
</script>

<Sidebar.Root>
  <Sidebar.Header>
    <a class="flex h-[36px] items-center gap-2 pl-2 font-bold text-zinc-900 dark:text-white" href="/">
      <img class="h-6 w-6 self-center" src={favicon} alt="App icon" />
      <span>Home</span>
    </a>
  </Sidebar.Header>
  <Sidebar.Content>
    <AppSidebarGroup title="App Links">
      <AppSidebarLink href="/link1" title="Link 1" />
      <AppSidebarLink href="/link2" title="Link 2" />
      <AppSidebarLink href="/link3" title="Link 3" />
    </AppSidebarGroup>
    <AppSidebarGroup title="External Links">
      <AppSidebarExternalLink href="https://svelte.dev/" title="Svelte" />
      <AppSidebarExternalLink href="https://shadcn-svelte.com/" title="shadcn-svelte" />
    </AppSidebarGroup>
  </Sidebar.Content>
</Sidebar.Root>
