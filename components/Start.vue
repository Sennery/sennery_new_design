<template>
    <v-container 
        class="start pa-0 ma-0" 
        :class="{ 'elevation-2': pointPassed }"
        :style="{background: $vuetify.theme.themes[theme].background}"
        fluid
    >
        <Logo :title="menuRotate" :pointPassed="pointPassed"/>
    </v-container>
</template>

<script>
import ThemeMixin from "~/assets/res/ThemeMixin.js"

export default {
    props: { 
        scroll: Number,
        height: Number
    },
    mixins: [
        ThemeMixin
    ],
    computed: {
        pointPassed() {
            return (this.scroll > this.height*0.5);
        },
        menuRotate() {
            let title;
            if (this.scroll > this.height*2.5) {
                title = 'other';
            } else if (this.scroll > this.height*1.5) {
                title = 'contact';
            } else if (this.scroll > this.height*0.5) {
                title = 'about';
            } else {
                title = 'face';
            }
            return title;
        }
    }
}
</script>

<style lang="scss">
    .shadowHeader {
        box-shadow: rgba(5, 5, 5, 0.06) 0px 2px 31px;
    }
</style>