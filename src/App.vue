<template>
	<div class="container">
		<app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
		<app-new-quote @quoteAdded="newQuote"></app-new-quote>
		<div class="alert alert-info">Info: Click on a quote to delete it</div>
		<app-quote-grid
			:quotes="quotes"
			@quoteDeleted="deleteQuote"
		></app-quote-grid>
		<div class="row">
			<div class="col-sm-12 text-center"></div>
		</div>
		<footer >
			<p class="text-center" v-if="windowWidth < 420">Copyright &copy; <a href="https://simicode.me">Simeon Udoh</a></p>
		</footer>
	</div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid.vue";
import NewQuote from "./components/NewQuote.vue";
import Header from "./components/Header.vue";
export default {
	data() {
		return {
			quotes: ["Just a quote to see something"],
			maxQuotes: 10,
			windowWidth: window.innerWidth,
		};
	},

	mounted() {
		window.onresize = () => {
			this.windowWidth = window.innerWidth;
			console.log(this.windowWidth);
		};
	},
	methods: {
		newQuote(quote) {
			if (this.quotes.length >= this.maxQuotes) {
				return alert("Please delete quotes first!");
			} else {
				this.quotes.push(quote);
			}
		},
		deleteQuote(index) {
			this.quotes.splice(index, 1);
		},
	},
	components: {
		appQuoteGrid: QuoteGrid,
		appNewQuote: NewQuote,
		appHeader: Header,
	},
};
</script>

<style></style>
