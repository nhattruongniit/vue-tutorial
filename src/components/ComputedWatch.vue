<template>
  <div>
    <h3>Computed and Watched</h3>  
    <div>{{ fullName }}</div>
    <div>filter array with computed: {{ evenNumbers }} </div>
  </div>
</template>

<script>
export default {
  props: {
    firstNameProps: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      firstName: 'Tony',
      lastName: 'Nguyen',
      numbers: [1, 2, 3 ,4 , 5, 6]
    }
  },
  methods: {
  },
  watch: {
    firstNameProps(val) {
      console.log('firstName: ', val)
      this.fullName = `${val} ${this.lastName}`
    },
    lastName(val) {
      this.fullName = `${this.firstName} ${val} `
    }
  },
  computed: {
    fullName: {
      // getter
      get: function () {
        return this.firstName + ' ' + this.lastName
      },
      // setter
      set: function (newValue) {
        const names = newValue.split(' ')
        this.firstName = names[0]
        this.lastName = names[names.length - 1]
      }
    },
    evenNumbers() {
      return this.numbers.filter(number => number % 2 === 0)
    }
  }
};
</script>

<style>
.underline {
  text-decoration: line-through;
}
</style>
