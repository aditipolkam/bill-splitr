<script>
  export let calculated_bill;
</script>

{#each Object.entries(calculated_bill) as [person, data]}
  <div>
    <p>{person}</p>
    <table>
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
