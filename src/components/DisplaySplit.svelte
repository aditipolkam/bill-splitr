<script>
  export let calculated_bill;
</script>

{#each Object.entries(calculated_bill) as [person, data]}
  <div>
    <h4>Bill split for {person}</h4>
    <table align="center" border="1px" border-color="#ff3e00">
      <tr>
        <th>Item</th>
        <th>Quantity</th>
        <th>Split Amount</th>
      </tr>

      {#each data.items as item}
        <tr>
          <td>{item.name}</td>
          <td>{item.quantity}</td>
          <td>{item.split_amount}</td>
        </tr>
      {/each}
      <tr>
        <td colspan="2">Total</td>
        <td>{data.total}</td>
      </tr>
    </table>
  </div>
{/each}

<style>
  table {
    align-content: center;
    border-color: #ff3e00;
    border: 1px;
  }
</style>
