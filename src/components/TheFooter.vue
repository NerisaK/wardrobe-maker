<template>
    <footer>
        <div class="navbar navbar-expand-lg navbar-light bg-grey">
            <p class="my-3 text-light">Vytvořila Nerisa Kalošin © 2021</p>
            <div class="devTools">
                <p class="text-light text-center">Pro vývoj</p>
                <button class="btn btn-light btn-sm" @click.prevent="$emit('deleteData')">
                    Vymazat data
                </button>
            </div>
        </div>
    </footer>
</template>

<style scoped>
    .devTools {margin-left: auto}
</style>
