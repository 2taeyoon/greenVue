<template>
    <v-container class="py-15">
        <v-row>
            <v-col cols="12" md="6">
                <h2>Welcome to my <br> Portfolio</h2>
                <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Est consectetur animi, explicabo rerum possimus
                    beatae molestiae, velit qui quisquam numquam, aliquid reprehenderit. Quidem veniam amet ab aspernatur
                    voluptatem? Nihil, quasi.</p>
                <v-btn color="light-green" rounded class="mr-10">About Me</v-btn>
                <v-btn color="indigo" rounded>
                    <v-icon start icon="mdi-play-circle"></v-icon>Portfolio
                </v-btn>
            </v-col>
            <v-col md="6">
                <img class="main_image" src="@/assets/main_image.jpg" alt="main_image">
            </v-col>
        </v-row>
    </v-container>
</template>

<script setup>

</script>

<style scoped>
    .main_image { width: 100%; }
</style>