<template>
  <Layout>
    <template>
      <v-carousel
        cycle
        height="400"
        hide-delimiter-background
        :show-arrows="false"
      >
        <v-carousel-item v-for="(image, i) in images" :key="i">
          <v-sheet height="100%">
            <v-row class="fill-height" align="center" justify="center">
              <div class="display-3">
                <img :src="image" />
              </div>
            </v-row>
          </v-sheet>
        </v-carousel-item>
      </v-carousel>
      <div class="separator"></div>
    </template>
  </Layout>
</template>

<script>
export default {
  metaInfo: {
    title: "Mealzers",
  },

  data() {
    return {
      images: [
        "https://bit.ly/33Ehev5",
        "https://bit.ly/33Ehev5",
        "https://bit.ly/33Ehev5",
        "https://bit.ly/33Ehev5",
      ],
    };
  },
};
</script>
