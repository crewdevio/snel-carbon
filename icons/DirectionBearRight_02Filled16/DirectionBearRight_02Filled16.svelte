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
  data-carbon-icon="DirectionBearRight_02Filled16"
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
  <path d="M28,2H4A2,2,0,0,0,2,4V28a2,2,0,0,0,2,2H28a2,2,0,0,0,2-2V4A2,2,0,0,0,28,2ZM6,7.4141,7.4141,6,14,12.5859,12.5859,14ZM26,16H24V9.4141L17.4644,15.95A4.9683,4.9683,0,0,0,16,19.4854V26H14V19.4854a6.954,6.954,0,0,1,2.05-4.95L22.5859,8H16V6H26Z"></path><path fill="none" d="M26,6V16H24V9.4141L17.4644,15.95A4.9683,4.9683,0,0,0,16,19.4854V26H14V19.4854a6.954,6.954,0,0,1,2.05-4.95L22.5859,8H16V6ZM14,12.5859,7.4141,6,6,7.4141,12.5859,14Z" data-icon-path="inner-path"></path>
  <slot>
    {#if title}
      <title>{title}</title>
    {/if}
  </slot>
</svg>