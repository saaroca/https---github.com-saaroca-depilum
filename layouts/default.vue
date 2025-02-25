<template>
  <v-app>
    <!-- Barra de navegación -->
    <v-app-bar fixed app class="app-bar">
      <!-- Logo alineado a la izquierda -->
      <nuxt-link to="/" class="logo-container">
        <img
          class="depilum-logo"
          alt="Depilum logo"
          src="https://centroslaserys.com/wp-content/uploads/2022/04/laserys_3_solo.png"
        />
      </nuxt-link>

      <v-spacer></v-spacer>

      <!-- Carrito alineado a la derecha -->
      <v-btn icon to="/checkout/checkout">
        <v-icon class="cart-icon">mdi-cart-outline</v-icon>
      </v-btn>
    </v-app-bar>

    <!-- Contenido principal -->
    <v-main>
      <v-container>
        <slot />
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

// Estado para ocultar la barra al hacer scroll
const isHidden = ref(false);

const handleScroll = () => {
  isHidden.value = window.scrollY > 100;
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<style scoped>
/* Efecto de ocultar navbar */
.hide-navbar {
  transform: translateY(-100%);
  transition: transform 0.3s ease-in-out;
}

/* Ajuste del navbar */
.app-bar {
  display: flex;
  align-items: center;
  padding: 0 1rem;
}

/* Contenedor del logo */
.logo-container {
  display: flex;
  align-items: center;
}

/* Tamaño del logo */
.depilum-logo {
  height: 3.5rem;
}

/* Estilo del botón del carrito */
.cart-icon {
  font-size: 2rem;
}
</style>
