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
  data-carbon-icon="Interactions32"
  on:click
  on:mouseover
  on:mouseenter
  on:mouseleave
  on:keyup
  on:keydown
  xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32" fill="currentColor" width="32" height="32"
  class={className}
  preserveAspectRatio="xMidYMid meet"
  {style}
  {id}
  {...attributes}>
  <path d="M26 18H22V14H20V28h6a2.0027 2.0027 0 002-2V20A2.0023 2.0023 0 0026 18zm-4 8V20h4v6zM20 6.076L19.256 4.219 16 5.522 16 2 14 2 14 5.523 10.744 4.22 10 6.077 13.417 7.444 10.9 10.8 12.5 12 15 8.667 17.5 12 19.1 10.8 16.583 7.443 20 6.076zM10 18H5v2h5v2H6a2 2 0 00-2 2v2a2 2 0 002 2h6V20A2.0023 2.0023 0 0010 18zm0 8H6V24h4z"></path>
  <slot>
    {#if title}
      <title>{title}</title>
    {/if}
  </slot>
</svg>