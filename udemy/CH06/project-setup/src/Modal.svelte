<script>
  import { createEventDispatcher, onMount, onDestroy } from "svelte"

  const dispatch = createEventDispatcher()

  let agreed = false
  let autoscroll = false

  onMount(() => {})

  onDestroy(() => {})
</script>

<div class="backdrop" on:click={() => dispatch("cancel")} />
<div class="modal">
  <header>
    <slot name="header" />
  </header>
  <div class="content">
    <slot name="content" />
  </div>
  <div class="disclaimer">
    <p>agree to your terms</p>
    <button on:click={() => (agreed = true)}>Agree</button>
  </div>
  <footer>
    <slot name="footer" didAgree={agreed}>
      <button on:click={() => dispatch("close")} disabled={!agreed}
        >Close</button
      >
    </slot>
  </footer>
</div>

<style>
  .backdrop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background: rgba(0, 0, 0, 0.75);
    z-index: 10;
  }

  .modal {
    padding: 1rem;
    position: fixed;
    top: 10vh;
    left: 10%;
    width: 80%;
    max-height: 15vh;
    background: white;
    border-radius: 5px;
    z-index: 100;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    overflow: scroll;
  }
</style>
