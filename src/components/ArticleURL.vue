<script setup lang="ts">
import { CrossTalkComments } from 'crosstalk-comments-livechat-vue3';
import { computed } from 'vue';

const props = defineProps({
    isLight: {
        type: Boolean,
        default: true
    }
});

const webPropertyName = "crosstalkDemo"; //our demo web property, you can make yours for free at https://crosstalk.cc/
const theme = computed(() => {
    if (props.isLight) return "light";
    else return "dark";
})
function getURL() {
    return "https://test.com/tech/article/hello-123"; //in production, you might use `window.location.href`
}
</script>

<template>
    <v-container fluid>
        <v-row>
            <v-col>
                <h1 class="ma-2">Imagine this is an article with some current URL <code>{{ getURL() }}</code></h1>
                <h3 class="ma-2">sample subtitle</h3>
            </v-col>
        </v-row>

        <v-row>
            <v-col>
                <p>Lorem ipsum dolor sit amet consectetur adipiscing elit. Quisque faucibus ex sapien vitae pellentesque
                    sem placerat. In id cursus mi pretium tellus duis convallis. Tempus leo eu aenean sed diam urna
                    tempor. Pulvinar vivamus fringilla lacus nec metus bibendum egestas. Iaculis massa nisl malesuada
                    lacinia integer nunc posuere. Ut hendrerit semper vel class aptent taciti sociosqu. Ad litora
                    torquent per conubia nostra inceptos himenaeos.
                    <br />
                    Lorem ipsum dolor sit amet consectetur adipiscing elit. Quisque faucibus ex sapien vitae
                    pellentesque sem placerat. In id cursus mi pretium tellus duis convallis. Tempus leo eu aenean sed
                    diam urna tempor. Pulvinar vivamus fringilla lacus nec metus bibendum egestas. Iaculis massa nisl
                    malesuada lacinia integer nunc posuere. Ut hendrerit semper vel class aptent taciti sociosqu. Ad
                    litora torquent per conubia nostra inceptos himenaeos.
                </p>
            </v-col>
        </v-row>

        <v-row>
            <v-col>
                <CrossTalkComments class="ma-1" :url="getURL()" :wp="webPropertyName" :theme="theme" />
            </v-col>
        </v-row>
    </v-container>
</template>