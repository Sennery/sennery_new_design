<template>
    <v-row no-gutters>
        <v-col
            class="ma-0 pa-0"
            v-scroll="onScroll" 
            v-resize="onResize"
            cols="12"
        >
            <Start
                :scroll="scroll"
                :height="clientHeight"
            />
            
            <About
                :scroll="scroll"
                :height="clientHeight"
            />
            
            <Contacts
                :scroll="scroll"
                :height="scrollHeight"
            />          
        </v-col>
    </v-row>
</template>

<script>
import Start from '~/components/Start.vue'
import About from '~/components/About.vue'
import Contacts from '~/components/Contacts.vue'

export default {
    components: {
        Start,
        About,
        Contacts
    },
    data() {
        return{
            scrollHeight: null,
            clientHeight: null,
            scroll: null
        }
    },
    methods: {
        onScroll() {
            this.scroll = window.scrollY;            
        },
        onResize() {
            this.clientHeight = document.documentElement.clientHeight;
            this.scrollHeight = document.body.scrollHeight;
        }
    },
    mounted() {
        this.clientHeight = document.documentElement.clientHeight;
    },
    beforeMount() {
        let theme = window.matchMedia('(prefers-color-scheme: dark)').matches;
        this.$vuetify.theme.dark = theme;
    }
}
</script>
