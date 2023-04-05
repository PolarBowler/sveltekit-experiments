<script lang="ts">
  import { Modal } from "$lib/index";

  let modal: Modal;
</script>

<button on:click={() => modal.toggle()}>Modal</button>

<Modal bind:this={modal} heading="Test">
  <p>Content</p>
</Modal>
