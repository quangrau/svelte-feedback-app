<script lang="ts">
	import { v4 as uuid } from 'uuid';
	import { feedbackStore } from 'src/stores/feedback-store';
	import Button from 'src/components/ui/button.svelte';
	import Card from 'src/components/ui/card.svelte';
	import RatingSelect from 'src/components/feedback/rating-select.svelte';

	let text = '';
	let rating = 10;
	let btnDisabled = true;
	let min = 10;
	let message: string | null;

	const _isFormValid = () => {
		return text.trim().length > min && rating;
	};

	const handleSelect = (e: CustomEvent<string>) => {
		rating = Number(e.detail);
	};

	const handleInput = () => {
		if (!_isFormValid()) {
			message = `Text must be at least ${min} characters.`;
			btnDisabled = true;
		} else {
			message = null;
			btnDisabled = false;
		}
	};

	const handleSubmit = () => {
		if (_isFormValid()) {
			const newFeedback = {
				id: uuid(),
				rating,
				text
			};

			// Adding newFeedback to store
			feedbackStore.update((currentFeedback) => {
				return [newFeedback, ...currentFeedback];
			});

			// Reset text
			text = '';
		}
	};
</script>

<Card>
	<header>
		<h2 class="text-lg mb-4 font-semibold text-center">
			How would you rate your experience with us?
		</h2>
	</header>

	<form on:submit|preventDefault={handleSubmit}>
		<RatingSelect selected={rating} on:rating-select={handleSelect} />
		<div class="flex flex-row border rounded-lg px-4 py-2">
			<input
				class="grow border-none focus:outline-none pr-4"
				type="text"
				placeholder="Tell us something that can be better..."
				on:input={handleInput}
				bind:value={text}
			/>
			<Button style="primary" type="submit" disabled={btnDisabled}>Send</Button>
		</div>

		{#if message}
			<p class="pt-2 text-xs font-normal text-gray-600">{message}</p>
		{/if}
	</form>
</Card>
