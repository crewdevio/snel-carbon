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
  data-carbon-icon="Road32"
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
  <path d="M13 13H19V15H13z"></path><path d="M25.4409 8L24.1687 3.45A2.009 2.009 0 0022.2456 2H9.7544A2.0089 2.0089 0 007.8313 3.4507L6.5315 8H4v2H6v7a2.0025 2.0025 0 002 2v3h2V19H22v3h2V19a2.0025 2.0025 0 002-2V10h2V8zM9.7544 4H22.2458l1.4285 5H8.3257zM24 13H22v2h2v2H8V15h2V13H8V11H24zM2 16H4V30H2zM28 16H30V30H28z"></path><path d="M15 21H17V24H15zM15 26H17V30H15z"></path>
  <slot>
    {#if title}
      <title>{title}</title>
    {/if}
  </slot>
</svg>