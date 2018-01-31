<template>
  <div class="form-group">
    <label v-if="typeForm === 'form'">{{ label }}</label>
    <label v-else class="col-sm-4 control-label">{{ label }}</label>

    <div v-if="typeForm === 'horizontal'" class="col-sm-6">
      <select :class="{
        'form-control': true, 'input-sm': true, changed: changedValue }" :value="ID"
        @change.prevent="handleChangeOption">
        <option v-for="option in options" :value="option.id">
          {{ option.name }}
        </option>
      </select>
    </div>

    <select v-else class="form-control input-sm" :value="selectedID"
      @change.prevent="handleChangeOption">
      <option v-for="option in options" :value="option.id">
        {{ option.name }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: 'Select',

  data () {
    return {
      value: false,
    }
  },

  props: {
    typeForm: {
      type: String,
      default: 'form'
    },
    options: Array,
    label: {
      type: String,
      default: '',
    },
    selectedID: {
      type: Number,
      default: 0,
    },
  },

  components: {
  },

  computed: {
    ID () {
      return this.value || this.selectedID;
    },

    changedValue () {
      if (!this.value) return false;
      return this.value !== this.selectedID;
    },
  },

  mounted() {
  },

  methods: {
    handleChangeOption (event) {
      this.value = parseInt(event.target.value, 10);
      this.$emit('changeOption', parseInt(event.target.value, 10));
    },
  },
}
</script>

<style>
.changed {
  background-color: #ffb74d;
}
</style>
