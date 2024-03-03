<template>
  <div>

    <section class="section-block" id="intro">
      <div>START</div>
    </section>

    <section id="scrolly">
			<figure>
				<p>0</p>
			</figure>

			<article>
				<div class="step" data-step="1">
					<p>STEP 1</p>
				</div>
				<div class="step" data-step="2">
					<p>STEP 2</p>
				</div>
				<div class="step" data-step="3">
					<p>STEP 3</p>
				</div>
				<div class="step" data-step="4">
					<p>STEP 4</p>
				</div>
			</article>
		</section>

    <section class="section-block" id="outro">
      <div>END</div>
    </section>

  </div>
</template>

<script setup>
import scrollama from "scrollama";

// instantiate the scrollama
const scroller = scrollama();

// scrollama event handlers
function handleStepEnter(res) {
  console.log(res, "---");
}

// setup the instance, pass callback functions
onMounted(() => {
  scroller
    .setup({
      step: "#scrolly article .step",
      offset: 0,
      debug: false
    })
    .onStepEnter(handleStepEnter);
})

</script>

<style lang="scss" scoped>

#scrolly {
  position: relative;
  background-color: #f3f3f3;
}

article {
  position: relative;
  padding: 0;
  max-width: 20rem;
  margin: 0 auto;
}

figure {
  position: -webkit-sticky;
  position: sticky;
  left: 0;
  width: 100%;
  margin: 0;
  -webkit-transform: translate3d(0, 0, 0);
  -moz-transform: translate3d(0, 0, 0);
  transform: translate3d(0, 0, 0);
  background-color: #8a8a8a;
  z-index: 0;
  top:0;

  p {
    text-align: center;
    position: absolute;
    font-size: 8rem;
    font-weight: 900;
    color: #fff;
  }
}

.step {
  margin: 0 auto 2rem auto;
  height: 100vh;
  color: #fff;
  background-color: rgba(0, 0, 0, 0.1);
  border: 1px solid purple;

  p {
    text-align: center;
    padding: 1rem;
    font-size: 1.5rem;
    background-color: #3b3b3b;
  }
}

.section-block, figure {
  height: 100vh;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}
</style>