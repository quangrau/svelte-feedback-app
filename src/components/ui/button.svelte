<script>
  export let style = 'primary'
  export let type = 'button'
  export let disabled = false
</script>

<button {type} {disabled} class={`px-4 py-2 border-none rounded-md text-white cursor-pointer ${style}`}>
  <slot></slot>
</button>


<style>
  .primary {
    background-color: #202142;
  }

  .secondary {
    background: #ff6a95;
  }

  button:hover {
    transform: scale(0.98);
    opacity: 0.9;
  }

  button:disabled{
    background-color: #cccccc;
    color: #333;
    cursor: not-allowed;
  }

  button:disabled:hover{
    transform:scale(1);
    opacity: 1;
  }
</style>