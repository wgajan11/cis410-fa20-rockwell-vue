<template>
    <div>
        <div class="card">
            <div class="card-body">
                <h2 class="text-primary">{{product.ProductName}}</h2>
                <br/>
                <p>Price: <br/> <strong>{{product.Price}}</strong></p>
                <!-- <p>Summary: <br/> <strong>{{product.Summary}}</strong></p>
                <p>Budget: <br/> <strong>{{formattedBudget}}</strong></p> -->
                <p>Department: <br/> <strong>{{product.DepartmentName}}</strong></p>
            </div>
        </div>
        <br/>
        <router-link v-if="auth" :to="`/products/${this.$route.params.pk}/review`">
            <button type="button" class="btn btn-success">Add a Review</button>
        </router-link>
        <router-link v-else :to="`/signin`">
            <button type="button" class="btn btn-outline-success">Sign In to Add a Review</button>
        </router-link>
        <br/>
        <br/>
        <router-view></router-view>
    </div>
</template>


<script>
export default {
    computed:{
        product(){
            var movies = this.$store.state.products;
            var thisProduct = movies.find((aProduct)=> aProduct.ProductID == this.$route.params.pk)
            console.log("here is the movie you want", thisProduct);
            return thisProduct
        },
        // formattedBudget(){
        //     return new Intl.NumberFormat("en-US",{
        //         style: 'currency',
        //         currency: 'USD'
        //     }).format(this.movie.Budget)
        // },
        auth(){return this.$store.state.token}
    }
}
</script>

<style scoped>
</style>