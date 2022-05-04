<script>
  let itemname = "";
  let itemamount = 0;
  let itemquantity = 0;
  let itemgst = 5.0;
  function addItem() {}
</script>

<input type="text" name="item" id="item" bind:value={itemname} />
<input type="text" name="amount" id="amount" bind:value={itemamount} />
<input type="text" name="quantity" id="quantity" bind:value={itemquantity} />
<input type="text" name="gst" id="gst" bind:value={itemgst} />
<button id="addItem" on:click={addItem}>Add Item</button>
