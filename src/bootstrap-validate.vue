<template>
  <div class="form-group has-feedback" :class="[problems ? 'has-error' : '', cssClass]">
      <label v-show="label" class="control-label" :for="field">{{label}}</label>
      <slot />      
      <span v-show="problems && label" class="glyphicon glyphicon-remove form-control-feedback" aria-hidden="true"></span>
      <span v-show="problems" class="help-block">
        <p v-for="problem in problems">
          <i v-show="problems.length > 1" class="fa fa-exclamation" aria-hidden="true"></i>
          {{ problem }}
        </p>
      </span>
    </div>
</template>

<script>
import Vue from 'vue'
import VeeValidate,  { Validator } from 'vee-validate'

Vue.use(VeeValidate, {
  fieldsBagName: 'veeFields'
});

export default {
  name: "field-validation",
  computed: {
    problems() { 
      var result = [];
      if (this.status.has(this.field)) { result.push(this.status.first(this.field)) }

      if (this.customErrors && this.customErrors[this.field]) { 
        this.customErrors[this.field].forEach(item => { result.push(item); });
      }

      return result.length > 0 ? result : false;
    },
  },
  props: {
    status: Object,
    field: String,
    label: String,
    cssClass: String,
    customErrors: Object
  },
  locale(lang, label){   
    Validator.addLocale(lang);
    Validator.setLocale(label);
  }
} 
</script>

<style scoped>
  .help-block p{ margin:0; }
</style>