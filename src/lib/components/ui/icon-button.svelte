<script lang="ts" module>
  export type Props = {
    url: string;
    title: string;
    disabled?: boolean;
    onclick: (event: MouseEvent) => void;
  };
</script>

<script lang="ts">
  const { url, title, disabled, onclick }: Props = $props();
</script>

<button type="button" class="icon-button" onclick={onclick} disabled={disabled} aria-label={title}>
  <svg>
    <title>{title}</title>
    <use href={url} />
  </svg>
</button>
