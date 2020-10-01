<template>
    <div id="app" class="app">
        <h1>{{ restaurantName }}</h1>
        <p class="description">
            Bienvenue dans notre café {{ restaurantName }}! Nous sommes réputés pour
            notre pain et nos merveilleuses pâtisseries. Faites vous plaisir dès le
            matin ou avec un goûter réconfortant. Mais attention, vous verrez qu'il
            est difficile de s'arrêter.
        </p>

        <section class="menu">
            <h2>Menu</h2>
    <MenuItem v-for="item in simpleMenu" 
    :key="item.name" 
    :addToShoppingCart="addToShoppingCart" 
    :image="item.image" 
    :name="item.name"
    :inStock="item.inStock"
    />
        </section>

        <aside class="shopping-cart">
            <h2>Panier d'achat: {{ totalArticles }} articles</h2>
        </aside>


        <footer class="footer">
            <p>Copyright {{ restaurantName }} 2020</p>
        </footer>
    </div>
</template>

<script>
import MenuItem from "../components/MenuItem"

export default {
name: 'App',
components: {
MenuItem,
},
data() {
return {
  restaurantName: "La belle vue",
  simpleMenu: [
    {
      name: "Croissant",
      image: {
        source: "/images/croissant.jpg",
        alt: "Un croissant"
      },
      inStock: true
    },
    {
      name: "Baguette de pain",
      image: {
        source: "/images/french-baguette.jpeg",
        alt: "Quatre baguettes de pain"
      },
      inStock: true
    },
    {
      name: "Éclair",
      image: {
        source: "/images/eclair.jpg",
        alt: "Éclair au chocolat"
      },
      inStock: false
    }
  ],
  totalArticles: 0,
}
},   
computed: {
copyright() {
  const currentYear = new Date().getFullYear()

  return `Copyright ${this.restaurantName} ${currentYear}`
}
},
methods: {
addToShoppingCart(quantity){
  this.totalArticles += Number(quantity) ;
}
}
}

</script>

<style lang="scss">
#app {
font-family: Avenir, Helvetica, Arial, sans-serif;
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
text-align: center;
color: #2c3e50;
margin-top: 60px;
}
</style>
