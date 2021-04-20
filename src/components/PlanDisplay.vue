<template>
    <section>
        <h3>Tvůj plán</h3>
        <div v-if="formVisible === false">
            <p class="mt-4 ml-2">Zatím ještě nemáš vytvořený žádný plán šatníku.</p>
            <button class="btn btn-primary ml-2" @click.prevent="showForm()" >Vytvořit nový</button>
        </div>
        <PlanForm v-if="formVisible === true" @hide="showForm"/>
    </section>
</template>

<script>
import PlanForm from './PlanForm'

export default {
    components: {
        PlanForm
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
    }
}
</script>