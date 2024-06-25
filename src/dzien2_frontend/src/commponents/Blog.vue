<template>
    <div>
        <button @click="pobierzWpisy">refresh</button>
        siema blog
        {{ wpisy }}
        <input v-model="nowyBlog" type="text">
        <button @click="dodaj_wpis">dodaj</button>
    </div>
</template>

<script>
import { dzien2_backend } from 'declarations/dzien2_backend/index';

export default {
    data() {
        return {
            wpisy: [],
            nowyBlog: ""
        }
    },
    methods: {
        async dodaj_wpis() {
            await dzien2_backend.dodaj_Wpisy(this.nowyBlog);
        },
        async pobierzWpisy() {
            this.wpisy = await dzien2_backend.odczytaj_wpisy();
        }
    }
}
</script>