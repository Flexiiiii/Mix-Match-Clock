<script>
	export let state = null;
</script>

<style>
	.active { color: whitesmoke;}
	.non-active { color: #333; }
</style>

<span
  class="span"
	class:active={state===true}
  class:non-active={state===false}
> <slot></slot>
</span>