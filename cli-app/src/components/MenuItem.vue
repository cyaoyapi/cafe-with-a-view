<template>
    <div>
        <img
            class="menu-item__image"
            :src="image.source"
            :alt="image.alt"
        />
        <div>
            <h3>{{ name }}</h3>
            <p v-if="inStock">En stock</p>
            <p v-else>En rupture de stock</p>
            <div>
                <label for="add-item-quantity">Quantité : {{ quantity }}</label> <br><br>
                <input id="add-item-quantity" type="number" v-model.number="quantity" /> <br><br>
                <button @click="addToShoppingCart(quantity)">Ajouter au panier d'achat</button> <br><br>
            </div>
        </div>
    </div>
 
</template>

<script>
export default {
    name: "MenuItem",
    props: ['addToShoppingCart', 'image', 'name', 'inStock'],
    data() {
        return {
            quantity: 1
        }
    }
}
</script>
