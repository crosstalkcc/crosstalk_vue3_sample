<script setup lang="ts">
import { CrossTalkVideoPlayer } from 'crosstalk-comments-livechat-vue3';
import { computed } from 'vue';

const props = defineProps({
    isLight: {
        type: Boolean,
        default: true
    }
});

const theme = computed(() => {
    if (props.isLight) return "light";
    else return "dark";
})
const webPropertyName = "crosstalkDemo"; //our demo web property, you can make yours for free at https://crosstalk.cc/
</script>

<template>
    <v-container fluid>
        <v-row>
            <v-col>
                <h3>Live TV with Live Chat Sample</h3>
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                <cross-talk-video-player pageID="livetv" :wp="webPropertyName" :theme="theme" ytvid="miVz9nsMYEw" class="mx-auto" style="width: 100%" />
            </v-col>
        </v-row>
    </v-container>
</template>