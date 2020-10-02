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
    :image="item.image" 
    :name="item.name" 
    :quantity="item.quantity" 
    :price="item.price"
    :inStock="item.inStock"
    />
        </section>

        <aside class="shopping-cart">
            <h2>Panier d'achat: {{ totalArticles }} articles</h2>
        </aside>


        <footer class="footer">
            <p>{{ copyright }}</p>
        </footer>
    </div>
</template>

<script>
import { mapState, mapGetters } from 'vuex'
import MenuItem from "../components/MenuItem"

export default {
name: 'App',
components: {
MenuItem,
},   
computed: {
...mapState(['totalArticles', 'restaurantName', 'simpleMenu']),
...mapGetters(['copyright'])
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

.description {
  max-width: 960px;
  font-size: 1.2rem;
  margin: 0 auto;
}

.menu {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}


.footer {
  text-align: center;
  font-style: italic;
}

.shopping-cart {
  position: absolute;
  right: 30px;
  top: 0;
}
</style>
