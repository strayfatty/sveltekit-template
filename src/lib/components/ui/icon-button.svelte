<script lang="ts">
  type Props = {
    url: string;
    title: string;
    disabled?: boolean;
    onclick: () => void;
  };
  const { url, title, disabled, onclick }: Props = $props();
</script>

<button type="button" class="icon-button" onclick={onclick} disabled={disabled} aria-label={title}>
  <svg>
    <title>{title}</title>
    <use href={url} />
  </svg>
</button>
