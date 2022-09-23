<script>
  import { feedbackStore } from 'src/stores/feedback-store';

  $: count = $feedbackStore.length;
  $: average = Math.round($feedbackStore.reduce((a, {rating}) => a + rating, 0) / $feedbackStore.length);
</script>

<div class="flex justify-between">
  <h4>{count} Reviews</h4>
  <h4>Ratings Average: {average || 0}</h4>
</div>