<template>
  <div class="carousel-container">
    <div class="carousel-wrapper carousel-one">
      <client-only>
        <carousel class="carousel-inner" v-bind="options">
          <slide v-for="(item, index) in items" :key="index" :data-index="index" class="carousel-item">

            <div class="slide-inner">
              <div class="carousel-image-wrapper">
                <img :src="item.imagePath" :alt="item.title" v-if="item.imagePath" />
              </div>

              <div class="carousel-content">
                <h3 class="title-group">
                  <div class="title">{{ item.title || '' }}</div>
                </h3>
                <div class="subtitle">{{ item.synopsis || '' }}</div>
              </div>
            </div>
          </slide>
        </carousel>
      </client-only>
    </div>
  </div>
</template>

<script>
export default {
  name: "CarouselPage",

  data() {

    const items = []

    for (let index = 1; index <= 3; index++) {
      items.push({ title: `a_${index}`, synopsis: ``, imagePath: `/mockup/banner/${index}_980x551.jpg` })
    }

    return {
      items,

      options: {
        loop: true,
        perPage: 1,
        // paginationActiveColor: '#000000', 
        // paginationColor: '#efefef',
        // paginationPadding: 10,
        // paginationSize: 10,

        navigationEnabled: true,
        // navigationClickTargetSize: 8,
        navigationNextLabel: `<svg viewBox="0 0 24 24" focusable="false"><g><path d="M10 6L8.59 7.41 13.17 12l-4.58 4.59L10 18l6-6z"></path></g></svg>`,
        navigationPrevLabel: `<svg viewBox="0 0 24 24" focusable="false"><g><path d="M15.41 7.41L14 6l-6 6 6 6 1.41-1.41L10.83 12z"></path></g></svg>`,

        autoplay: true,
        // autoplayTimeout: 3000,
        // autoplayHoverPause: true,
        // mouseDrag: false,
      }
    }
  },
}
</script>

<style scoped>
.carousel-container {
  overflow: hidden;
}

.carousel-wrapper {
  position: relative;
  max-width: 980px;
  margin: 0 auto;
  height: 561.13167px;
  overflow: unset;
}

.carousel-inner,
.VueCarousel-slide,
.VueCarousel-inner {
  height: 561.13167px;
}
</style>