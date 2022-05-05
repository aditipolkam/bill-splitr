<script>
  export let selected_people;
  let itemname = "";
  let itemamount = "";
  let itemquantity = "";
  let itemgst = "";
  function addItem() {
    console.log(selected_people);
  }
</script>

<input
  type="text"
  placeholder="Item Name"
  name="item"
  id="item"
  bind:value={itemname}
  required
/>
<input
  type="number"
  placeholder="Amount for 1 unit"
  name="amount"
  id="amount"
  bind:value={itemamount}
  required
/>
<input
  type="number"
  placeholder="Quantity"
  name="quantity"
  id="quantity"
  bind:value={itemquantity}
  required
/>
<input
  type="number"
  placeholder="GST (default 5%)"
  name="gst"
  id="gst"
  bind:value={itemgst}
/>
<button id="addItem" on:click={addItem}>Add Item</button>
<br />
