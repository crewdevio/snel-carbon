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
  data-carbon-icon="CabinCareAlert20"
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
  <path d="M24 2H26V9H24z"></path><rect width="3" height="3" x="23.5" y="11" rx="1.5"></rect><path d="M23.8218,18H15.083L11.8643,5.9653a4,4,0,0,0-7.7276,2.07L8.5454,24.5168A2,2,0,0,0,10.4775,26H19v2H4v2H19a2,2,0,0,0,2-2V26h3a4.0046,4.0046,0,0,0,3.98-4.4A4.1215,4.1215,0,0,0,23.8218,18ZM24,24H10.4775L6.0686,7.5181A2,2,0,1,1,9.9324,6.4829L13.5466,20H24a2,2,0,0,1,0,4Z"></path>
  <slot>
    {#if title}
      <title>{title}</title>
    {/if}
  </slot>
</svg>