<script lang="ts">
  import { tick } from "svelte";

  export let heading = "";
  export let headingLevel = "2";
  let active = false;

  let modal: HTMLDivElement;

  const headingProps = {
    id: "dialog1_label",
    class: "dialog_label",
  };

  export const toggle = async () => {
    active = !active;
    await tick();

    modal && modal.focus();
  };
</script>

<div
  style:display={active ? "block" : "none"}
  id="dialog_layer"
  class="dialogs"
>
  <div
    bind:this={modal}
    role="dialog"
    id="dialog1"
    aria-labelledby="dialog1_label"
    aria-modal="true"
    class="hidden"
  >
    <button on:click={toggle}>Close</button>
    {#if heading}
      {#if headingLevel === "1"}
        <h1 {...headingProps}>
          {heading}
        </h1>
      {:else if headingLevel === "2"}
        <h2 {...headingProps}>
          {heading}
        </h2>
      {:else if headingLevel === "3"}
        <h3 {...headingProps}>
          {heading}
        </h3>
      {:else if headingLevel === "4"}
        <h4 {...headingProps}>
          {heading}
        </h4>
      {:else if headingLevel === "5"}
        <h5 {...headingProps}>
          {heading}
        </h5>
      {:else if headingLevel === "6"}
        <h6 {...headingProps}>
          {heading}
        </h6>
      {/if}
    {/if}

    <slot />
  </div>
</div>
