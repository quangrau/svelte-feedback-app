<script lang="ts">
	import { createEventDispatcher } from 'svelte';

	export let selected: number | null;

	const dispatch = createEventDispatcher();
	const onChange = (e: any) => {
		selected = e.currentTarget.value;
		dispatch('rating-select', selected);
	};
</script>

<ul class="rating my-10 grid gap-4 grid-cols-5 md:grid-cols-10">
  {#each [1,2,3,4,5,6,7,8,9,10] as num}
	<li>
		<input
			type="radio"
			id={`num${num}`}
			name="rating"
			value={num}
			on:change={onChange}
			checked={selected === num}
		/>
		<label for={`num${num}`}>{num}</label>
	</li>
  {/each}
</ul>

<style>
  .rating li {
    position: relative;
    background: #f4f4f4;
    width: 50px;
    height: 50px;
    text-align: center;
    border-radius: 50%;
    font-size: 19px;
    border: 1px #eee solid;
    transition: 0.3s;
  }

  .rating li label {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 50px;
    height: 50px;
    padding: 10px;
    border-radius: 50%;
    transform: translate(-50%, -50%);
    cursor: pointer;
  }

  .rating li:hover {
    background: #ff6a95;
    color: #fff;
  }

  /* Make actual radio select invisible */
  [type='radio'] {
    opacity: 0;
  }

  /* Use the sibling select */
  [type='radio']:checked ~ label {
    background: #ff6a95;
    color: #fff;
  }
</style>