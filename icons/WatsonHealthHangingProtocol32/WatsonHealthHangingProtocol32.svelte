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
  data-carbon-icon="WatsonHealthHangingProtocol32"
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
  <path d="M26.37,20.52,17,15.41V13.86A4,4,0,1,0,12,10h2a2,2,0,1,1,4,.34A2.08,2.08,0,0,1,15.89,12h0a.89.89,0,0,0-.89.89v2.52L5.63,20.52A3.1,3.1,0,0,0,4.25,22a2.83,2.83,0,0,0,2.56,4H25.19a2.83,2.83,0,0,0,2.56-4A3.1,3.1,0,0,0,26.37,20.52ZM25.19,24H6.81A.81.81,0,0,1,6,23.19a1,1,0,0,1,.52-.88L16,17.14l9.48,5.17a1,1,0,0,1,.52.88A.81.81,0,0,1,25.19,24Z"></path>
  <slot>
    {#if title}
      <title>{title}</title>
    {/if}
  </slot>
</svg>