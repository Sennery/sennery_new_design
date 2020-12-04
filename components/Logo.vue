<template>
    <div
    class="face"
    :class="{ translatePerspective: pointPassed }"
    :style="{ background: $vuetify.theme.themes[theme].background }"
    >
        <div class="navigation" :style="rotation">
            <div class="wrapper out" :class="{ stopAnimation: pointPassed }">
                <div class="wrapper in" :class="{ stopAnimation: pointPassed }">
                    <div class="side front">
                        <div class="containerm main">
                            <span>S</span>
                            <span>E</span>
                            <span>N</span>
                            <span>N</span>
                            <span>E</span>
                            <span>R</span>
                            <span>Y</span>
                        </div>
                    </div>
                    <div class="side back">
                        <div class="containerm">
                            <div class="text">CONTACTS</div>
                        </div>
                    </div>
                    <div class="side top">
                        <div class="containerm">
                            <div class="text">ABOUT</div>
                        </div>
                    </div>
                    <div class="side bottom">
                        <div class="containerm">
                            <div class="text"></div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <v-tooltip left>
            <template v-slot:activator="{ on, attrs }">
                <v-btn
                    icon
                    class=".float-right"
                    absolute
                    right
                    :top="!pointPassed"
                    @click="changeTheme"
                    v-bind="attrs"
                    v-on="on"
                >
                    <v-icon> mdi-theme-light-dark </v-icon>
                </v-btn>
                <v-icon :class="{ icon_down: true, stopAnimation: pointPassed }">
                    mdi-chevron-down
                </v-icon>
            </template>
            <span>Change color theme</span>
        </v-tooltip>
    </div>
</template>

<script>
export default {
    name: "Logo",
        props: {
        title: String,
        pointPassed: Boolean,
    },
    data() {
        return {
            rotationMap: {
                face: 0,
                about: -90,
                contact: -180,
                other: -270,
            },
        };
    },
    methods: {
        changeTheme() {
            this.$vuetify.theme.dark = !this.$vuetify.theme.dark;
        },
    },
    computed: {
        rotation() {
            if (this.rotationMap[this.title] != 0) {
            return {
                transform:
                "rotateX(" +
                this.rotationMap[this.title] +
                "deg) scale3d(0.5,0.5,0.5) translateX(var(--translate-header)",
            };
            }
            return null;
        },
        theme() {
            return this.$vuetify.theme.dark ? "dark" : "light";
        },
    },
};
</script>

<style lang="scss">
    .translatePerspective {
        height: calc(var(--container-height)*0.8);
        perspective-origin: var(--perspective-x) 50%;
    }

    .stopAnimation {
        animation-iteration-count: 0 !important;
    }

    .icon_down {
        position: absolute !important;
        bottom: 3.5%;
        transition: opacity 0.3s ease;
        opacity: 0;
        animation: jump_icon 1s ease 3s infinite;
    }

    @keyframes jump_icon {
        0% {
            transform: translateY(-1rem);
            opacity: 1;
        }

        100% {
            transform: translateY(0rem);
            opacity: 0;
        }
    }
</style>