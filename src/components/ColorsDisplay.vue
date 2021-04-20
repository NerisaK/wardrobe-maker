<template>
    <section>
        <keep-alive>
            <div v-if="showColors">
                <p v-if="colorsNotSet"><strong>
                    Začni výběrem hlavních barev pro svůj šatník!
                </strong></p>
                <h3 class="mb-4" v-if="!colorsNotSet">Tvoje barvy</h3>
                <div class="palette-three" v-if="!colorsNotSet">
                    <div
                        class="color"
                        :style="{ backgroundColor: userColors[0] }"
                    ></div>
                    <div
                        class="color"
                        :style="{ backgroundColor: userColors[1] }"
                    ></div>
                    <div
                        class="color"
                        :style="{ backgroundColor: userColors[2] }"
                    ></div>
                </div>
                <div class="palette-two" v-if="!colorsNotSet">
                    <div
                        class="color"
                        :style="{ backgroundColor: userColors[3] }"
                    ></div>
                    <div
                        class="color"
                        :style="{ backgroundColor: userColors[4] }"
                    ></div>
                </div>
                <button
                    class="btn btn-primary my-3 ml-2"
                    @click="showColors = !showColors, showSettings = !showSettings"
                    >
                    Vybrat nové barvy
                </button>
            </div>
        </keep-alive>
        <form v-if="showSettings">
            <h4 class="mb-4">Nastavení barev</h4>
            <p>Hlavní barvy (akcenty):</p>
            <div>
                <input
                    type="color"
                    name="color-picker0"
                    id="color-picker0"
                    v-model.lazy="newColors[0]"
                />
                <input
                    type="color"
                    name="color-picker1"
                    id="color-picker1"
                    v-model.lazy="newColors[1]"
                />
                <input
                    type="color"
                    name="color-picker2"
                    id="color-picker2"
                    v-model.lazy="newColors[2]"
                />
            </div>
            <p>Neutrální barvy (doplňkové):</p>
            <div>
                <input
                    type="color"
                    name="color-picker3"
                    id="color-picker3"
                    v-model.lazy="newColors[3]"
                />
                 <input
                    type="color"
                    name="color-picker4"
                    id="color-picker4"
                    v-model.lazy="newColors[4]"
                />
            </div>
            <p class="info">Pokud si svůj výběr později rozmyslíš, můžeš se sem vrátit, ale pamatuj na to, že barva se nezmění jen ve tvé paletě, ale i u všech věcí, které máš tou barvou označené!</p> 
            <button
                class="btn btn-success"
                @click.prevent="changeColors(), showColors = !showColors, showSettings = !showSettings"
                >
                Uložit změny
            </button>
            <button
                class="btn btn-danger ml-2"
                @click.prevent="keepColors(), showColors = !showColors, showSettings = !showSettings"
                >
                Zrušit
            </button>
        </form>
    </section>
</template>

<script>
export default {
    props: {
        userColors: Array,
        colorsNotSet: Boolean,
    },
    data(){
        return{            
            showColors: true,
            showSettings: false,
            newColors: [
                "#C57C7C",
                "#768A3D",
                "#7A1A1A",
                "#4b3520",
                "#ffffff"
            ],
        }
    },
    methods: {
        changeColors(){
            let colors = this.newColors.slice();
            this.$emit('colorsChanged', colors);
            if (this.colorsNotSet === true) {
                this.$emit('choseColors')
            }
        },
        keepColors(){
            this.newColors = this.userColors.slice();
        },
    }    
}
</script>

<style scoped>
    .palette-three, .palette-two, form div {
        display: flex;
    }

    .palette-three .color{
        width: 60px;
        height: 60px;
        margin: 5px;
    }

    .palette-two .color{
        width: 95px;
        height: 60px;
        margin: 5px;
    }

    .color{border: 2px solid #3C403D}

    input{
        width: 3rem;
        height: 3rem;
        margin-right: 10px;
        margin-bottom: 30px
    }  

    .info{width: 50%}  
</style>