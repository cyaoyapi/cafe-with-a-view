<template>
    <div>
        <img
            class="menu-item__image"
            :src="image.source"
            :alt="image.alt"
        />
        <div>
            <h3>{{ name }}</h3>
            <p>{{ itemPrice }} €</p>
            <p v-if="inStock">En stock</p>
            <p v-else>En rupture de stock</p>
            <div>
                <label for="add-item-quantity">Quantité : {{ itemQuantity }}</label> <br><br>
                <input id="add-item-quantity" type="number" v-model.number="itemQuantity" /> <br><br>
                <button @click="addToShoppingCart(itemQuantity)">Ajouter au panier d'achat</button> <br><br>
            </div>
        </div>
    </div>
 
</template>

<script>
export default {
    name: "MenuItem",
    props: ['addToShoppingCart', 'image', 'name', 'quantity', 'price', 'inStock'],
    data() {
        return {
            itemQuantity: this.quantity,
            itemPrice: parseFloat(this.price)
        }
    },
    beforeMount(){
        const dayNumber = new Date().getDate() ;
        if(dayNumber % 2 != 0) {
            this.itemPrice *= 0.99 ;
        }
    }
}
</script>
