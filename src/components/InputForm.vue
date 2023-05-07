<template>
    <div>
        <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />
        <form @submit.prevent="submitData">
            <input v-model="goalText" placeholder="Please input Text" />
            <select v-model="goalCategory">
                <option value="year">{{ yearText }} </option>
                <option value="halfYear">{{ halfYearText }}</option>
                <option value="month">{{ monthText }}</option>
                <option value="week">{{ weekText }}</option>
                <option value="any">{{ anyText }}</option>
            </select>
            <button type="submit">Register</button>
        </form>
    </div>
</template>

<script>
import { defineComponent , ref, computed } from 'vue'
var YearText;
var HalfYearTetx;
var MonthTxet;
var WeekTxet;
var AnyTxet = 'Anything Task'
GetDate()

function GetDate(){
    const date = new Date()
    const Year = date.getFullYear().toString()
    YearText = 'This Years Goal' + Year
    const HalfYear = halftYear()
    function halftYear() {
        if (date.getMonth() < 4) {
            return 'This Half Year' + "September(9) ~ March(3)"
        } else {
            return 'This Half Year' +  "Aprile(4) ~ August(8)"
        }
    }
    const Month = date.getMonth() 
    const Week = "Today" + date.getDay().toString()
}

export default defineComponent({
    setup() {
        const goalText = ref('')
        const goalCategory = ref('year')

    },
    submitData() {
        this.$emit('add-goal', {
            text: this.goalText,
            category: this.goalCategory,
        })
    }  
})


</script>
