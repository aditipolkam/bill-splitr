<script>
  import AddItem from "./components/AddItem.svelte";
  import AddPeople from "./components/AddPeople.svelte";
  import DisplaySplit from "./components/DisplaySplit.svelte";

  let people = [];
  let selected_people = [];
  let calculated_bill = {};
  function addName(event) {
    people = [...people, event.detail.personname];
    calculated_bill[event.detail.personname] = {
      items: [],
      total: 0,
    };
    //console.log(people);
  }

  function displayError(event) {
    alert(event.detail);
  }

  function addItem(event) {
    //console.log(event.detail);
    let item = event.detail;
    for (let i = 0; i < item.length; i++) {
      calculated_bill[item[i]["person"]]["items"].push({
        name: item[i]["name"],
        split_amount: item[i]["split_amount"],
        quantity: item[i]["quantity"],
      });
      calculated_bill[item[i]["person"]]["total"] += item[i]["split_amount"];
    }
    selected_people = [];
  }
</script>

<main>
  <h1>Bill Splitr</h1>
  <AddPeople on:message={addName} /><br />
  {#each people as person}
    <input
      type="checkbox"
      bind:group={selected_people}
      name="selected_people"
      value={person}
    />
    {person}
  {/each}<br />
  {#if selected_people.length > 0}
    <p>You selected:</p>
    {selected_people.join(" ")}
  {/if}<br />
  <AddItem {selected_people} on:addItem={addItem} on:error={displayError} /><br
  />
  <DisplaySplit {calculated_bill} />
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
