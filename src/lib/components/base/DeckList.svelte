<script lang="ts">
  import { createEventDispatcher } from "svelte";
  import { Trash, Pencil, Icon } from "svelte-hero-icons";

  const dispatch = createEventDispatcher();
  const emitRemove = (id: Number) => dispatch("remove", id);
  const emitEdit = (id: Number) => dispatch("edit", id);
  const emitClick = (name: String) => dispatch("click", name);

  export let items = [];
</script>

<ul>
  {#each items as item}
    <li on:click={() => emitClick(item.name)}>
      {item.name}
      <div class="buttons">
        <div class="icon" on:click|stopPropagation={() => emitEdit(item.id)}>
          <Icon src={Pencil} />
        </div>
        <div class="icon" on:click|stopPropagation={() => emitRemove(item.id)}>
          <Icon src={Trash} />
        </div>
      </div>
    </li>
  {/each}
</ul>

<style lang="sass">
li
  font-family: 'Merriweather Sans', sans-serif
  font-weight: 600
  text-transform: capitalize
  display: flex
  padding: 10px
  margin: 5px 0px 
  background-color: #ff5c27
  border: none
  border-radius: 2px
  font-size: 1rem
  justify-content: space-between
  min-width: 300px
  cursor: pointer
  .buttons
    margin-left: 20px
    display: flex
    gap: 10px
    .icon
      height: 18px
      width: 18px
</style>
