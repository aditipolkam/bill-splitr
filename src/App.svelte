<script>
  import AddItem from "./components/AddItem.svelte";
  import AddPeople from "./components/AddPeople.svelte";
  export let name;
  function addName(event) {
    console.log(event.detail.personname);
  }
</script>

<main>
  <h1>Hello {name}!</h1>
  <AddPeople on:message={addName} />
  <AddItem />
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
