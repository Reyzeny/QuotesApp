<template>
    <div>
        <div class="col-lg-6 col-md-6 col-sm-6 col-xs-6">
            <form @submit.prevent="onSubmitted">
                <div class="form-group">
                    <label for="content"><strong>Quote</strong></label>
                    <em>Write your quote</em>
                    <textarea name="content" class="form-control" cols="80" rows="6" 
                                v-model="quoteContent" id="content"></textarea>
                    <div class="form-group">
                        <button type="submit" class="btn btn-success">Add quote</button>
                    </div>
                </div>
            </form>
        </div>
    </div>
    
</template>
<script>
    import axios from 'axios'
    export default {
        data () {
            return {
                quoteContent: ''
            }
        },
        methods: {
            onSubmitted () {
                axios.post("http://localhost:8000/api/quote", {
                content: this.quoteContent
                })
                .then((response) => {
                    window.location.href = "/"
                }) 
                .catch((error) => {
                    console.log(error)
                }) 
            }
        }
    }    
</script>

<style scoped>
#content {
    margin-top: 40px;
}
</style>