<template>
    <section>
        <h3>Tvůj plán</h3>
        <div v-if="formVisible === false">
            <p class="mt-4 ml-2" v-if="!hasPlan">
                Zatím ještě nemáš vytvořený žádný plán šatníku.
            </p>
            <button
                class="btn btn-primary ml-2"
                @click.prevent="showForm()"
                v-if="!hasPlan">
                    Vytvořit nový
            </button>
        </div>
        <PlanForm
            v-if="formVisible === true" @hide="showForm"
            @planChanged="$emit('planChanged', $event)"
        />
        <div class="mt-4" v-for="(value, name) in userPlan" :key="name">
            <p class="clothes">
                <span class="value">{{ value.value }}</span>
                <span class="quantity">{{ value.quantity}}</span>
            </p>
        </div>
    </section>
</template>

<script>
import PlanForm from './PlanForm'

export default {
    components: {
        PlanForm
    },
    props: {
        userPlan: Object,
    },
    data(){
        return{
            formVisible: false,
        }
    },
    methods: {
        showForm(){
            this.formVisible ? this.formVisible = false : this.formVisible = true;
        },
    },
    computed: {
        hasPlan(){
            return true
        },
    },
}
</script>

<style scoped>
    p{font-size: 1.1em} 
    .clothes {margin-left: 15px; display: flex; align-items: center;}
    .quantity {border: 2px solid white; padding: 5px 15px}
    .value {flex-basis: 300px; border-bottom: 2px solid white; align-self:flex-end;}
</style>