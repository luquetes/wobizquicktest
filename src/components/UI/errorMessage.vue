<template>
    <div class="alert alert-danger"><slot /></div>
</template>

<style scoped>
    .alert.alert-danger {
        background: #e85837;
        color: white;
        margin: 1em 0;
        font-family: Roboto, sans-serif;
        font-size: 13px;
        font-weight: 500;
    }
</style>