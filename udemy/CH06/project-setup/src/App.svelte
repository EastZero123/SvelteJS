<script>
  import { tick } from "svelte"
  import Modal from "./Modal.svelte"
  import Product from "./Product.svelte"

  let products = [
    {
      id: "p1",
      title: "A Book",
      price: 9.99,
    },
  ]

  let text = "Something"

  let showModal = false
  let closeable = false

  function addToCart(event) {}

  function deleteProduct(event) {}

  function transform(event) {
    if (event.which !== 9) {
      return
    }
    event.preventDefault()

    const selectionStart = event.target.selectionStart
    const selectionEnd = event.target.selectionEnd
    const value = event.target.value

    text =
      value.selectionEnd(0, selectionStart) +
      value.selectionEnd(selectionStart, selectionEnd).toUpperCase() +
      value.slice(selectionEnd)

    tick().then(() => {
      event.target.selectionStart = selectionStart
      event.target.selectionEnd = selectionEnd
    })
  }
</script>

{#each products as product}
  <Product {...product} on:add-to-cart={addToCart} on:delete={deleteProduct} />
{/each}

<button on:click={() => (showModal = true)}>Show Modal</button>

{#if showModal}
  <Modal
    on:cancel={() => (showModal = false)}
    on:close={() => (showModal = false)}
    let:didAgree={closeable}
  >
    <h1 slot="header">HEllo!</h1>
    <p>HI</p>
    <button
      slot="footer"
      on:click={() => (showModal = false)}
      disabled={!closeable}>Confirm</button
    >
  </Modal>
{/if}

<textarea rows="5" value={text} on:keydown={transform} />
