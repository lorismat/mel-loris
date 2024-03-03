<template>
  <div>

    <section id="scrolly">

			<figure>
				<p>{{ step }}</p>
			</figure>

			<article>
        <ProjParcoursScrollArticle 
          v-for="article in articles" 
          :key="article.index"
          class="step"
          :data-step="article.index"
          :title="article.title"
          :paddingY="article.paddingY"
        >
        </ProjParcoursScrollArticle>
			</article>

		</section>

  </div>
</template>

<script setup>
import scrollama from "scrollama";

const articles = [
  {
    "title": "temp bla",
    "index": 1,
    "paddingY": "20px"
  },
  {
    "title": "temp zzz",
    "index": 2,
    "paddingY": "200px"
  },
  {
    "title": "temp xxx",
    "index": 3,
    "paddingY": "0px"
  },
  {
    "title": "temp ttt",
    "index": 4,
    "paddingY": "400px"   
  }
]

const step = ref(0)

// instantiate the scrollama
const scroller = scrollama();

// scrollama event handlers
function handleStepEnter(res) {
  console.log(res, "---");
  step.value = res.index + 1;
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
@import url("~/assets/scss/projets/parcours/main.scss");

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
  top:0;
  width: 100%;
  margin: 0;
  background-color: #eee;
  height: 100vh;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
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
  color: #fff;
  border: 1px solid purple;
  
  // background-color: rgba(0, 0, 0, 0.1);
  // border: 1px solid purple;
}
</style>