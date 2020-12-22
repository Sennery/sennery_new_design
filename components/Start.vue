<template>
    <v-container 
        class="start pa-0 ma-0" 
        :class="{ 'elevation-3': pointPassed }"
        :style="{background: $vuetify.theme.themes[theme].background}"
        fluid
    >
        <Logo :title="menuRotate" :pointPassed="pointPassed"/>
    </v-container>
</template>

<script>

export default {
    props: { 
        scroll: Number,
        height: Number
    },
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
        },
        theme(){
            return (this.$vuetify.theme.dark) ? 'dark' : 'light'
        }
    }
}
</script>

<style lang="scss">
    .shadowHeader {
        box-shadow: rgba(5, 5, 5, 0.06) 0px 2px 31px;
    }
</style>