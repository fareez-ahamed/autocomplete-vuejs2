<template>
    <div style="position:relative" v-bind:class="{'open':openSuggestion}">
        <input class="form-control" type="text" :value="value" @input="updateValue($event.target.value)">
        <ul class="dropdown-menu" style="width:100%">
            <li v-for="suggestion in matches">
              <a href="#">{{ suggestion }}</a>
            </li>
        </ul>
    </div>
</template>

<script>
export default {

  props: {

    value: {
      type: String,
      required: true
    },

    suggestions: {
      type: Array,
      required: true
    }

  },

  data () {
    return {
      open: false,
      current: 0
    }
  },

  computed: {
    // Filtering the suggestion based on the input
    matches () {
      return this.suggestions.filter((str) => {
        return str.indexOf(this.selection) >= 0
      })
    },

    openSuggestion () {

    }
  },

  methods: {
    updateValue (value) {
      this.$emit('input', value)
    }
  }

}
</script>
