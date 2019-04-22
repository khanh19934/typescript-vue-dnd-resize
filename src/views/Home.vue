<template>
    <div class="home">
        <div id="drag-section">
            <VueDragResize :parentW="500" :parentH="500" :parentLimitation="false"  :isActive="false" :w="200" :h="200" v-on:resizing="resize"
                           v-on:dragging="resize">
                <h3>Hello World!</h3>
                <p>{{ top }} х {{ left }} </p>
                <p>{{ width }} х {{ height }}</p>
            </VueDragResize>
        </div>
    </div>
</template>

<script lang="ts">
import {Component, Vue} from 'vue-property-decorator';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src

// @ts-ignore
import VueDragResize from 'vue-drag-resize';

@Component({
    components: {
        HelloWorld,
        VueDragResize
    },
})
export default class Home extends Vue {
    public width: number = 0;
    public height: number = 0;
    public top: number = 0;
    public left: number = 0;

    public resize(newRect: any) {
        this.width = newRect.width;
        this.height = newRect.height;
        this.top = newRect.top;
        this.left = newRect.left;
    }
}
</script>

<style>
    #drag-section {
        width: 500px;
        height: 500px;
        margin: auto;
        display: flex;
        border: 1px dashed black;
        position: relative;
        overflow: hidden;
    }
</style>
