<script>
	let space = "&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;";

	import Dot from "./Dot.svelte";
	import Span from "./Span.svelte";
	import dayjs from "dayjs";

	const hour = dayjs().format('h')
	const minutes = dayjs().format('m');



	function findRemainder(minutes, nearestMultiple) {
		return nearestMultiple - minutes;
	}

	function roundDown(num) {
  		return Math.floor(num / 5) * 5;
	}

	function roundUp(num) {
  		return Math.ceil(num / 5) * 5;
	}
	
	function getMultiple(minutes) {
		if (minutes < 31) {
			return roundDown(minutes)
		} else {
			return roundUp(minutes)
		}
		
	}


	const remainder = Math.abs(findRemainder(minutes, getMultiple(minutes)));
	
</script>

<div class="clock">

	<div class="row-1">
		<p><Span state="{true}">I{@html space}T{@html space}</Span>L{@html space}<Span state="{true}">I{@html space}S{@html space}</Span>A{@html space}S{@html space}T{@html space}I{@html space}M{@html space}E</p>
	</div>
	<div class="row-2">
		<p>A{@html space}C{@html space}<Span state="{roundDown(minutes) == 15 || roundUp(minutes) == 45}">Q{@html space}U{@html space}A{@html space}R{@html space}T{@html space}E{@html space}R{@html space}</Span>D{@html space}C</p>
	</div>
	<div class="row-3">
		<p><Span state="{roundDown(minutes) == 20 || roundDown(minutes) == 25 || roundUp(minutes) == 35 || roundUp(minutes) == 40}">T{@html space}W{@html space}E{@html space}N{@html space}T{@html space}Y{@html space}</Span><Span state="{roundDown(minutes) == 5 || roundDown(minutes) == 25 || roundUp(minutes) == 35 || roundUp(minutes) == 55}">F{@html space}I{@html space}V{@html space}E{@html space}</Span>X</p>
	</div>
	<div class="row-4">
		<p><Span state="{roundDown(minutes) == 30}">H{@html space}A{@html space}L{@html space}F{@html space}</Span>B{@html space}<Span state="{roundDown(minutes) == 10 || roundUp(minutes) == 50}">T{@html space}E{@html space}N{@html space}</Span>F{@html space}<Span state="{minutes > 30}">T{@html space}O</Span></p>
	</div>
	<div class="row-5">
		<p><Span state="{minutes == 30 || minutes < 30}">P{@html space}A{@html space}S{@html space}T{@html space}</Span>E{@html space}R{@html space}U{@html space}<Span state="{hour == 9}">N{@html space}I{@html space}N{@html space}E</Span></p>
	</div>
	<div class="row-6">
		<p><Span state="{hour == 1}">O{@html space}N{@html space}E{@html space}</Span><Span state="{hour == 6}">S{@html space}I{@html space}X{@html space}</Span><Span state="{hour == 3}">T{@html space}H{@html space}R{@html space}E{@html space}E</Span></p>
	</div>
	<div class="row-7">
		<p><Span state="{hour == 4}">F{@html space}O{@html space}U{@html space}R{@html space}</Span><Span state="{hour == 5}">F{@html space}I{@html space}V{@html space}E{@html space}</Span><Span state="{hour == 2}]">T{@html space}W{@html space}O</Span></p>
	</div>
	<div class="row-8">
		<p><Span state="{hour == 8}">E{@html space}I{@html space}G{@html space}H{@html space}T{@html space}</Span><Span state="{hour == 11}">E{@html space}L{@html space}E{@html space}V{@html space}E{@html space}N</Span></p>
	</div>
	<div class="row-9">
		<p><Span state="{hour == 7}">S{@html space}E{@html space}V{@html space}E{@html space}N{@html space}</Span><Span state="{hour == 12}">T{@html space}W{@html space}E{@html space}L{@html space}V{@html space}E</Span></p>
	</div>
	<div class="row-10">
		<p><Span state="{hour == 10}">T{@html space}E{@html space}N{@html space}</Span>S{@html space}E{@html space}<Span state="{roundDown(minutes) == 0}">O{@html space}C{@html space}L{@html space}O{@html space}C{@html space}K</Span></p>
	</div>
</div>

	
<center class="remainders">
	<Dot state="{remainder > 0}"></Dot>
	<Dot state="{remainder > 1}"></Dot>
	<Dot state="{remainder > 2}"></Dot>
	<Dot state="{remainder > 3}"></Dot>
</center>



<style>


.clock {
	text-align: center;
	padding: 10%;
	font-size: 20px;
}

</style>