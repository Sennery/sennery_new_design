<template>
    <div class="text_wrapper">
        <span
            v-for="(it, i) in symbolsArray"
            :key="i"
            :class="{ space: it == ' '} "
            :style="{...transitionStyle,...style, 
                     transition: 'transform ' + animationTime + 's ' + timingFunction + ' ' + (step*i + delay) + 's'
                        + ', opacity ' + animationTime/2 + 's ease-out ' + (step*i + delay) + 's'}"
            >{{ it }}</span>
    </div>
</template>

<script>
export default {
    props: {
        text: String,
        time: Number,
        delay: {
            type: Number,
            default: 0.05
        },
        from: String,
        opacity: Boolean,
        letterSpacing: {
            type: Number,
            default: 0
        },
        show: Boolean,
    },
    data() {
        return {
            step: 0.05,
            animationTime: 0.3,
            translateSize: 1,
            timingFunction: 'cubic-bezier(0.18, 0.89, 0.32, 1.28)',
            directionMap: {
                'l' : (i) => { return 'translate(-' + i +  'em)'},
                'r' : (i) => { return 'translate(' + i +  'em)'},
                't' : (i) => { return 'translate(0,-' + i +  'em)'},
                'b' : (i) => { return 'translate(0,' + i +  'em)'},
            }
        }
    },
    computed: {
        symbolsArray() {
            let result = [];
            this.text.split(' ').forEach( e => {
                result = result.concat(e.split(''));
                result.push(' ');
            });
            return result;
        },
        transformation() {
            return this.directionMap[this.from](this.translateSize);
        },
        visibility() {
            return this.opacity ? 0 : 1;
        },
        activate() {
            return this.show;
        },
        transitionStyle() {
            let transition = {
                
            }

            if (this.activate) {
                return {
                    transform: 'translate(0)',
                    opacity: 1,
                }
            } else {
                return {
                    transform: this.transformation,
                    opacity: this.visibility,
                }
            }
        },
        style() {
            return {
                marginRight: this.letterSpacing + 'rem'
            }
        }        
    },
    mounted() {
        while((this.time-(this.step*this.symbolsArray.length)) < this.animationTime) {
                this.step-=0.0001;
        }
    }
}
</script>

<style lang="scss">
    .text_wrapper {
        margin: 0;
        padding: 0;

        & span {
            display: block;
            float: left;
            position: relative;
        }

        & .space {
            width: 0.25em !important;
            height: 1em !important;
        }
    }
</style>