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
  data-carbon-icon="CenterSquare20"
  on:click
  on:mouseover
  on:mouseenter
  on:mouseleave
  on:keyup
  on:keydown
  xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32" fill="currentColor" width="20" height="20"
  class={className}
  preserveAspectRatio="xMidYMid meet"
  {style}
  {id}
  {...attributes}>
  <path d="M6 12L4 12 4 4 12 4 12 6 6 6 6 12zM28 12L26 12 26 6 20 6 20 4 28 4 28 12zM12 28L4 28 4 20 6 20 6 26 12 26 12 28zM28 28L20 28 20 26 26 26 26 20 28 20 28 28zM15 10H17V14H15zM10 15H14V17H10zM18 15H22V17H18zM15 18H17V22H15z"></path>
  <slot>
    {#if title}
      <title>{title}</title>
    {/if}
  </slot>
</svg>