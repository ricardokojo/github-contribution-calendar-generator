<script lang="ts">
  import { onDestroy } from "svelte";
  import { isHoldingMouse } from "./stores";

  export let colNumber = -1;
  export let rowNumber = -1;
  export let fillColor = "#EBEDF0";

  let shouldUpdateColor = false;

  function updateFill() {
    if (shouldUpdateColor) {
      fillColor = "#000000";
    }
  }

  const unsubscribe = isHoldingMouse.subscribe(value => {
		shouldUpdateColor = value;
	});

  onDestroy(unsubscribe);
</script>

<rect
  on:click={updateFill}
  on:mousemove={updateFill}
  width="11"
  height="11"
  fill={ fillColor }
  x="{ 16 - colNumber }"
  y="{ rowNumber * 15 }"
  rx="2"
  ry="2">
</rect>

<style>
  rect {
    shape-rendering: geometricPrecision;
    outline: 1px solid rgba(27,31,35,0.06);
    outline-offset: -1px;

    transition: all 0.2s;
  }

  rect:hover {
    stroke:#2ba805;
  }
</style>