<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  let person = "";
  function addPerson() {
    //console.log(person);
    dispatch("message", {
      personname: person,
    });
    person = "";
  }
</script>

<input type="text" bind:value={person} id="person-name" />
<button id="add" on:click={addPerson}>Add Person</button>
