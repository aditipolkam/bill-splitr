<script>
  import { createEventDispatcher } from "svelte";
  export let selected_people;
  let itemname = "";
  let itemamount = "";
  let itemquantity = "";
  let itemgst = "";
  const dispatch = createEventDispatcher();

  function addItem() {
    if (itemgst === "") {
      itemgst = 5;
    }
    //console.log(selected_people);
    const totalp = selected_people.length;
    if (totalp == 0)
      return dispatch("error", "Please select atleast one person");

    if (itemname === "") return dispatch("error", "Please enter item name");

    if (itemamount === "" || itemamount == 0)
      return dispatch("error", "Please enter item amount");

    if (itemquantity === "" || itemquantity == 0)
      return dispatch("error", "Please enter item quantity");

    const gst_amount = parseInt((itemamount * itemgst) / 100);
    const share = ((itemamount + gst_amount) * itemquantity) / totalp;

    let item_split = [];
    for (let i = 0; i < selected_people.length; i++) {
      let q = 0;
      if (totalp == 1) q = itemquantity;
      else if (itemquantity % totalp == 0) q = parseInt(itemquantity / totalp);
      else q = itemquantity / totalp;

      item_split.push({
        person: selected_people[i],
        name: itemname,
        split_amount: share,
        quantity: q,
      });
    }

    dispatch("addItem", item_split);

    itemname = "";
    itemamount = "";
    itemquantity = "";
    itemgst = "";
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
