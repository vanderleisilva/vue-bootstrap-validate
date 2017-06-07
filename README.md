# vue-bootstrap-validate 

> A bootstrap integrated validation component for vue.js.

The component adds a bootstrap style to the validation form elements status. The component uses **vee-validate** to perform validations.  

# Requirements

- [Vue.js](https://github.com/vuejs/vue) `^2.0.0`
- Module bundler: [webpack](https://github.com/webpack/webpack)
- [Bootstrap](getbootstrap.com) `^3.3.7`
- [Vee-validate](http://vee-validate.logaretm.com/) `^2.0.0`

# Installation

``` bash
$ npm install vue-bootstrap-validate --save
```

# Usage
``` html
<field-validation :status="errors" :custom-errors="apiErrors" label="Input label" field="data">
	<input v-validate="'required'" class="form-control" v-model="databind" name="data" data-vv-as="data-to-show" type="text" />
</field-validation> 

<script>
import fieldValidation from 'vue-bootstrap-validate'

import ptBR from 'vee-validate/dist/locale/pt_BR'
fieldValidation.locale(ptBR, 'pt_BR')

Vue.component('field-validation', fieldValidation);
</script>
```