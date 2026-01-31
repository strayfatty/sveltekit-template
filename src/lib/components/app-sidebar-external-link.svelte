<script lang="ts">
  import * as Sidebar from "$lib/components/ui/sidebar";
  import { ExternalLink } from "@lucide/svelte";

  type Props = {
    title: string;
    href: string;
  };
  const { title, href }: Props = $props();
</script>

<Sidebar.MenuItem>
  <Sidebar.MenuButton>
    {#snippet child({ props })}
      <a href={href} target="_blank" rel="noopener noreferrer nofollow"
        aria-label={`${title} (opens in new window)`} {...props}>
        <span class="flex items-center gap-1">
          {title}
          <ExternalLink class="size-[0.8rem]" />
        </span>
      </a>
    {/snippet}
  </Sidebar.MenuButton>
</Sidebar.MenuItem>
