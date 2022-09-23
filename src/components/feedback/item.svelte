<script lang="ts">
	import { feedbackStore } from "src/stores/feedback-store";
	import type { IFeedback } from "src/stores/feedback-store";
  import Card from 'src/components/ui/card.svelte';

  export let item: IFeedback;

  const handleDelete = (itemId: string) => {
    feedbackStore.update((currentFeedback) => {
      return currentFeedback.filter(item => item.id !== itemId)
    })
  }
</script>

<Card>
  <div class="num-display">
    {item.rating}
  </div>
  <button class="close" on:click={() => handleDelete(item.id)}>&#x2715</button>
  <p class="text-display">
    {item.text}
  </p>
</Card>

<style>
  .num-display {
    position: absolute;
    top: -10px;
    left: -10px;
    width: 50px;
    height: 50px;
    background: #ff6a95;
    color: #fff;
    border: 1px #eee solid;
    border-radius: 50%;
    padding: 10px;
    text-align: center;
    font-size: 19px;
  }

  .close {
    position: absolute;
    top: 10px;
    right: 20px;
    cursor: pointer;
    background: none;
    border: none;
  }
</style>