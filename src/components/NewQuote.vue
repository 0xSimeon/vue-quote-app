<template>
	<div class="row">
		<form action="">
            <p v-if="hide" class="error text-center bg-danger">{{ message }}</p>
			<div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 mb-2 margin">
				<label for="quote">Quote </label>
				<textarea
					name="quote"
					id="quote"
					class="form-control"
					rows="3"
					v-model="quote"
				></textarea>
			</div>

            <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3">
				<button class="btn btn-primary margin" @click.prevent="createNew">Add Quote</button>
			</div>
		</form>
	</div>
</template>

<script>
export default {
    data: function() {
        return {
            quote: '',
            hide: false,
            message: `Sorry... You can't add an empty quote!`
             
        }
    },
    methods: {
        validateQuote() {
            this.hide = true;
            setTimeout(() => this.hide = false, 2000);
        },
        createNew() {
            if (this.quote === '') return this.validateQuote();
            this.$emit('quoteAdded', this.quote);
            this.quote = '';
        },
        
    }
};
</script>

<style scoped>
.margin {
    margin-bottom: 10px; 
}
.error {
    padding: .7rem; 
    font-size: 16px;
}


</style>
