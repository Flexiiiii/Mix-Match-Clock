<script>
	export let state = null;
</script>

<style>
	.active { background-color: whitesmoke; height: 8px; width: 8px;  border-radius: 50%; display: inline-block; position: relative; bottom: 150px; margin: 20px;}
	.non-active { background-color: #333;  height: 8px; width: 8px;  border-radius: 50%; display: inline-block; position: relative; bottom: 150px; margin: 20px;}
</style>

<span
  class="span"
	class:active={state===true}
  class:non-active={state===false}
> <slot></slot>
</span>