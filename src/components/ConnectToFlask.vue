<template>
    <div>
        <button @click="getProducts">Update Table</button>
        <form action="postProduct">
            <label for="product">Produkt eingeben</label><br>
            <input type="text" id="product" name="product"><br>
            <input type="submit" value="Submit">
        </form>
        <table border=1>
            <thead>
                <tr>
                    <th scope="col">ID</th>
                    <th scope="col">Name</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(item, index) in items" :key="index">
                    <td>{{ item.id }}</td>
                    <td>{{ item.name }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    data: () => ({
        items: []
    }), 
    methods: {
        getProducts() {
            const path = 'http://localhost:5000/api/shop/products/'; // bei Flask muss CORS aktiv sein;
            axios.get(path)
                .then((res) => {
                    this.items = res.data.items;
                    console.log(res)
                })
                .catch((error) => {
                    console.error(error);
                })
        },
        async getProducts2() {
            const path = 'http://localhost:5000/api/shop/products/';
            let response = await axios.get(path);
            this.items = response.data.items
        }
    },
    created() {
        this.getProducts()
    }
}
</script>

<style>
    table {
        font-family: 'Open Sans', sans-serif;
        width: 750px;
        border-collapse: collapse;
        border: 3px solid #44475C;
        margin: 10px 10px 0 10px;
    }

    table th {
        text-transform: uppercase;
        text-align: left;
        background: #44475C;
        color: #FFF;
        padding: 8px;
        min-width: 30px;
    }

    table td {
        text-align: left;
        padding: 8px;
        border-right: 2px solid #7D82A8;
    }
    table tbody tr:nth-child(2n) td {
        background: #D4D8F9;
    }
</style>