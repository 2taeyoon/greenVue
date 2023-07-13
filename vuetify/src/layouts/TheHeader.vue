<template>
    <v-app-bar style="padding:0 90px;" color="white" :elevation="5">
        <template v-slot:prepend>
            <v-app-bar-nav-icon></v-app-bar-nav-icon>
        </template>

        <v-app-bar-title>
            <router-link to="/" class="title text-h5 font-weight-bold text-decoration-none">Vuetify App</router-link>
        </v-app-bar-title>

        <v-list class="d-flex align-center">
            <v-list-item v-for="(menu, index) in menus" :key="index">
                <router-link :to="menu.url" class="menu text-decoration-none">{{ menu.title }}</router-link>
            </v-list-item>
        </v-list>
        <v-btn icon="mdi-magnify"></v-btn>
        <v-btn variant="outlined" color="teal" rounded="xl">CONTACT</v-btn>
    </v-app-bar>
</template>

<script setup>
const menus = [
    { title: 'Home', url: '/' },
    { title: 'About Me', url: '/about' },
    { title: 'Portfolio', url: '/portfolio' },
    { title: 'Project', url: '/project' },
    { title: 'Gallary', url: '/gallery' }
]
</script>
<style scoped>
    .title { color: teal; }
    .menu { color: #212121; }
    .menu:hover { color: teal; }
</style>