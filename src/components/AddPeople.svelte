<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  let person = "";
  function addPerson() {
    //console.log(person);
    if (person == "") {
      return;
    }
    dispatch("message", {
      personname: person,
    });
    person = "";
  }
</script>

<input
  type="text"
  placeholder="Name"
  bind:value={person}
  id="person-name"
  required
/>
<button id="add" on:click={addPerson}>Add Person</button>
