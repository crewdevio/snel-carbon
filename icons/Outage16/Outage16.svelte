<script>
  let className = undefined;
  export { className as class };
  export let id = undefined;
  export let tabindex = undefined;
  export let focusable = false;
  export let title = undefined;
  export let style = undefined;

  $: ariaLabel = $$props['aria-label'];
  $: ariaLabelledBy = $$props['aria-labelledby'];
  $: labelled = ariaLabel || ariaLabelledBy || title;
  $: attributes = {
    'aria-label': ariaLabel,
    'aria-labelledby': ariaLabelledBy,
    'aria-hidden': labelled ? undefined : true,
    role: labelled ? 'img' : undefined,
    focusable: tabindex === '0' ? true : focusable,
    tabindex
  };
</script>

<svg
  data-carbon-icon="Outage16"
  on:click
  on:mouseover
  on:mouseenter
  on:mouseleave
  on:keyup
  on:keydown
  xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32" fill="currentColor" width="16" height="16"
  class={className}
  preserveAspectRatio="xMidYMid meet"
  {style}
  {id}
  {...attributes}>
  <path d="M12 24H21V26H12zM13 28H19V30H13z"></path><path d="M8.7832 18.9746l1.4177-1.418A6.9206 6.9206 0 018 12 7.99 7.99 0 0121.5273 6.2305l1.4136-1.4136A9.9884 9.9884 0 006 12 8.9411 8.9411 0 008.7832 18.9746zM30 3.4141L28.5859 2 2 28.5859 3.4141 30 23.6606 9.7534A7.7069 7.7069 0 0124 12a7.2032 7.2032 0 01-2.8223 6.1426C20.1069 19.1348 19 20.1611 19 22h2c0-.9194.5264-1.45 1.5352-2.3857A9.193 9.193 0 0026 12a9.8739 9.8739 0 00-.7764-3.81z"></path>
  <slot>
    {#if title}
      <title>{title}</title>
    {/if}
  </slot>
</svg>