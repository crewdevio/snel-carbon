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
  data-carbon-icon="UvIndexAlt24"
  on:click
  on:mouseover
  on:mouseenter
  on:mouseleave
  on:keyup
  on:keydown
  xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32" fill="currentColor" width="24" height="24"
  class={className}
  preserveAspectRatio="xMidYMid meet"
  {style}
  {id}
  {...attributes}>
  <path d="M13 30H9a2.0027 2.0027 0 01-2-2V20H9v8h4V20h2v8A2.0027 2.0027 0 0113 30zM25 20L23.25 20 21 29.031 18.792 20 17 20 19.5 30 22.5 30 25 20zM15 2H17V7H15z"></path><path d="M21.668 6.854H26.625999999999998V8.854H21.668z" transform="rotate(-45 24.147 7.853)"></path><path d="M25 15H30V17H25zM2 15H7V17H2z"></path><path d="M6.854 5.375H8.854V10.333H6.854z" transform="rotate(-45 7.854 7.853)"></path><path d="M22,17H20V16a4,4,0,0,0-8,0v1H10V16a6,6,0,0,1,12,0Z"></path>
  <slot>
    {#if title}
      <title>{title}</title>
    {/if}
  </slot>
</svg>