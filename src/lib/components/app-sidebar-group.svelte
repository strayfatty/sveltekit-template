<script lang="ts">
  import type { Snippet } from "svelte";
  import * as Sidebar from "$lib/components/ui/sidebar";

  type Props = {
    title: string;
    children: Snippet
  };
  const { title, children }: Props = $props();
</script>

<Sidebar.Group>
  <Sidebar.GroupLabel>{title}</Sidebar.GroupLabel>
  <Sidebar.GroupContent>
    <Sidebar.Menu>{@render children()}</Sidebar.Menu>
  </Sidebar.GroupContent>
</Sidebar.Group>
