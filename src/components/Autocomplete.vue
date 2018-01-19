<template>
    <div style="position:relative" v-bind:class="{'open':openSuggestion}">
        <input class="form-control" type="text" :value="value" @input="updateValue($event.target.value)"
          @keydown.enter = 'enter'
          @keydown.down = 'down'
          @keydown.up = 'up'
          @keydown.esc = 'close'
        >
        <ul class="dropdown-menu" style="width:100%">
            <li v-for="(suggestion, index) in matches" :key="index"
                v-bind:class="{'active': isActive(index)}"
                @click="suggestionClick(index)"
            >
              <a href="#">{{ suggestion.name }} <small>{{ suggestion.description }}</small>
              </a>
            </li>
        </ul>
    </div>
</template>

<script>
import compareStrings from 'string-compare'

export default {

  props: {

    value: {
      type: String,
      required: true
    },

    suggestions: {
      type: Array,
      required: true
    },

    limit: Number

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
      return this.suggestions.sort((a, b) => compareStrings(a.name, this.value) < compareStrings(b.name, this.value) ? 1 : -1).slice(0, this.limit || 5)
    },

    openSuggestion () {
      return this.selection !== '' &&
             this.matches.length !== 0 &&
             this.open === true
    }
  },

  methods: {

    updateValue (value) {
      if (this.open === false) {
        this.open = true
        this.current = 0
      }
      this.$emit('input', value)
    },

    // When enter pressed on the input
    enter () {
      this.$emit('input', this.matches[this.current].name)
      this.open = false
    },

    close () {
      this.open = false
    },

    // When up pressed while suggestions are open
    up () {
      if (this.current > 0) {
        this.current--
      }
    },

    // When up pressed while suggestions are open
    down () {
      if (this.current < this.matches.length - 1) {
        this.current++
      }
    },

    // For highlighting element
    isActive (index) {
      return index === this.current
    },

    // When one of the suggestion is clicked
    suggestionClick (index) {
      this.$emit('input', this.matches[index].name)
      this.open = false
    }

  }

}
</script>
