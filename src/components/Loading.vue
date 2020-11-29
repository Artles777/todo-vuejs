<template>
    <div class="loading">
        <p class="loading-text">
            Загрузка...
        </p>
        <md-progress-spinner :md-diameter="100" :md-stroke="10" md-mode="indeterminate" />
    </div>
</template>

<script>
export default {
    name: 'ProgressSpinnerSizes'
}
</script>

<style scoped>
  .md-progress-spinner {
    margin: 24px;
  }
</style>
