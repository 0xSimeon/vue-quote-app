<template>
	<div class="row">
         <app-quote v-for="(quote, index) in quotes" @click.native="deleteQuote(index)">{{ quote }}</app-quote>
    </div>

    
      
</template>

<script>
import Quote from "./Quote.vue";
export default {
    methods: {
        deleteQuote(index) {
            this.$emit('quoteDeleted', index);
        }
    },
    props: ["quotes"],
    components: {
        appQuote: Quote
    }
};
</script>

<style scoped>

</style>
