<template>
  <form @submit="trySubmit" class="d-flex flex-column">
    …
    <h4>Ajouter un produit :</h4>
    <hr class="w-100" />
    <div class="form-group">
      <label>Image</label>
      <input type="text" class="form-control" />
    </div>
    <div class="form-group">
      <label>Titre</label>
      <input type="text" class="form-control" />
    </div>
    <div class="form-group">
      <label>Description</label>
      <textarea class="form-control"></textarea>
    </div>
    <div class="form-group">
      <label>Prix</label>
      <input type="number" class="form-control" />
    </div>
    <button class="btn btn-primary">Ajouter</button>
    <ul v-if="errors.length">
      <li class="text-danger" v-for="error in errors" :key="error">{{ error }}</li>
    </ul>
  </form>
</template>

<script>
export default {
  data() {
    return {
      form: {
        img: '',
        title: '',
        description: '',
        price: ''
      },
      errors: []
    }
  },
  methods: {
  trySubmit(e) {
    e.preventDefault();
    if (this.formIsValid()) {
      console.log(this.form);
    }
  },
  formIsValid() {
    this.errors = [];
    if (!this.form.img) {
      this.errors.push('img required');
    }
    if (!this.form.title) {
      this.errors.push('title required');
    }
    if (!this.form.description) {
      this.errors.push('description required');
    }
    if (!this.form.price) {
      this.errors.push('price required');
    }
    return this.errors.length ? false : true;
  }
},
}

</script>

<style>
</style>