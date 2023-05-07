<template>
    <div>
        <div class="form-continer">
        <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />
        <form @submit.prevent="submitData">
            <input v-model="goalText" placeholder="Please input Text" />
            <select v-model="goalCategory">
                <option value="goal">"My Goal"</option>
                <option value="year">{{ yearText }} </option>
                <option value="halfYear">{{ halfYearText }}</option>
                <option value="month">{{ monthText }}</option>
                <option value="week">{{ weekText }}</option>
                <option value="any">{{ todayText }}</option>
                <option value="any">{{ anyText }}</option>                
            </select>
            <button type="submit">Register</button>
        </form>
    </div>
    <div class = "right-container">
        <h1>"My Goal" </h1>
        <h1> {{ halfYearText }} </h1>
        <h1> {{ todayText }} </h1>
    </div>
    <div class = "left-container">
            <h1> {{ yearText }} </h1>
            <h1> {{ monthText }} </h1>
            <h1> {{ anyText }} </h1> 
    </div>    
    </div>
</template>

<script>
import { defineComponent , ref} from 'vue'


export default defineComponent({
    setup() {
        const goalText = ref('')
        const goalCategory = ref('year')
     const today = new Date()
    const year = today.getFullYear().toString()
    const yearText = `This Year's Goal (${year})`

    const halfYearText = (() => {
      const month = today.getMonth()
      if (month < 4) {
        return `This Half Year's Goal (September (9) ~ March (3))`
      } else {
        return `This Half Year's Goal (April (4) ~ August (8))`
      }
    })()

    const month = today.toLocaleString('default', { month: 'long' })
    const monthText = `This Month's Goal (${month})`

    const week = today.toLocaleString('default', { weekday: 'long' })
    const weekText = `This Week's Goal (${week})`

    const todayText = `Today's Goal (${today.toLocaleDateString()})`

    const anyText = 'Anything Task'

    function submitData() {
      // Emit event with goal data
    }

    return {
      goalText,
      goalCategory,
      yearText,
      halfYearText,
      monthText,
      weekText,
      anyText,
      todayText,
      submitData,
    }
  },  
})


</script>
