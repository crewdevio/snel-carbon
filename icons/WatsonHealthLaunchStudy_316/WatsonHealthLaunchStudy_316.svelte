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
  data-carbon-icon="WatsonHealthLaunchStudy_316"
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
  <circle cx="23" cy="25" r="1"></circle><path d="M26 22v6H6V22H26m0-2H6a2 2 0 00-2 2v6a2 2 0 002 2H26a2 2 0 002-2V22a2 2 0 00-2-2zM20.59 4.59L17 8.17 17 0 15 0 15 8.17 11.41 4.59 10 6 16 12 22 6 20.59 4.59z"></path><path d="M20.59 10.59L16 15.16 11.41 10.59 10 12 16 18 22 12 20.59 10.59zM8 24H20V26H8z"></path>
  <slot>
    {#if title}
      <title>{title}</title>
    {/if}
  </slot>
</svg>