<script lang="ts">
  import { page } from "$app/state";
  import * as Sidebar from "$lib/components/ui/sidebar";
  import { useSidebar } from "$lib/components/ui/sidebar";

  type Props = {
    title: string;
    href: string;
  };
  const { title, href }: Props = $props();

  const sidebar = useSidebar();

  function handleClick() {
    if (sidebar.isMobile) {
      sidebar.setOpenMobile(false);
    }
  }
</script>

<Sidebar.MenuItem>
  <Sidebar.MenuButton isActive={page.url.pathname === href}>
    {#snippet child({ props })}
      <a href={href} onclick={handleClick} {...props}>{title}</a>
    {/snippet}
  </Sidebar.MenuButton>
</Sidebar.MenuItem>
