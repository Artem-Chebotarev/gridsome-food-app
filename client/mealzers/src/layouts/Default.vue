<!-- src/layouts/Default.vue -->
  <template>
  <v-app>
    <div
      hidden
      id="snipcart"
      data-api-key="ZTE1ZmM3MTQtMmJlZS00NzE5LTgwZDUtOTM2YTliNWU5Y2ZlNjM3NjEwMjIwMDA5MTU4MTAy"
    ></div>
    <div>
      <v-app-bar
        absolute
        color="orange"
        dark
        shrink-on-scroll
        scroll-target="#scrolling-techniques-2"
      >
        <v-app-bar-nav-icon class="mt-5" @click="drawer = !drawer">
        </v-app-bar-nav-icon>
        <g-link
          class="mt-7 ml-3"
          style="text-decoration: none; color: inherit"
          to="/"
          >Mealzers</g-link
        >
        <v-spacer></v-spacer>
        <v-btn outlined rounded dense class="mt-5 mr-3">
          <g-link style="text-decoration: none; color: inherit" to="/shop/"
            >Shop</g-link
          >
        </v-btn>
        <v-btn outlined rounded dense class="mt-5 mr-3">
          <g-link style="text-decoration: none; color: inherit" to="/support/"
            >Support</g-link
          >
        </v-btn>
        <!-- <v-btn class="snipcart-checkout" icon>
          <v-icon>mdi-cart</v-icon>
          <span class="snipcart-total-items"></span>
          <span class="snipcart-total-price"></span>
        </v-btn> -->
        <v-text-field
          v-model="searchText"
          @click:clear="searchText = ''"
          placeholder="Search products ..."
          class="mt-5 mr-4"
          style="max-width: 350px"
          prepend-inner-icon="mdi-magnify"
          clearable
          outlined
          rounded
          dense
          hide-details
        />
        <v-btn class="mt-4 mr-4 ml-4 snipcart-checkout" icon>
          <v-icon>mdi-cart</v-icon>
          <span class="snipcart-total-items"></span>
          <span class="snipcart-total-price">{{ this.totalPrice }}</span>
        </v-btn>
      </v-app-bar>
      <v-navigation-drawer v-model="drawer" absolute bottom temporary>
        <v-list nav dense>
          <v-list-item-group
            v-model="group"
            active-class="deep-purple--text text--accent-4"
          >
            <v-list-item>
              <v-list-item-title>
                <v-btn elevation="0" rounded>
                  <g-link
                    style="text-decoration: none; color: orange"
                    to="/shop/"
                    >Shop</g-link
                  >
                </v-btn>
              </v-list-item-title>
            </v-list-item>
            <v-list-item>
              <v-list-item-title>
                <v-btn elevation="0" rounded dense>
                  <g-link
                    style="text-decoration: none; color: orange"
                    to="/support/"
                    >Support</g-link
                  >
                </v-btn>
              </v-list-item-title>
            </v-list-item>
          </v-list-item-group>
        </v-list>
      </v-navigation-drawer>
      <v-sheet
        id="scrolling-techniques-2"
        class="overflow-y-auto"
        max-height="600"
      >
        <v-container style="height: 120px"></v-container>
      </v-sheet>
      <slot />
    </div>
    <Footer />
  </v-app>
</template>

<script>
import Footer from "@/components/Footer.vue";
export default {
  components: {
    Footer,
  },

  data() {
    const drawer = false;
    const group = null;
    return {
      drawer,
      group,
      totalPrice: 0,
    };
  },

  watch: {
    group() {
      this.drawer = false;
    },
  },

  methods: {
    getTotalPrice() {
      return Snipcart.store.getState().cart.total;
    },
  },

  mounted() {
    this.totalPrice = this.getTotalPrice();
  },
};
</script>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>
