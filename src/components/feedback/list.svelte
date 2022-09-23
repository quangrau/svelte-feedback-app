<script lang="ts">
	import { fade, scale } from 'svelte/transition';
	import { feedbackStore } from 'src/stores/feedback-store';
	import FeedbackItem from 'src/components/feedback/item.svelte';
</script>

<ul>
	{#each $feedbackStore as fb}
		<li in:scale="{{ duration: 200 }}" out:fade="{{ duration: 200 }}">
			<FeedbackItem item={fb} />
    </li>
	{/each}
</ul>
