<template>
    <div class="menu-item">
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
                <button @click="updateShoppingCart">Ajouter au panier d'achat</button> <br><br>
            </div>
        </div>
    </div>
 
</template>

<script>
export default {
    name: "MenuItem",
    props: {
        image: {
            type: Object,
            required: true,
        }, 
        name: {
            type: String,
            required: true,
        }, 
        quantity: {
            type: Number,
            default: 1
        }, 
        price: {
            type: Number,
            required: true,
        }, 
        inStock: {
            type: Boolean,
            default: true
        }
    },
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
    },
    methods: {
        updateShoppingCart(){
            this.$emit('add-items-to-cart', { quantity: this.itemQuantity }) ;
        }
    }
}
</script>

<style lang="scss">

.menu-item {
  display: flex;
  width: 500px;
  justify-content: space-between;
  margin-bottom: 30px;

    &__image {
    max-width: 300px;
    }

}


</style>