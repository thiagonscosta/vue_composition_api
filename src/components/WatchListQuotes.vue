<template>
  <ListQuotes :quotes="quotes" :listenQuotes="listenQuotes" />
  <cite class="text-small">
    Atualizará novamente em <strong>x segundos</strong>
  </cite>
</template>

<script>
import { defineComponent } from "@vue/composition-api";
import ListQuotes from "./QuotesList.vue";
import { ref } from "vue";

export default defineComponent({
  components: {
    ListQuotes,
  },
  props: {
    listenQuotes: {
      type: Array,
      required: true,
    },
  },
  setup() {
    const quotes = ref({});

    return { quotes };
  },
});
</script>
