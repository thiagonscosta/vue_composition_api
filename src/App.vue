<template>
  <div class="container grid-lg my-2 py-2">
    <div class="card">
      <div class="card-header">
        <div class="h4">Follow</div>
      </div>
      <div class="card-body">
        <WatchListQuotes />
      </div>
    </div>

    <div class="card">
      <div class="card-header">
        <div class="h4">All Coins</div>
      </div>
      <div class="card-body">
        <QuotesList :quotes="quotes" :listenQuotes="listenQuotes" />
      </div>
    </div>
  </div>
</template>

<script>
import { onMounted, reactive, toRefs } from "vue";
import QuotesList from "./components/QuotesList.vue";
import WatchListQuotes from "./components/WatchListQuotes.vue";
import api from "./services/api";

export default {
  name: "App",
  components: {
    QuotesList,
    WatchListQuotes,
  },
  setup() {
    const data = reactive({
      quotes: {},
      listenQuotes: [],
    });

    onMounted(async () => {
      await api.all().then((resp) => {
        data.quotes = resp.data;
      });
    });

    return { ...toRefs(data) };
  },
};
</script>
