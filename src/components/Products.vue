
<template>
    <div>
        <h1>Products</h1>
        <hr/>

        <table class="table">
            <thead>
                <tr>
                    <th>Product</th>
                    <th>Departmeent</th>
                    <th>Price</th>
                    <th></th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="thisProduct in products" :key="thisProduct.ProductID">
                    <th>{{thisProduct.ProductName}}</th>
                    <td>{{thisProduct.DepartmentName}}</td>
                    <td>{{thisProduct.Price}}</td>
                    <td>
                        <router-link :to="`/products/${thisProduct.ProductID}`">
                            <button type="button" class="btn btn-primary">Details</button>
                        </router-link>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>


<script>
export default {
    computed:{
        products(){return this.$store.state.products}
    }
}
</script>

<style scoped>
</style>