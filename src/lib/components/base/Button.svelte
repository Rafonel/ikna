<script lang="ts">
  export let link = "";
  const click = (e) => {
    if (link) {
      window.location.href = link;
    }
  };
</script>

<button on:click|preventDefault={click}> <slot /> </button>

<style lang="sass">
button
  color: white
  padding: 5px 10px
  margin: 5px 
  background-color: #ff3e00
  border: none
  border-radius: 4px
  font-size: 1.125rem
</style>
