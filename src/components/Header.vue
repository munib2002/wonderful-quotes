<template>
    <div class="header">
        <h2 class="heading2">Quotes Added</h2>
        <div class="progress-bar">
            <div v-if="progress>0" class="progress" :style="{width: progress *10 + '%'}">
                <p class="progress-count">{{progress}} / 10</p>
            </div>
            <div v-else style="text-align: center">No quotes</div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['progress'],
    methods: {
        updateProgress() {
            this.progress++;
            this.progress = this.progress > 10 ? 10: this.progress;
            this.width = this.progress * 10;
        }
    }
}
</script>

<style scoped>
    .header {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-bottom: 2rem;
    }
    .heading2 {
        font-size: 3rem;
        align-self: flex-start;
    }
    .progress-bar {
        border: .1rem solid #ddd;
        background-color: #f4f4f4;
        align-self: stretch;
        border-radius: .5rem;
    }
    .progress {
        background-color: #2980b9;
        display: flex;
        justify-content: center;
        color: #fff;
        font-size: 1.2rem;
        transition: all .2s;
    }
</style>