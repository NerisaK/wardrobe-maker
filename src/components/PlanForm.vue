<template>
    <form>
        <h4 class="mb-4">Nový plán</h4>        
        <p class="mt-3">Zadej počet:</p>
        <div v-for="(value, name) in planFormData" :key="name">
            <p class="clothes">
                <span class="value">{{ value.value }}</span>
                <span class="quantity">{{ value.quantity}}</span> 
                <span class="buttons">                
                    <button class="btn btn-success changeBtn"
                        @click.prevent="value.quantity++">+</button>
                    <button class="btn btn-danger changeBtn"
                        @click.prevent="value.quantity--">-</button>
                </span>
            </p>
        </div>
        <button class="btn btn-success ml-3"
            @click.prevent="savePlan(), $emit('hide')">
                uložit
        </button>
        <button class="btn btn-danger ml-3"
            @click.prevent="clearForm(), $emit('hide')">
                zrušit
        </button>
    </form>
</template>

<script>
export default {
    data(){
        return{
            planFormData: {
                coats: {value: "kabáty", quantity: 0},
                jackets: {value: "bundy", quantity: 0},
                blazers: {value: "saka", quantity: 0},
                sweaters: {value: "svetry", quantity: 0},
                tops: {value: "trička", quantity: 0},
                skirts: {value: "sukně", quantity: 0},
                pants: {value: "kalhoty", quantity: 0},
                leggins: {value: "legíny", quantity: 0},
                shorts: {value: "kraťasy", quantity: 0},
                dresses: {value: "šaty", quantity: 0},
                formal: {value: "společenské šaty", quantity: 0},
                shoes: {value: "boty", quantity: 0},
                bags: {value: "kabelky", quantity: 0},
                accessories: {value: "doplňky, šperky", quantity: 0},
                topsHome: {value: "domácí trička", quantity: 0},
                bottomsHome: {value: "tepláky", quantity: 0},
                sleepHome: {value: "pyžama/košilky", quantity: 0},
                hoodies: {value: "mikiny", quantity: 0},
            },
        }
    },
    methods: {
        clearForm(){
            for (let key in this.planFormData){
                this.planFormData[key].quantity = 0;
            }
        },
        savePlan(){
            const newList = {};
            for (const key in this.planFormData) {
               if (this.planFormData[key].quantity !== 0){
                   newList[key] = this.planFormData[key];
               } 
            }
            this.$emit('planChanged', newList);
        },
    }
}
</script>

<style scoped>
    p, label{font-size: 1.1em}
    label {margin-right: 10px}
    input {width: 150px}
    .changeBtn {font-size: 1.5em; padding: 0; width: 25px; height: 25px; margin-left: 5px}
    form {width: 50%; margin: 30px auto; padding: 30px 40px; border: 2px solid white;}
    .clothes {margin-left: 15px; display: flex; align-items: center;}
    .quantity {border: 2px solid white; padding: 5px 15px}
    .value {flex-basis: 300px; border-bottom: 2px solid white; align-self:flex-end;}
</style>