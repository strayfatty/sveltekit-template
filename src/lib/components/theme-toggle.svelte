<script lang="ts">
  import { Moon, Sun } from "@lucide/svelte";
  import { onMount } from "svelte";

  let darkMode = $state(false);

  onMount(() => {
    // Initialize based on current document state (set by blocking script in app.html)
    darkMode = document.documentElement.classList.contains('dark');

    // Listen for system preference changes
    const mediaQuery = window.matchMedia('(prefers-color-scheme: dark)');
    
    function handleSystemThemeChange(e: MediaQueryListEvent) {
      // Only follow system changes if user hasn't set an explicit preference
      if (!localStorage.getItem('theme')) {
        darkMode = e.matches;
        applyTheme(darkMode ? 'dark' : 'light');
      }
    }

    mediaQuery.addEventListener('change', handleSystemThemeChange);

    return () => {
      mediaQuery.removeEventListener('change', handleSystemThemeChange);
    };
  });

  function toggleTheme() {
    darkMode = !darkMode;
    const theme = darkMode ? 'dark' : 'light';
    localStorage.setItem('theme', theme);
    applyTheme(theme);
  }

  function applyTheme(theme: 'light' | 'dark') {
    document.documentElement.classList.remove('light', 'dark');
    document.documentElement.classList.add(theme);
    document.documentElement.style.colorScheme = theme;
  }
</script>

<svelte:head>
  <script>
    (() => {
      const stored = localStorage.getItem('theme');
      const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
      if (stored === 'dark' || (!stored && prefersDark)) {
        document.documentElement.classList.add('dark');
        document.documentElement.style.colorScheme = 'dark';
      } else {
        document.documentElement.style.colorScheme = 'light';
      }
    })();
  </script>
</svelte:head>

<button
  type="button"
  class="relative inline-flex h-9 w-9 items-center justify-center rounded-md font-medium text-sm ring-offset-background transition-colors hover:bg-accent hover:text-accent-foreground focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50"
  onclick={toggleTheme}
>
  <Sun class="h-6 w-6 rotate-0 scale-100 transition-all dark:-rotate-90 dark:scale-0" />
  <Moon class="absolute h-6 w-6 rotate-90 scale-0 transition-all dark:rotate-0 dark:scale-100" />
</button>
