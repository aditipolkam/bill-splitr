<script>
  import AddItem from "./components/AddItem.svelte";
  import AddPeople from "./components/AddPeople.svelte";
  let people = [];
  let selected_people = [];
  $: speople = selected_people.join(" ");
  function addName(event) {
    people = [...people, event.detail.personname];
    //console.log(people);
  }
</script>

<main>
  <h1>Bill Spiltr</h1>
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
  <AddItem {selected_people} /><br />
  {#if selected_people.length > 0}
    <p>You selected:</p>
    {#each selected_people as person}
      {person}
    {/each}
  {/if}<br />
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
