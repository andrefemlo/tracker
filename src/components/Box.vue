<template>
 <div class="box has-text-weight-bold">
    <slot></slot>
 </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'BoxWrapper'
})
</script>

<style scoped>
.box {
    background-color: #f0f0c4;
}
</style>