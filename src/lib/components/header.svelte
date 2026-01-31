<script lang="ts">
  import ThemeToggle from "$lib/components/theme-toggle.svelte";
  import * as Sidebar from "$lib/components/ui/sidebar";
</script>

<header class="flex justify-between border-zinc-900/10 border-b py-2 pr-6 pl-1 dark:border-white/10">
  <Sidebar.Trigger class="size-9" />
  <div class="flex gap-4">
    <a
      href="https://github.com/strayfatty/sveltekit-template"
      target="_blank"
      class="py-[6px] dark:fill-white"
      rel="noopener noreferrer"
    >
      <svg class="size-[24px]">
        <title>GitHub</title>
        <use href="/github.svg#github" />
      </svg>
    </a>
    <ThemeToggle />
  </div>
</header>
