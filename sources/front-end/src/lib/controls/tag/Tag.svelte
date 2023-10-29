<script>
  /**
   * @type {string}
   */
  export let value;
  /**
   * @type {string}
   */
  export let text;

  const handleButtonClick = (e) => {
    console.log('handleButtonClick', e, value);
  };
</script>

<style>
  button {
    background-color: transparent;
    padding: 0.25rem;
    border: none;
    cursor: pointer;
  }
</style>

<button on:click={handleButtonClick}>{text}</button>