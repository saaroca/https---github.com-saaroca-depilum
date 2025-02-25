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

      <!-- Contenedor para los enlaces de navegación -->
      <div class="nav-links">
        <!-- Menú desplegable en hover -->
        <v-menu open-on-hover offset-y close-on-content-click>
          <template v-slot:activator="{ props }">
            <nuxt-link to="/" v-bind="props" class="nav-item">
              DEPILACIÓN LÁSER
            </nuxt-link>
          </template>

          <v-card class="submenu">
            <v-container>
              <v-row>
                <!-- Primera columna: Depilación Femenina -->
                <v-col cols="6">
                  <h4>Depilación Femenina</h4>
                  <v-list density="compact">
                    <v-list-item to="/depilacion-femenina/cuerpo"
                      >Cuerpo</v-list-item
                    >
                    <v-list-item to="/depilacion-femenina/rostro"
                      >Rostro</v-list-item
                    >
                  </v-list>
                </v-col>

                <!-- Segunda columna: Depilación Masculina -->
                <v-col cols="6">
                  <h4>Depilación Masculina</h4>
                  <v-list density="compact">
                    <v-list-item to="/depilacion-masculina/cuerpo"
                      >Cuerpo</v-list-item
                    >
                    <v-list-item to="/depilacion-masculina/rostro"
                      >Rostro</v-list-item
                    >
                  </v-list>
                </v-col>
              </v-row>
            </v-container>
          </v-card>
        </v-menu>

        <!-- Otros enlaces -->
        <nuxt-link to="/" class="nav-item">OTROS TRATAMIENTOS</nuxt-link>
      </div>
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
  height: 4.5rem;
}

/* Estilos para los enlaces de navegación */
.nav-links {
  display: flex;
  gap: 2rem; /* Espacio entre los enlaces */
  margin-left: 2rem; /* Separación del logo */
}

/* Estilo del submenú */
.submenu {
  min-width: 300px;
  padding: 1rem;
  background: white;
}

.submenu h4 {
  font-size: 1rem;
  font-weight: bold;
  margin-bottom: 0.5rem;
}

.v-list-item {
  font-size: 0.9rem;
}

/* Estilo para los enlaces */
.nav-item {
  text-decoration: none;
  color: inherit;
  font-weight: bold;
  font-size: 1rem;
}
</style>
