<template>
  <div v-if="fieldType !== 'checkbox' && fieldType !== 'button'" class="form-group">
    <label :class="{
      'col-sm-4': formType === 'horizontal',
      'control-label': formType === 'horizontal'
      }">
    {{ label }}</label>

    <div v-if="formType === 'horizontal'" class="col-sm-6">
      <input
        v-if="fieldType === 'number'"
        :type="fieldType"
        :class="{ 'form-control': true, 'input-sm': true,
        changed: changedValue }"
        :value="componentValue"
        @change="changeValue"
        :min="minNumber"
        :step="stepNumber"
      >

      <input
        v-else-if="fieldType !== 'textarea'"
        :type="fieldType"
        :class="{ 'form-control': true, 'input-sm': true,
        changed: changedValue }"
        :value="componentValue"
        @change="changeValue"
      >
      <textarea
        v-else-if="fieldType === 'textarea'"
        :class="{ 'form-control': true, 'input-sm': true,
        changed: changedValue }"
        @change="changeValue"
        >
        {{ componentValue }}
      </textarea>

    </div>

    <input v-if="formType === 'form'" :type="fieldType" class="form-control input-sm" :value="fieldValue">
  </div>

  <div v-else class="form-group">
    <div class="col-sm-offset-4 col-sm-6">
      <label v-if="fieldType === 'checkbox'">
        <input
          :type="fieldType"
          :checked="fieldValue"
          @change="changeValue"
        >&nbsp; {{ label }}
      </label>

      <button
        v-if="fieldType === 'button'"
        class="btn btn-primary btn-sm"
        @click.prevent="clickButton"
      >{{ fieldValue }}</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Field',

  data () {
    return {
      value: false,
    }
  },

  props: {
    fieldType: {
      type: String,
      default: 'text'
    },

    fieldValue: {
      type: [String, Number, Boolean],
      default: ''
    },

    fixedNumber: {
      type: Number,
      default: 0
    },

    formType: {
      type: String,
      default: 'form'
    },

    label: {
      type: String,
      default: ''
    },

    minNumber: {
      type: Number,
    },

    stepNumber: {
      type: Number,
      daefault: 1
    }

  },

  components: {
  },

  computed: {
    changedValue () {
      if (!this.value) return false;
      return this.fieldValue != this.value;
    },

    componentValue () {
      if (this.value) {
        return this.fixedNumber ? parseFloat(this.value).toFixed(this.fixedNumber) : this.value;
      }
      return this.fixedNumber ? parseFloat(this.fieldValue).toFixed(this.fixedNumber) : this.fieldValue;
    },
  },

  mounted() {
  },

  methods: {
    changeValue (event) {
      let changedValue = event.target.value;
      if (this.fixedNumber) {
        changedValue = parseFloat(event.target.value);
      }
      this.value = changedValue;
      this.$emit('changeValue', changedValue);
    },

    clickButton () {
      this.$emit('clickButton');
    },
  },
}
</script>

<style>
.changed {
  background-color: #ffb74d;
}
</style>
