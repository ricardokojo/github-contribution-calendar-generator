<script lang="ts">
  import { isHoldingMouse } from "./stores"
  import Day from "./Day.svelte";

  let legendColors = [
    { color: "#EBEDF0", level: 0 },
    { color: "#9BE9A8", level: 1 },
    { color: "#40C463", level: 2 },
    { color: "#30A14E", level: 3 },
    { color: "#216E39", level: 4 },
  ];

  function onMouseHold() {
    isHoldingMouse.set(true);
  }

  function onMouseRelease() {
    isHoldingMouse.set(false);
  }
</script>

<div class="js-yearly-contributions" on:mousedown={onMouseHold} on:mouseup={onMouseRelease}>
  <div class="position-relative">
    <div class="border py-2 graph-before-activity-overview">
      <div class="js-calendar-graph mx-md-2 mx-3 d-flex flex-column flex-items-end flex-xl-items-center overflow-hidden pt-1 is-graph-loading graph-canvas ContributionCalendar height-full text-center">
        <svg width="828" height="128" class="js-calendar-graph-svg">
          <g transform="translate(10, 20)">
            {#each Array.from({length: 52}, (_x, i) => i) as colNumber}
              <g transform="translate({ colNumber * 16 }, 0)">
                {#each Array.from({length: 7}, (_x, i) => i) as rowNumber}
                  <Day colNumber={colNumber} rowNumber={rowNumber} />
                {/each}
              </g>
            {/each}
            <text x="16" y="-8" >Jul</text>
            <text x="61" y="-8" >Aug</text>
            <text x="136" y="-8">Sep</text>
            <text x="196" y="-8">Oct</text>
            <text x="256" y="-8">Nov</text>
            <text x="331" y="-8">Dec</text>
            <text x="391" y="-8">Jan</text>
            <text x="466" y="-8">Feb</text>
            <text x="526" y="-8">Mar</text>
            <text x="586" y="-8">Apr</text>
            <text x="646" y="-8">May</text>
            <text x="721" y="-8">Jun</text>
            <text x="781" y="-8">Jul</text>
            <text dx="-10" dy="8" style="display: none;">Sun</text>
            <text dx="-10" dy="25">Mon</text>
            <text dx="-10" dy="32" style="display: none;">Tue</text>
            <text dx="-10" dy="56">Wed</text>
            <text dx="-10" dy="57" style="display: none;">Thu</text>
            <text dx="-10" dy="85">Fri</text>
            <text dx="-10" dy="81" style="display: none;">Sat</text>
          </g>
        </svg>
          
        <footer>
          <a href="https://docs.github.com/articles/why-are-my-contributions-not-showing-up-on-my-profile" class="Link--muted">
            Learn how we count contributions
          </a>
          <div title="A summary of pull requests, issues opened, and commits to the default and gh-pages branches.">
            Less
            {#each legendColors as { color }}
              <svg width="10" height="10">
                <rect width="10" height="10" fill="{ color }" rx="2" ry="2"></rect>
              </svg>&nbsp;
            {/each}
            More
          </div>
        </footer>
      </div>
    </div>
  </div>      
</div>

<style>
  .js-yearly-contributions {
    font-family: "-apple-system", "BlinkMacSystemFont", "Segoe UI", "Helvetica", "Arial", "sans-serif", "Apple Color Emoji", "Segoe UI Emoji";
  }

  .position-relative {
    position: relative;
  }

	.graph-before-activity-overview {
		border-top-left-radius: 6px;
    border-top-right-radius: 6px;
    padding-top: 8px!important;
    padding-bottom: 8px!important;
    border: 1px solid #e1e4e8!important;
	}
	
	.js-calendar-graph {
    display: flex!important;
    text-align: center!important;
    padding-top: 4px!important;
    margin-right: 8px!important;
    margin-left: 8px!important;
    height: 100%!important;
    overflow: hidden!important;
    align-items: center!important;
    flex-direction: column!important;
	}

	.js-calendar-graph rect {
		shape-rendering: geometricPrecision;
    outline: 1px solid rgba(27,31,35,.04);
    outline-offset: -1px;
    rx: 2;
    ry: 2;
	}

	.js-calendar-graph text {
		font-size: 9px;
    fill:#24292E;
    user-select: none;
	}

  footer {
    @apply flex justify-between w-full;

    font-size: 12px;
    padding: 4px 32px;
  }

  footer > a {
    color: rgb(88, 96, 105);
  }

  footer > a:hover {
    color: rgb(3, 102, 214);
    text-decoration: none;
  }

  footer > div {
    color: rgb(88, 96, 105);
  }

  footer > div > svg {
    @apply inline-block;
  }

  footer > div > svg > rect {
    shape-rendering: geometricPrecision;
    outline: 1px solid rgba(27,31,35,0.06);
    outline-offset: -1px;
  }
</style>